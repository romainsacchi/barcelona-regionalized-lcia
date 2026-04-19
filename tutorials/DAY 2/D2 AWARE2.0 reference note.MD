# D2 AWARE2.0 Reference Note

This note supports the Day 2 regionalized LCIA notebooks, especially `D2-02 Edges fundamentals and regionalisation concepts.ipynb`, `D2-05 Regionalised methods across impact categories.ipynb`, and `D2-06 Variability and uncertainty in regionalised LCIA.ipynb`. It explains what AWARE2.0 is, how its equations work, how the main variables are defined, and how to interpret the resulting regionalized water scarcity factors in LCA.

## What AWARE2.0 Measures

AWARE2.0 quantifies the **potential deprivation caused by consuming water** in a specific basin and month. The method asks a simple question: after human use and environmental protection are accounted for, how much water remains available in that place and time? Water consumption is characterized as more critical where that remaining amount is small, and less critical where it is large.

The method stays at the **midpoint** level. It does not calculate final damage to ecosystems or human health. Instead, it estimates how strongly one cubic meter of consumed water may contribute to local scarcity pressure. The result is a characterization factor expressed in **m3 world-eq./m3**, which compares the local situation to a world reference.

AWARE2.0 provides factors at **native basin-month resolution**, which is the core resolution of the method. It also provides annual values and country-level aggregations for practical use in regionalized LCIA, including geometry definitions aligned with `ecoinvent` and `GLAM`. The published dataset covers **9406 basins and subbasins** and also includes an alternative expression in **maximum deprivation equivalents (MDE)**.

## Core Equations

The central quantity is the monthly basin-level **available water remaining**:

```text
AMD_ij = (ActAvail_ij - EWR_ij) / Area_i
```

`AMD_ij` is the water left in basin `i` during month `j`, normalized by basin area. Each term has a clear interpretation:

- `ActAvail_ij`: actual water available after human water use and water management have already altered the flow regime.
- `EWR_ij`: environmental water requirement, meaning the portion that should remain available for aquatic ecosystems.
- `Area_i`: basin area, used to normalize the result so basins can be compared more consistently.

This equation means that water scarcity is not based on total flow alone. It depends on the amount of water that still remains **after subtracting what should stay in the river system for ecosystems**, and then relating that remaining amount to basin size.

The environmental water requirement is:

```text
EWR_ij = EFR_ij * NatAvail_ij
```

`NatAvail_ij` is the naturalized flow, meaning the water that would be available without human withdrawals and dam operations. `EFR_ij` is the environmental flow coefficient, which sets the share of that naturalized flow reserved for ecosystems. AWARE2.0 keeps the variable monthly flow logic, but it smooths the intermediate-flow category and uses the outflow cell rather than basin-wide averaging when determining the coefficient.

The local AMD values are turned into a world reference through a consumption-weighted average:

```text
AMD_world_avg = sum(AMD_ij * HWC_ij) / sum(HWC_ij)
```

This is not a simple arithmetic mean. Basin-month combinations with more human water consumption count more heavily in the global reference. That weighting step matters because the final characterization factor is defined relative to this benchmark rather than in isolation.

The final characterization factor is:

```text
CF_ij = AMD_world_avg / AMD_ij
```

This inverse relation drives the interpretation. If little water remains locally, `AMD_ij` is small and `CF_ij` becomes large. If much water remains, `CF_ij` becomes small. AWARE2.0 caps factors between **0.1** and **100 m3 world-eq./m3** to keep the method stable in very wet or very scarce situations.

These are **marginal** characterization factors. They are meant for ordinary LCA inventories that do not themselves transform basin-scale hydrology. In practice, that is exactly the intended use in regionalized LCIA.

## How AWARE2.0 Defines the Main Variables

AWARE2.0 is built from **WaterGAP2.2e** at **0.5° x 0.5°** resolution. Water demand is modeled across irrigation, domestic use, manufacturing, electricity, and livestock, with post-processing used to improve representation of the most recent years.

`ActAvail_ij` is based on **actual discharge leaving a basin after upstream human influence**, including water consumption and water management. In AWARE2.0, actual availability uses the **1990-2019** period, which anchors the method in recent hydrological conditions.

`NatAvail_ij`, used in the environmental requirement, is based on **naturalized discharge**, meaning flow without withdrawals and dam operations. For AWARE2.0, the environmental baseline still uses a **1960-2010** naturalized reference period. The logic is that environmental protection is anchored to a baseline natural flow regime rather than being recalculated from the exact same recent actual period used for current availability.

