# D4-03 IBIF Reference Note

This note supports `D4-03 AWARE and biodiversity with regionalised methods.ipynb`. It explains what the **Intactness-based Biodiversity Impact Factors (IBIF)** dataset is, how the factors are built from the GLOBIO model, what the units mean, and how to interpret the country-level biodiversity factors used in regionalized LCIA.

## What IBIF Measures

IBIF provides **country-level biodiversity impact factors** for terrestrial pressures that reduce local biodiversity intactness. The underlying biodiversity metric is **mean species abundance (MSA)**, a dimensionless indicator between **0** and **1**:

- `MSA = 1` means the original local species assemblage is fully intact.
- `MSA = 0` means the original local assemblage has effectively disappeared.

IBIF converts modeled losses in MSA into impact factors that can be multiplied by inventory flows. The dataset covers **234 countries** and five pressure families:

- `CO2 emissions`
- `NH3 emissions`
- `NOx emissions`
- `land use`
- `roads`

The factors are provided for three biological scopes:

- `vascular plants`
- `warm-blooded vertebrates (birds and mammals)`
- `overall`

The `overall` factors are calculated as the arithmetic mean of the plant and vertebrate factors. When one species group is assumed not to be affected by a pressure, its value is treated as zero before averaging.

## From GLOBIO to IBIF

IBIF starts from **GLOBIO 4**, a global terrestrial biodiversity model that estimates local MSA losses from a set of direct drivers. In the IBIF workflow, those direct-driver losses are then attributed back to the pressures that appear in inventories.

![IBIF workflow from GLOBIO direct-driver losses to pressure-specific biodiversity impact factors](assets/d4-03/ibif/figure_1_workflow.png)

*Extracted from the source PDF: IBIF workflow linking GLOBIO direct-driver losses to the final biodiversity impact factors.*

The logic is:

1. GLOBIO estimates local biodiversity intactness loss for plants and/or warm-blooded vertebrates.
2. Those losses are calculated for direct drivers such as climate change, nitrogen deposition, habitat loss, habitat fragmentation, and habitat disturbance.
3. The losses are then translated into inventory-facing pressures: CO2, NH3, NOx, land use, and roads.
4. Country-level impact factors are calculated for each pressure.

For IBIF, the authors excluded **direct exploitation (hunting)** from the original GLOBIO pressure set because it is difficult to attribute hunting impacts consistently to economic activities in supply-chain accounting.

## Core Equations

### 1. Combined local biodiversity intactness

The first key equation combines direct-driver-specific MSA values into one overall local MSA:

```text
MSA_g,i = product_x MSA_x,g,i
```

`MSA_g,i` is the local intactness of species group `g` in grid cell `i`. `MSA_x,g,i` is the intactness associated with direct driver `x` in that grid cell. In plain language, GLOBIO treats different direct drivers as multiplicative pressures on local biodiversity intactness after excluding direct drivers considered subordinate under specific land-use conditions.

### 2. Allocation of total local loss to direct drivers

After the total loss is known, the local biodiversity loss is distributed across the direct drivers:

```text
MSA-loss_x,g,i = ((1 - MSA_x,g,i) / sum_x(1 - MSA_x,g,i)) * (1 - MSA_g,i)
```

This matters because IBIF is not built directly from raw pressures. It is built from **attributed losses in MSA**. A direct driver gets a larger share of the local total loss when its own driver-specific intactness reduction is larger relative to the others affecting the same grid cell.

### 3. Land-use biodiversity impact factors

For land use, the impact factor is the attributed cumulative biodiversity loss for a land-use type in a country divided by the total area of that land-use type in that country:

```text
BIF_LU,l,g,j = sum_i(MSA-loss_LU,l,g,i,j * A_i,j) / sum_i(A_LU,l,i,j)
```

`l` is land-use type, `g` is species group, and `j` is country. This gives a country-specific biodiversity loss intensity per unit area of land used.

### 4. Road biodiversity impact factors

For roads, the impact factor is the attributed cumulative biodiversity loss due to roads divided by the total road length in the country:

```text
BIF_R,j = sum_i(MSA-loss_R,i,j * A_i,j) / RL_j
```

Here the denominator is road length instead of land area, because roads are represented as a linear infrastructure pressure.

## How the Main Variables Are Defined

IBIF uses GLOBIO at **10 arc-seconds** resolution, roughly **300 m at the equator**. The model represents plants and warm-blooded vertebrates differently because the evidence base and direct drivers differ between those groups.

For **plants**, GLOBIO uses:

- climate change
- atmospheric nitrogen deposition
- habitat loss

For **warm-blooded vertebrates**, GLOBIO uses:

- climate change
- habitat loss
- habitat fragmentation
- habitat disturbance

The inputs used to build the published dataset are representative of **2020**:

- global mean temperature increase for climate change
- atmospheric nitrogen deposition grids
- land cover and land-use allocation
- mining polygons
- the GRIP global roads database

This means the published factors are designed for **current footprinting**, not for historical or future scenarios.

## What the Pressure-Specific Factors Mean

The most important thing to understand in IBIF is that the units differ across pressures because the inventory quantities differ across pressures.

### Emissions

