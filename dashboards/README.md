# Power BI dashboard

The PBIX is copied unchanged from the original project and may contain imported data and local source paths. It is not connected to the generated demo CSV. Screenshots in `assets/` show the original report visuals.

To refresh:
1. Run the notebook with your original dataset.
2. Find the `part-*.csv` file under `outputs/cleaned_shipments/` (Spark writes a directory, not a single file named CSV).
3. Open the PBIX in Power BI Desktop.
4. Under Transform data / Data source settings, replace the existing source path with the exported CSV. Review the query's Source step if necessary.
5. Check column types, transformations and visual measures, then refresh and save.

The binary dashboard was inspected as an archive during packaging but was not opened or refreshed in Power BI Desktop. Confirm permission to publish its embedded academic dataset before making the repository public.
