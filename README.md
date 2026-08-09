# Governmental Expenditure and Measure-Mapping Data Previews

This directory contains data previews supporting the study *Beyond Cost-Effectiveness: Improving Governmental Expenditure Efficiency in Watershed Governance through Performance-based Appraisal Design*. The data describe governmental expenditure records and the mapping of project narratives to 23 watershed-governance measures.

## Files

| File | Language | Dimensions | Content |
|---|---:|---:|---|
| `GEWGTABLES.xlsx` | Chinese | Multiple worksheets | Full working workbook for `Preview_GEWGTABLES.csv`. |
| `PROJECT2MEASURES.xlsx` | Chinese | Two worksheets | Full working workbook for `Preview_PROJECTS2MEASURES.csv`|
| `Preview_GEWGTABLES.csv` | English | 11 rows × 19 columns | Preview of governmental budget, expenditure, performance-target, completion, and provenance records. |
| `Preview_PROJECTS2MEASURES.csv` | English | 10 rows × 49 columns | Preview of project descriptions, binary project-to-measure assignments, and assignment rationales. |

## `Preview_GEWGTABLES.csv`

Each row represents one governmental project record extracted from a public budget or final-account document. Monetary fields retain the units reported in the working dataset, generally ten thousand CNY. `execution_rate` is stored as a proportion from 0 to 1.

| Column | Type | Content |
|---|---|---|
| `project_name` | Text | Name of the government-funded project. |
| `responsible_department` | Text | Government department responsible for the project. |
| `fiscal_allocation` | Numeric | Fiscal amount formally allocated to the project, when reported. |
| `annual_budget` | Numeric | Full-year project budget. |
| `initial_budget` | Numeric | Budget reported at the beginning of the fiscal year. |
| `approved_budget` | Numeric | Confirmed or approved budget amount, when available. |
| `annual_expenditure` | Numeric | Realized expenditure for the full year. |
| `planned` | Numeric | Harmonized planned amount used in downstream analysis, selected from the available budget fields. |
| `execution_rate` | Numeric | Budget execution ratio, calculated as realized expenditure divided by the harmonized planned amount. |
| `expected_objective` | Text | Project objective or expected performance target reported in the source document. |
| `actual_completion` | Text | Reported implementation status, outputs, or performance achieved. |
| `workbook` | Text | Source workbook filename. In the English preview, this metadata is translated for accessibility. |
| `sheet_name` | Text | Worksheet from which the record was extracted. |
| `source_file` | Text | Source-document path recorded during data compilation. The `_cn.csv` version preserves the exact original Chinese path. |
| `dept` | Categorical text | Normalized department or policy-sector category, such as natural resources, ecology and environment, lake management, or water resources. |
| `year` | Integer | Fiscal year of the record. |
| `level_all` | Categorical text | Administrative level or jurisdiction associated with the record, such as Yunnan Province, Yuxi City, or Tonghai County. |
| `proj` | Text | Structured composite description combining project name, expected objective, and actual completion. |
| `comp_desc` | Text | Concatenated project description used for text processing and project classification. |

## `Preview_PROJECTS2MEASURES.csv`

Each row represents one project narrative evaluated against 23 watershed-governance measures. Measure columns are binary: `1` indicates that the project was assigned to the measure, and `0` indicates that it was not. The matching `*_reason` column records the classification rationale.

### Project and summary columns

| Column | Type | Content |
|---|---|---|
| `project_description` | Text | Composite project narrative containing the project name, expected objective, and reported completion. |
| `reason` | Text | Ordered aggregation of the 23 measure-specific rationales. It may contain plain text and fenced JSON because both forms occurred in the classification output. |
| `sum` | Integer | Number of measures assigned to the project; equal to the sum of the 23 binary measure columns. |

### Measure-assignment columns

