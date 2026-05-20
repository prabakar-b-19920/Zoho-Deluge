# Zoho-Deluge

## Update one field from another field (same module)

Use this Deluge custom function to copy a value from a source field to a target field in the same module record.
Replace `Source_Field_API_Name` and `Target_Field_API_Name` with your actual CRM field API names.
Update `module_name` and `record_id` assignment based on where the function runs (workflow, custom button, or another trigger).
Choose an `ifnull` fallback value that matches your target field type (for example, `0` for number fields).

```deluge
module_name = "Leads";
record_id = input.recordId.toLong();

record_data = zoho.crm.getRecordById(module_name, record_id);
fallback_value = ""; // For text fields. Use 0 for number fields, etc.
source_value = ifnull(record_data.get("Source_Field_API_Name"), fallback_value);

update_map = Map();
update_map.put("Target_Field_API_Name", source_value);

response = zoho.crm.updateRecord(module_name, record_id, update_map);
info response;
```
