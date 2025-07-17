# Skill Matching & Critical Zone Mapping – Renukiran NGO

## Context
Renukiran is an NGO dedicated to women empowerment, education, and social welfare. This module was developed as part of a larger project built for Renukiran NGO, which works toward women empowerment and social welfare. While the complete solution included multiple features, this contribution focuses specifically on:
1. Matching trained women to relevant job opportunities based on their skills.  
2. Identifying and visualizing underserved regions using available demographic and geospatial data.

The work presented here was contributed as part of a broader team solution built during JPMC CFG'25.

---

## 1. Skill Matching System

Developed a semantic matching feature to link job descriptions provided by employers with the skillsets of certified women beneficiaries. Key components:

- **Model Used**: `intfloat/e5-large-v2` – a sentence embedding model pre-trained for semantic search and matching tasks.
- **Input**: Recruiter's job description (e.g., “Looking for someone with MS Office and typing skills”).
- **Matching Logic**:
  - Converts both job description and user skills into vector embeddings.
  - Calculates similarity using **cosine distance**.
  - Uses a predefined **skill synonym map** to ensure broader matching (e.g., “computer course” ≈ “MS Office”, “Word”).
- **Output**: Ranked list of matching candidates, including their skills and contact information.

Planned improvements include incorporating work experience and feedback data to refine ranking and match relevance.

---

## 2. Critical Zone Mapping

To support outreach planning, a mapping interface was created to visualize areas needing attention based on literacy and employment statistics.

- **Data Source**: A dummy dataset inspired by real survey structures, containing fields like:
  - `Location_ID`, `Region`, `Latitude`, `Longitude`, `Female_Unemployment_Rate`, `Female_Literacy_Rate`
- **Processing**:
  - Aggregated and cleaned data using `pandas`.
  - Calculated a **Criticality Score** as a weighted function of literacy and unemployment.
  - Sorted and selected the top 3 regions based on this score.
- **Visualization**:
  - Used **Leaflet.js** to render an interactive map.
  - Circle markers were customized in size and color based on score.
  - Each location included a popup showing relevant statistics.

This feature can help the organization decide where to run future campaigns and transition from manual data collection to a scalable, location-based strategy.

---

## Technologies Used

| Area                | Tools/Frameworks                     |
|---------------------|--------------------------------------|
| Data Processing     | Python (Pandas)                      |
| NLP + Matching      | SentenceTransformers (`e5-large-v2`) |
| Visualization       | JavaScript (Leaflet.js), HTML/CSS   |
| Environment         | Google Colab (for experimentation)  |

---

## Future Scope

- Enable recruiter dashboards with filters by skill, location, and availability.
- Integrate real beneficiary data from digital forms with geolocation.
- Use historical job match data and experience to enhance recommendations.

---

## Contribution Summary

This module focused on building:
- A scalable **skill-to-job matching algorithm** using semantic similarity.
- A **geospatial mapping interface** to prioritize high-need areas.

Both components are designed for easy integration into a centralized platform to support real-world social impact through technology.