| Column | Type | Watershed-governance measure represented by `1` |
|---|---|---|
| `Pipe` | Binary | Construction or improvement of urban sewer and drainage-pipe networks. |
| `PipeCCTV` | Binary | CCTV/QV inspection, diagnosis, and repair of existing sewer networks, including related GIS records. |
| `RuralPipe` | Binary | Centralized rural domestic-sewage collection networks. |
| `RuralEmerge` | Binary | Emergency centralized treatment of rural domestic wastewater or swill. |
| `RuralDistribute` | Binary | Decentralized rural domestic-wastewater treatment facilities. |
| `WWTPExpand` | Binary | Expansion of wastewater-treatment-plant capacity. |
| `WWTPTech` | Binary | Upgrade or retrofit of wastewater-treatment processes. |
| `WWTPWetland` | Binary | Constructed wetlands or related polishing systems for wastewater-treatment-plant effluent. |
| `Gen_PlantTrans` | Binary | Transition of planting structure toward environmentally friendly or conservation-oriented crops. |
| `Gen_OrganicFert` | Binary | Organic-fertilizer substitution and green pest-management demonstrations. |
| `Gen_ModernPlant` | Binary | Modernized planting technologies, including integrated irrigation and fertilization, high-standard farmland, or agricultural water-price reform. |
| `Intercept` | Binary | Pollution-interception or ecological storage-belt construction and management. |
| `InterceptReuse` | Binary | Reuse of intercepted or stored water, including pumping, storage, treatment, and irrigation. |
| `InterceptTreat` | Binary | Treatment of intercepted water, including mobile or integrated treatment facilities. |
| `RiverLeakage` | Binary | Investigation, control, or remediation of river pollution outlets and leakage sources. |
| `RiverClean` | Binary | Routine river cleaning, refuse removal, inspection, and corrective action. |
| `RiverEngineering` | Binary | Riverbank protection, ecological restoration, and other river-engineering works. |
| `RiverDredging` | Binary | River dredging and removal of contaminated sediment. |
| `AlgaeStation` | Binary | Construction or operation of fixed algae-water separation stations. |
| `AlgaeMobile` | Binary | Mobile algae-water separation or emergency cyanobacteria-control equipment. |
| `MannualDredge` | Binary | Manual removal of cyanobacteria, aquatic vegetation, or shoreline refuse. |
| `AlgaeInsitu` | Binary | In-situ algae control, including deep-well control or relevant biological measures. |
| `Sediment` | Binary | Treatment, testing, or removal of lake-bottom sediment. |

> [!IMPORTANT]
> `MannualDredge` retains the spelling used in the source schema so that the preview remains compatible with the full workbook and analysis code.

### Measure-specific rationale columns

Every rationale column corresponds one-to-one with the binary measure column of the same prefix.

| Column | Content |
|---|---|
| `Pipe_reason` | Rationale for the `Pipe` assignment. |
| `PipeCCTV_reason` | Rationale for the `PipeCCTV` assignment. |
| `RuralPipe_reason` | Rationale for the `RuralPipe` assignment. |
| `RuralEmerge_reason` | Rationale for the `RuralEmerge` assignment. |
| `RuralDistribute_reason` | Rationale for the `RuralDistribute` assignment. |
| `WWTPExpand_reason` | Rationale for the `WWTPExpand` assignment. |
| `WWTPTech_reason` | Rationale for the `WWTPTech` assignment. |
| `WWTPWetland_reason` | Rationale for the `WWTPWetland` assignment. |
| `Gen_PlantTrans_reason` | Rationale for the `Gen_PlantTrans` assignment. |
| `Gen_OrganicFert_reason` | Rationale for the `Gen_OrganicFert` assignment. |
| `Gen_ModernPlant_reason` | Rationale for the `Gen_ModernPlant` assignment. |
| `Intercept_reason` | Rationale for the `Intercept` assignment. |
| `InterceptReuse_reason` | Rationale for the `InterceptReuse` assignment. |
| `InterceptTreat_reason` | Rationale for the `InterceptTreat` assignment. |
| `RiverLeakage_reason` | Rationale for the `RiverLeakage` assignment. |
| `RiverClean_reason` | Rationale for the `RiverClean` assignment. |
| `RiverEngineering_reason` | Rationale for the `RiverEngineering` assignment. |
| `RiverDredging_reason` | Rationale for the `RiverDredging` assignment. |
| `AlgaeStation_reason` | Rationale for the `AlgaeStation` assignment. |
| `AlgaeMobile_reason` | Rationale for the `AlgaeMobile` assignment. |
| `MannualDredge_reason` | Rationale for the `MannualDredge` assignment. |
| `AlgaeInsitu_reason` | Rationale for the `AlgaeInsitu` assignment. |
| `Sediment_reason` | Rationale for the `Sediment` assignment. |

## Recommended use

- Use the CSV files for lightweight inspection, code examples, and repository previews.
- Use the XLSX workbooks when the full working data or intermediate worksheets are required.
- Treat the Chinese files as authoritative for source wording and provenance identifiers.
- Interpret project-to-measure assignments as classification outputs based on reported project descriptions, not as direct field verification of project implementation.