`Area_i` uses **land area rather than full grid-cell area**. This matters especially in coastal basins, where a basin may occupy only part of a grid cell.

`HWC_ij` in the world-weighted average is based on **actual human water consumption**, not only theoretical demand. That makes the world benchmark better aligned with the inventory logic of LCA.

## Spatial Cases That Need Special Treatment

AWARE2.0 includes several implementation choices that are easiest to understand as method features rather than exceptions.

**Inland sinks** need a specific approximation because terminal sink cells do not produce regular basin outflow in the hydrological model. AWARE2.0 therefore estimates remaining water from inflow, local runoff, local consumption, and environmental demand in the sink cell.

**Large river deltas** are treated as integrated systems when estimating actual availability. Without that step, side branches can look artificially disconnected from the main river and appear drier than they really are.

**Subdivided basins** are handled in a way that reflects upstream-downstream propagation. If an upstream subbasin is assessed in complete isolation, downstream deprivation potential can be understated. AWARE2.0 therefore links upstream subbasins with their downstream continuation unless local scarcity is already lower than the broader downstream-based calculation would imply.

![Conceptual scheme for AWARE2.0 treatment of subdivided basins](assets/aware2/figure_1_subbasin_scheme.jpg)

*Extracted from the source PDF: schematic of the AWARE2.0 subbasin logic and the exception case when local AMD is already lower.*

This subbasin logic is important because it changes the interpretation of who may be deprived by upstream consumption. In AWARE2.0, the question is not only “how scarce is this subbasin locally?” but also “how much scarcity pressure can move through the downstream system?”

## Reading AWARE2.0 Outputs

The figure below shows the **annual arithmetic average** of AWARE2.0 characterization factors at basin level. This is not the native monthly output, but it is a useful overview of the global pattern.

![Annual arithmetic average of AWARE2.0 characterization factors](assets/aware2/figure_2_annual_cf_map.png)

*Extracted from the source PDF: annual arithmetic average of AWARE2.0 basin factors.*

Warm colors indicate higher characterization factors, meaning less water remains available relative to the world benchmark. Cool colors indicate lower characterization factors, meaning more water remains available. The map should be read as a **relative scarcity surface**. It does not mean that red basins are “running out of water” in an absolute sense, or that blue basins are hydrologically unproblematic in every respect. It means the deprivation potential of one cubic meter of consumed water is higher in red basins than in blue ones according to the AWARE2.0 calculation.

For interpretation, three things matter:

- The **native result is monthly and basin-specific**. Annual maps are summaries.
- Country-level factors are **aggregations** of basin-month values, not direct hydrological measurements.
- The world benchmark is embedded in the factor itself. A CF is always relative to `AMD_world_avg`.

The published global reference value for AWARE2.0 is `AMD_world_avg = 0.02410 m3/m2 month`. This number matters because it anchors all characterization factors. When local `AMD_ij` falls below that reference, the factor rises above 1. When local `AMD_ij` exceeds it, the factor falls below 1.

## Using AWARE2.0 in Day 2

In the Day 2 notebooks, AWARE2.0 enters as a **regionalized characterization method**. The practical interpretation is straightforward: water consumption should not be treated as equally critical everywhere. The location and timing of consumption matter because the characterization factor depends on basin-specific hydrology and environmental water protection.

Three points are especially important while working with the notebook:

1. The characterization factor is a **relative scarcity indicator**, not a direct hydrological measurement.
2. Basin and month are the core resolution of the method, so annual or country values always compress seasonality and spatial detail.
3. AWARE2.0 is about **deprivation potential of water consumption**, not about total water withdrawals in general.

## Limits

AWARE2.0 is still not a full hydrological assessment. It does not explicitly represent **fossil groundwater depletion** or fully capture **major inter-basin water transfers**. Uncertainty also remains high in very scarce regions, where the upper cutoff of the method improves robustness but reduces differentiation among the most stressed basins.

That limitation is acceptable for comparative LCA, but it matters for interpretation. AWARE2.0 should be treated as a strong midpoint indicator for regionalized impact assessment, not as a substitute for local water management analysis.

## Bottom Line

AWARE2.0 can be read as a basin-month method built from four pieces: actual water availability, environmental water requirement, basin area, and a world consumption-weighted reference. Its characterization factor becomes high where little water remains after human and ecological needs are accounted for, and low where more water remains.

For Day 2 work, that is the key interpretation to keep in mind: AWARE2.0 turns water consumption into a **location-sensitive and time-sensitive scarcity impact**, which is why regionalized LCIA can say much more than a simple inventory of cubic meters consumed.
