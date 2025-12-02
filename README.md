📊 Global Researcher Mobility Analysis (2000–2025)

This repository contains SQL code for analysing global researcher mobility using Dimensions publication data and the Leiden Ranking (Open Edition 2025) list of universities.
It identifies the institutional and country affiliations on researchers’ first and most recent publications and constructs forward-looking and backward-looking mobility flows.

🔍 Purpose

The project investigates:
Which universities and countries researchers begin their academic publishing career (2000–2010), 
and then where they are affiliated on their most recent publication (2020–2025). This enables us to analyse:

- Flows of researchers from origin → destination countries

- Domestic retention rates

- Internationalization rates

- Reverse (destination → origin) mobility flows

- Mobility patterns aggregated by world region

- This workflow supports bibliometric studies of researcher careers and global mobility.

📂 Data Sources

This repository includes only code, not data.
The SQL requires access to the Dimensions_2025jul dataset hosted by CWTS at Leiden University.
Tables used include:
pub;
pub_author;
pub_author_affiliation;
pub_affiliation_organization;
organization;
country;
Leiden Ranking (Open Edition 2025).

⚙️ Requirements

Microsoft SQL Server (2017+ recommended)
Sufficient permissions to:
Create temporary tables in tempdb, 
Execute multi-join queries on large datasets, 
Access to Dimensions data in the schema expected by the SQL.

🧠 How the SQL Works (Pipeline)

1. Parameter setup.
Set the first-publication and last-publication year windows.
2. Identify each researcher’s first publication year using MIN(pub_year).
3. Filter first-year affiliations to Leiden Ranking universities using ROR ID matching.
4. Construct first-year country/university affiliation counts
5. Identify each researcher’s most recent publication (2020–2025)
6. Join to university/country affiliations for those final publications
7. Classify each researcher into:
- Still in Leiden
- Active outside Leiden
- No publications in analysis window
8. Forward mobility analyses
Origin → destination country flows
- Top 20 flows for each origin
- Domestic retention
- Internationalization rate
- Mobility matrices (country + region)
9. Backward mobility analyses
- Destination → origin flows
- Domestic origin share
- International origin share
- Reverse mobility matrices

▶️ How to Run

Open the SQL file.
Ensure the DECLARE statements remain at the top.
Run the entire script at once (Ctrl+A → F5).
Running partial batches will cause variable-not-declared errors.
Inspect each output block after execution.

📁 Repository Structure
README.md
analysis.sql

📈 Outputs

The script produces multiple tables including:

- #first_paper_university_counts
- #first_paper_country_counts
- #last_paper_university_counts
- #last_paper_country_counts
- #country_flows_leiden
- #destination_international_counts
- etc.
Each table’s purpose is explained in comments inside the SQL script.

📜 License

🙏 Acknowledgements

CWTS, Leiden University

Dimensions, Digital Science

Leiden Ranking (Open Edition 2025), Leiden University
