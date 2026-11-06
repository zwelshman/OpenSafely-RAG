1. Generating ehrQL Dataset Definitions

OpenSAFELY transitioned its data schema language to ehrQL (Electronic Health Record Query Language). Writing these definitions requires exact syntax for clinical event codes, dates, and patients.
• How to use your RAG: Ask it to write boilerplate dataset code based on existing repositories.
• Example Prompts:

	• "Show me how to define a dataset that extracts the most recent HbA1c lab result between two dates using ehrQL."
	• "Generate an ehrQL variable definition for identifying patients with a history of asthma based on SNOMED codes."

2. Matching Study Designs to the "OpenSAFELY Way"

OpenSAFELY enforces an "action-based" workflow where your analysis is split into distinct steps (e.g., data extraction, data cleaning, matching, analysis) defined in a project.yaml file.
• How to use your RAG: Use it to map out your study infrastructure so you don't fail the automated build checks.
• Example Prompts:

	• "Look at the standard template repositories. How do I structure a cohort matching study in the project.yaml file?"
	• "What are the required input and output arguments for a data-cleaning Python script in a typical OpenSAFELY pipeline?"

3. Decoding Codelists and Clinical Metadata

Navigating how clinical codelists (SNOMED-CT, ICD-10, CTV3) integrate with the code can be tricky.
• How to use your RAG: Have it explain how codelists are imported, referenced, and validated across the codebase.
• Example Prompts:

	• "How does the codebase handle the download and caching of codelists from OpenCodelists?"
	• "Give me an example of how a codelist is passed into an ehrQL where() filtering function."

4. Reverse-Engineering Existing Studies

Instead of reading through dozens of repository folders to see how another team did their statistics, let your RAG synthesize it.
• How to use your RAG: Ask it to summarize the implementation logic of specific public studies indexed in your RAG.
• Example Prompts:

	• "How did the [Specific Study Name/Repo] handle adjusting for confounding variables in their Cox proportional hazards model?"
	• "What Python or R packages are most commonly included in the Docker environments across these repositories for doing survival analysis?"

5. Troubleshooting Dummy Data Generation

OpenSAFELY requires you to test your code locally using automatically generated fake "dummy" data before submitting it to the real secure server.
• How to use your RAG: Use it to debug why your dummy data expectations aren't matching your dataset definitions.
• Example Prompts:
	• "Based on the ehrQL documentation in the repo, how do I specify custom distributions or prevalence rates for dummy data generation?"
