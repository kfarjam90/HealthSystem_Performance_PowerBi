# UK and Global Health System Performance
### Power BI analysis of pandemic pressures and recovery, 2018–2024

**32 countries · 212 fictional health system regions · 7 report pages · 45 DAX measures**

A Power BI portfolio project developed for the **Onyx Data #dataDNA Challenge**. The report examines how health systems absorbed the pandemic shock, how elective care recovered, and how the United Kingdom compares with the EU member countries included in the dataset.

> **Synthetic data**  
> All performance, workforce and spending figures were simulated for a training challenge. Findings describe this scenario and cannot be used as evidence about real countries, health systems or organisations. Health system regions are fictional.

<!-- Add a screenshot of the rendered report at images/dashboard-overview.png, then uncomment the next line.
![Overview of the Power BI health system performance report](images/dashboard-overview.png)
-->

## Project objectives

The report approaches the analysis from the perspective of a health system performance analyst reporting to an international policy board.

- Measure changes in acute care across the dataset's pandemic phases.
- Compare elective waiting times before the pandemic, during the backlog and after recovery.
- Benchmark UK spending, waiting times and workforce indicators against relevant country groups.
- Explore the relationship between staff burnout and vacancy rates at different levels of aggregation.
- Quantify recorded disease trends using annual slopes.

## Tools and approach

| Tool or format | Role in the project |
| --- | --- |
| Power BI Desktop | Report development, interactive charts and semantic model |
| Power Query / M | Loading the five embedded tables and assigning data types |
| DAX | KPI measures, baseline comparisons, country benchmarks, trend slopes and correlations |
| PBIP | Project structure suitable for Git version control |
| PBIR | Report pages, visual definitions, themes and image resources |
| TMDL | Readable semantic model, relationships and measure definitions |

The report uses a consistent visual design with page-specific accent colours, rounded panels, formatted tables and illustrative AI-generated healthcare photography.

## Dataset

This project uses the corrected November challenge dataset covering **2018 Q1 through 2024 Q4**.

| Table | Rows | Grain |
| --- | ---: | --- |
| dim_country | 32 | One row per country |
| dim_date | 28 | One row per calendar quarter |
| dim_health_system | 212 | One row per fictional health system region |
| fact_health_performance | 5,936 | One row per region per quarter |
| fact_workforce | 1,484 | One row per region per annual survey |

Currency is **USD**. Workforce surveys are associated with Q4 of their survey year.

Country reference attributes provide context for the simulation, including WHO region, income group, OECD membership and EU membership.

## Report pages

| Page | Focus |
| --- | --- |
| Overview | Headline KPIs and an executive interpretation of the scenario |
| Acute-care shock | ICU occupancy, ED 4-hour performance and recorded respiratory illness by phase and country |
| Elective backlog | Waiting times in 2019 and 2021, subsequent recovery, and UK comparisons |
| Health spending | UK spending per person against the sampled EU countries |
| Workforce | Annual burnout and vacancies, regional associations and group comparisons |
| Disease trends | Recorded cardiovascular disease, diabetes and cancer trends |
| Method and caveats | Definitions, weighting choices and interpretation limits |

## Selected findings

The figures below reflect the measures and aggregation choices in this report. Percentage-point differences are labelled **pp**.

| Area | Finding in the synthetic scenario | Measure, filter and period |
| --- | --- | --- |
| Acute pressure | ICU occupancy increased by approximately **9.5 pp**, while ED 4-hour performance fell by **3.7 pp**. | Average of all region-quarter observations, Acute Pandemic versus Pre-Pandemic |
| Delayed disruption | ED 4-hour performance reached its lowest phase average during Recovery, at approximately **65.1%**. | All regions, Recovery phase |
| Elective backlog | Average elective waits increased from approximately **9.0 to 17.0 weeks**, a rise of around **8.0 weeks**. | All region-quarter observations, calendar 2019 versus 2021 |
| Uneven recovery | Sweden, Norway, Denmark, Finland and Germany returned to within **0.3 weeks** of their own 2019 waiting times by 2024. UK waits remained around **15.5 weeks**, against **7.8 weeks** in 2019. | Annual within-country averages |
| Spending gap | UK spending averaged approximately **$4,781 per person**, compared with **$5,537** for the EU sample, or about **86.3%** of that benchmark. | 2018–2024, UK average versus equally weighted averages of the 10 sampled EU countries |
| Workforce strain | Burnout peaked at approximately **72.3 in 2022**, before easing to **63.7 in 2024**. | Average of the 212 regional annual survey observations in each year |
| Aggregation matters | Burnout and vacancies were positively associated across region-year surveys, with **r ≈ 0.58**. The association was much weaker across country averages, with **r ≈ 0.16**. | 1,484 region-year surveys versus 32 country means, both covering 2018–2024 |

