# Zoho-Deluge

## Update one field from another field (same module)

Use this Deluge custom function to copy a value from a source field to a target field in the same module record.
Replace `Source_Field_API_Name` and `Target_Field_API_Name` with your actual CRM field API names.

```deluge
module_name = "Leads";
record_id = input.recordId.toLong();

record_data = zoho.crm.getRecordById(module_name, record_id);
source_value = ifnull(record_data.get("Source_Field_API_Name"), "");

update_map = Map();
update_map.put("Target_Field_API_Name", source_value);

response = zoho.crm.updateRecord(module_name, record_id, update_map);
info response;
```
