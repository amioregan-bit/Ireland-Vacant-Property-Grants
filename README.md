# Ireland’s Vacant Property Grants — Power BI Project

**By Ami O’Regan | Data coverage to 30 September 2026**

## Project overview

Ireland’s housing crisis is a social crisis, affecting people’s ability to find a secure and affordable home. Bringing vacant properties back into use is one part of the response. The Vacant Property Refurbishment Grant, funded through the Croí Cónaithe (Towns) Fund, was launched on 14 July 2022. [Source: Department of Housing, Local Government and Heritage](https://www.gov.ie/en/department-of-housing-local-government-and-heritage/press-releases/vacant-property-refurbishment-grant-expanded-to-cities-and-remote-rural-areas/)

Having personally been through the Vacant Property Refurbishment Grant process, I’m one of the people behind these statistics. That experience made me want to understand how the scheme was progressing across the country.

The government publishes grant statistics in separate PDFs, but I wanted to compare local authorities, follow changes over time and explore how much funding had been paid. I built this Power BI report to bring those figures together and make them easier to explore.

The project also gave me practical experience applying my Power BI training to a subject I had a personal connection with, working through data-quality problems and presenting the results clearly.

**Tools:** Power BI Desktop, Power Query, DAX and Strawberry Browser as an AI learning and troubleshooting assistant.

## Data sources and scope

I used the quarterly grant-statistics PDFs published by the Department of Housing, Local Government and Heritage on gov.ie.

For the main refurbishment grant, I brought together council-level quarterly data from Q1 2023 to Q3 2026, covering 31 local authorities. I also included a separate 2022 year-end snapshot and cumulative figures to 30 September 2026.

I kept quarterly activity separate from cumulative totals to avoid double-counting. Above the Shop and Expert Advice grant data were prepared separately so they would not be confused with the main refurbishment scheme.

[Source example: Vacant Property Grant Statistics — July to September 2026](https://assets.gov.ie/static/documents/93cbc02e/Vacant_Property_Grant_Statistics__July_to_September_2026.pdf)

## How I worked through the project

### 1. Extracting and preparing the data

I used the Strawberry Browser AI agent as a step-by-step learning and troubleshooting assistant while carrying out the work in Power BI Desktop. It helped me work through unfamiliar steps, understand Power Query transformations and troubleshoot problems as they arose.

I imported the PDF tables into Power Query and identified the sections needed for each reporting period. Some council tables continued across several pages, so I combined these before adding them to the history.

The PDF layouts varied between publications. I checked the contents of each table rather than relying on its table number, removed unwanted heading and blank rows where necessary, and standardised the column names.

I assigned appropriate data types to council names, application counts, grant values and dates. I added a reporting-period end date and a quarterly/cumulative label so each record retained its context.

Once each quarter was prepared, I appended it to the appropriate history query, allowing comparisons across quarters in one report.

### 2. Cleaning Local Authority Names

The PDF imports sometimes split local authority names across lines or included extra spaces. This meant the same local authority could appear under several slightly different names. A check initially returned 60 distinct names instead of the expected 31.

With guidance from Strawberry Browser, I applied a Power Query transformation to remove inconsistent whitespace while preserving the spaces between words. I also standardised the spelling of Dún Laoghaire-Rathdown County Council.

I repeated the checks after cleaning. The main quarterly history returned 31 distinct local authority names, with no duplicate local-authority-and-quarter combinations.

This helped prevent a local authority’s figures from being split across different categories and supported consistent filtering.

### 3. Building the Data Model and Calculations

With guidance from Strawberry Browser, I created shared local authority and date tables, called Dim Council and Dim Date. I linked them to the main refurbishment, Above the Shop and Expert Advice quarterly history tables.

These relationships allowed the same local authority and date selections to filter the relevant quarterly data consistently. I tested the filters using individual local authorities and reporting periods.

I added year and quarter labels for chronological comparisons. I also used a DAX measure, developed with guidance, to make chart titles reflect the selected local authority and year.

I kept the cumulative snapshot separate from the quarterly history because they represent different reporting views.

### 4. Checking the Data and Results

I used check queries and temporary report tables to review row counts, local authority names, duplicate records, data types and totals. With assistance from Strawberry Browser, I compared the results with the published PDF tables and investigated differences.

I also tested local authority and date filters to check that the visuals showed the expected figures.

Some published national summaries did not agree with the totals obtained from the local authority tables. Where this happened, I retained the local authority figures and documented the discrepancy rather than changing the data to force agreement.

For example, the Q2 2026 Above the Shop local authority rows total 38 applications received, while the published summary reports 37.

### 5. Designing the Report

I organised the report into an overview and separate pages for quarterly trends, payments, funding value and local authority comparisons. I included explanations of the data sources, scheme background and known limitations.

I refined the layout with feedback from Strawberry Browser, using consistent fonts and colours, clear titles, short instructions and navigation buttons. Blue represents applications received and green represents approvals in the comparison charts.

I tested filtering, chart interactions and navigation. I also adjusted spacing and visual sizes to keep labels and explanatory notes readable without unnecessary scrolling.

### 6. Creating the Funding Map

I wanted a geographical view of the funding paid, alongside the charts and tables. I used an Ireland-only county shape map, shaded from light to dark green to show the total value paid.

The map boundaries represent counties rather than all 31 local authorities. With guidance from Strawberry Browser, I created a mapping field to group the local authorities into counties. This combines Cork and Galway city and county figures and groups all four Dublin local authorities under Dublin.

I retained a separate table showing each local authority’s figures and checked the Dublin, Cork and Galway groupings against it. Hovering over a county shows its totals, while selecting one displays its local authorities in the table.

I added a note explaining the grouping and colour scale. The map shows funding totals, not a measure of local authority performance.

## Limitations and interpretation

The report uses published summary statistics, not individual application records. It cannot show how long an applicant waited or follow the same application from receipt through approval to payment.

Applications received, approvals and payments in a quarter may relate to different applications. Their totals should not be treated as a conversion rate or a confirmed backlog.

Higher funding totals do not, on their own, demonstrate better local authority performance. This report does not adjust for differences such as population, eligible vacant properties or refurbishment costs.

The source publications contain some inconsistencies, which I have documented where identified. Updates require preparing and importing new PDF data; the report is not a live data feed.

## My Contribution and What I Learned

I carried out the work in Power BI Desktop, using the Strawberry Browser AI agent for step-by-step guidance, explanations and troubleshooting. I applied the transformations, tested the results and made decisions about the report’s scope, layout and wording.

This project helped me move from following Power BI training exercises to working with an inconsistent public dataset. I developed practical experience in Power Query, table relationships, guided DAX calculations, validation and report design.

I learned that building a useful report involves more than creating charts. It requires checking definitions, investigating discrepancies and being clear about what the data can and cannot tell us.

This is an ongoing learning project. AI assistance helped me work through unfamiliar steps, while I remained actively involved in applying, questioning and reviewing the work.