Together, these results support further investigation of elective recovery capacity and persistent workforce pressures within the scenario. The association between burnout and vacancies depends on the unit of analysis and does not establish causation.

## Model and methodology

The model contains three dimensions and two fact tables. Each fact table relates directly to country, date and health system dimensions through six relationships in total.

**Averages and weighting**

Base rate, waiting-time and spending measures use averages of source observations. Overall results therefore give more weight to countries with more fictional regions.

UK-versus-EU measures calculate each EU country's average first, then average those country values. The EU benchmark includes the **10 EU member countries in the dataset**. Each country receives equal weight in that benchmark.

**Time comparisons**

Pandemic comparisons follow the phase labels supplied in the date table. Baseline and recovery comparisons use calendar years. Percentage-point changes are calculated by subtraction, while relative percentage changes divide the difference by the baseline.

**Trends and associations**

Disease trend measures fit a least-squares line through annual mean values. Slopes express change per calendar year in the metric's own units. Burnout-vacancy measures use Pearson correlation, with the unit of analysis stated alongside the result.

**Interpretation limits**

Recorded disease rates may reflect differences in recording as well as underlying disease patterns. Country groups contain only the countries supplied in the challenge. Spending comparisons use reported USD values without a purchasing-power or inflation adjustment.

## Open the report

1. Download the repository as a ZIP or clone it to your computer.
2. Extract the project and retain the report and semantic model folders beside the PBIP file.
3. Open **HealthSystemPerformance.pbip** in a recent version of Power BI Desktop for Windows with PBIP, PBIR and TMDL support.
4. Select **Home → Refresh** to load the embedded data.
5. Review each report page and check the headline values before presenting or publishing.

The five tables are embedded as compressed data in the Power Query definitions. This project copy requires no external CSV file paths or database credentials.

## Repository organisation

Upload the extracted project alongside this README. The main project components are listed below.

| Path | Contents |
| --- | --- |
| HealthSystemPerformance/HealthSystemPerformance.pbip | Project entry point |
| HealthSystemPerformance/HealthSystemPerformance.Report/ | Report definitions and visual assets |
| HealthSystemPerformance/HealthSystemPerformance.SemanticModel/ | TMDL model, embedded queries and DAX measures |
| HealthSystemPerformance/DESIGN_UPDATE.txt | Notes on the visual redesign |
| README.md | Project documentation |

If you place the PBIP and its two companion folders at the repository root, open the PBIP from that location instead. Their relative folder names must match the project references.

## Validation and project status

Source row counts and model definitions were inspected. The visual redesign retained the original data bindings, filters, chart types and narrative text across **47 existing visuals**. Semantic model files were compared with the uploaded source project and matched byte for byte.

Final rendering, refresh and DAX execution must be verified in Power BI Desktop. Suggested acceptance checks include the unfiltered ICU change of approximately **+9.5 pp**, elective wait change of **+8.0 weeks**, and UK spending at approximately **86.3%** of the EU benchmark.

Decorative panel backgrounds are embedded images. Moving or resizing visuals may require adjusting the corresponding page background.

## Author and acknowledgements

**Parham Farjam**  
Data Analytics · Data Science · Power BI

Created for the **#dataDNA Challenge** with acknowledgements to the challenge organisers and partners.

- [Onyx Data](https://www.linkedin.com/company/onyxdata/)
- [SmartFramesUI](https://www.linkedin.com/company/smart-frames-ui/)
- [DataCareerJumpstart](https://www.linkedin.com/company/datacareerjumpstart/)

Dataset attribution and reuse should follow the challenge provider's terms.
