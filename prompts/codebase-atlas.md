# Codebase architecture map prompt

Source inspiration: [Jay Scambler’s bookmarked post](https://x.com/JayScambler/status/2088356230968287547) and the related codebase-atlas description.

Use this only after inspecting the repository at its current revision:

> Analyze this repository at its current revision. Create an isometric system map with a legend and an explainer panel. Represent infrastructure and major components as distinct buildings on a grid. Trace real control and data paths with labeled dependencies and payloads. Support drill-down views for important subsystems, and cite the exact files that justify every component and connection. Clearly distinguish observed architecture from inference.

Verification requirements:

- Cite repository-relative files for every major node and edge.
- Mark inferred, planned, deprecated, and runtime-observed components differently.
- Do not include secrets, credentials, personal data, or learner/customer records.
- Keep the visualization disposable until a human confirms that it reflects the current system.

