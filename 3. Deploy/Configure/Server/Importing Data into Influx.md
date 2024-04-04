1. **Prepare Your Spreadsheet**
   - **Open Your Spreadsheet**: Use your preferred spreadsheet software (e.g., Microsoft Excel, Google Sheets).
   - **Organize Data**: Arrange your data in columns. You need columns for each tag, field, and a timestamp. Also, ensure you have a column for the measurement name if it varies; otherwise, you'll set it as a default in the CSV annotations.

2. **Add InfluxDB Annotations**
   - **Insert Annotation Rows**: At the top of your spreadsheet, insert a few rows to add InfluxDB-specific annotations. You'll typically need three rows for `#datatype`, `#group`, and `#default`.
     - `#datatype`: Define the datatype for each column (e.g., `string`, `double`, `dateTime:RFC3339` for timestamps).
     - `#group`: This is usually `false` for all columns except in advanced use cases.
     - `#default`: Set default values for columns like measurement name if it's consistent. Leave blank for columns that vary per row.

3. **Export as CSV**
   - **Export/Save As CSV**: Once your spreadsheet is properly formatted, export or save it as a CSV file. In Excel or Google Sheets, you can use "File" > "Save As" or "Download" and then select CSV format.

4. **Verify CSV Format**
   - **Open in a Text Editor**: Open the exported CSV in a text editor (like Notepad++ or Visual Studio Code) to verify the format.
   - **Check for Extra Commas/Spaces**: Ensure there are no extra commas or spaces that might disrupt the CSV format.

5. **Example Conversion**
   Suppose you have the following spreadsheet data:

   | Measurement | Location | Temperature | Humidity | Timestamp            |
   | ----------- | -------- | ----------- | -------- | -------------------- |
   | Environment | London   | 23.4        | 68       | 2021-07-04T12:00:00Z |
   | Environment | Paris    | 25.1        | 75       | 2021-07-04T12:00:00Z |

   Your CSV with annotations might look like this:

   ```csv
   #datatype measurement,tag,double,double,dateTime:RFC3339
   #group false,false,false,false,true
   #default Environment,,,,,
   , London, 23.4, 68, 2021-07-04T12:00:00Z
   , Paris, 25.1, 75, 2021-07-04T12:00:00Z