For `CO2`, `NH3`, and `NOx`, the factors represent:

- **time- and area-integrated MSA loss per kilogram emitted**

The units are:

- `MSA-loss · km² · yr · kg⁻¹`

For `CO2`, the factor is tied to climate change through the **integrated absolute global temperature change potential** over a **100-year time horizon**. Because climate change is treated as a global mechanism, the CO2 factor is effectively global rather than country-specific.

For `NH3` and `NOx`, the attribution is more spatial. Nitrogen deposition losses are linked back to emitting countries through **TM5-FASST source-receptor matrices**, which describe how emissions from one region contribute to deposition in receiving regions. As a result, nitrogen BIFs vary by country.

### Land use

For land use, the factors represent:

- **area-integrated MSA loss per unit area of land use**

The units are:

- `MSA-loss · km² · km⁻²`

In footprint calculations, these factors are multiplied by land occupation or transformation data, which usually already include a time dimension such as `km²·yr` or `m²a`. The notebook’s `IBIF biodiversity (land use)` method sits in this family.

The land-use categories in the paper are:

- `cropland`
- `pasture`
- `plantation forest`
- `urban land`
- `mines`

Land use can affect biodiversity through multiple direct drivers:

- `habitat loss`
- `habitat fragmentation`
- `habitat disturbance`

Not every direct driver applies to every species group or every land-use type.

### Roads

For roads, the factors represent:

- **area-integrated MSA loss per kilometer of road**

The units are:

- `MSA-loss · km² · km⁻¹`

The paper explains that these factors need an extra conversion step before they can be used in LCA or MRIO applications, because inventories usually contain transport demand or fuel use rather than kilometers of national road network.

## What Varies Across Countries

Some IBIF values are nearly constant across countries, while others vary strongly. That depends on how the pressure is modeled.

- `CO2` is effectively global.
- Some habitat-loss factors are close to constant because the modeled response is driven mainly by a universal land-use impact relationship plus global climate.
- `NH3` and `NOx` vary strongly because deposition, natural-area shares, and atmospheric transport differ across countries.
- `Fragmentation` and `disturbance` vary strongly because they depend on how infrastructure or land use is embedded within surrounding natural habitat.

The figure below shows the country-level factors for **warm-blooded vertebrates**, including habitat loss, disturbance, and fragmentation from land use and roads.

![Country-level IBIF maps for warm-blooded vertebrates](assets/d4-03/ibif/figure_3_vertebrate_bifs.jpg)

*Extracted from the source PDF: country-level IBIF values for warm-blooded vertebrates across land-use and road-related pressures.*

These maps are useful for intuition. High factors do **not** simply mean that a country has high absolute biodiversity loss overall. They mean that **one unit of the pressure** generated in that country is associated with a relatively large attributed loss in local terrestrial intactness.

## How to Read `IBIF biodiversity (land use)` in Day 4

The Day 4 notebook uses the **land-use branch** of IBIF. In practice, that means:

- the characterized result responds to **where land occupation or land transformation occurs**
- the country of the consuming activity matters because the method is **country-level**
- the final score can be dominated by **upstream supply-chain locations**, not only by the foreground process location

This is why IBIF behaves differently from AWARE. AWARE follows water-related exchanges and local water scarcity. IBIF land use follows land occupation and transformation pressures and translates them into country-specific biodiversity-intactness losses.

For the Day 4 notebook, the most important interpretation points are:

1. `IBIF biodiversity (land use)` is a **country-level terrestrial biodiversity method**, not a species-extinction method.
2. The response variable is **MSA loss**, so the method tracks declines in local ecological intactness rather than disappeared fraction of species.
3. The score is sensitive to **supply-chain geography**, because land-use factors vary across countries.
4. The `overall` version averages plants and warm-blooded vertebrates, including zeros where one of the groups is not affected by a given pressure.

## Limits

The paper is explicit about several limits that matter for teaching and interpretation.

The published factors are based on **2020** input conditions. They are therefore appropriate for present-day footprinting, but not automatically valid for historical or future assessments.

The factors do **not** include biodiversity recovery after a pressure is released. They represent the duration of the altered state, not the full recovery trajectory after land abandonment or other pressure reduction.

The underlying GLOBIO relationships are **global and universal**, which means IBIF does not explicitly account for spatial differences in species richness, endemism, or community composition beyond what enters through modeled pressure patterns. For a broader biodiversity assessment, the authors recommend combining IBIF with complementary metrics.

Uncertainty is also present but not yet propagated into probabilistic BIF estimates.

## Bottom Line

IBIF is a country-level biodiversity footprint dataset built from **GLOBIO-derived MSA losses** that are attributed to inventory-facing pressures. It translates climate emissions, nitrogen emissions, land use, and roads into **terrestrial biodiversity intactness loss factors** for plants, warm-blooded vertebrates, and their overall average.

For Day 4 work, the main idea is simple: `IBIF biodiversity (land use)` makes land-related exchanges **geographically meaningful**. The same quantity of land occupation or transformation does not carry the same biodiversity-intactness consequence everywhere, which is why regionalized LCIA can expose upstream biodiversity hotspots that do not appear in a non-regionalized inventory.
