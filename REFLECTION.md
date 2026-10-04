# BrewMetrics BI — Reflection

## Reflection on GitHub Copilot and Version-Controlled Development

This project helped me understand how AI assistance and version control can be combined in a Business Intelligence workflow. GitHub Copilot was useful during the development of DAX measures because it provided starting points for calculations such as Month-over-Month Sales Growth, Running Total Sales, Product Sales Rank, and Average Order Value. Instead of writing every formula from scratch, I could review Copilot's suggestions and compare them with the BrewMetrics semantic model.

However, Copilot suggestions were not accepted blindly. I checked the table names, column names, relationships, date table, filter context, and calculation logic before using each formula. This showed me that understanding DAX and the underlying data model is still important even when AI tools are available. The `NOTES.md` file was used to record the Copilot suggestions and the review process.

Using GitHub and GitHub Desktop also helped me understand the importance of version-controlled BI development. The Power BI project was saved in `.pbip` format so that the report and semantic model could be tracked as files. Separate commits were created for the star schema and individual DAX measures, making it possible to follow the development history.

Overall, Copilot improved productivity, while manual validation and Git version control provided accuracy, transparency, and traceability throughout the project.