<a name="models.helpers.pydantic"></a>
# models.helpers.pydantic

<a name="models.helpers.pydantic.create_pydantic_field"></a>
#### create\_pydantic\_field

```python
create_pydantic_field(field_name: str, model: Type["Model"], model_field: "ManyToManyField") -> None
```

Registers pydantic field on through model that leads to passed model
and is registered as field_name passed.

Through model is fetched from through attributed on passed model_field.

**Arguments**:

- `field_name` (`str`): field name to register
- `model` (`Model class`): type of field to register
- `model_field` (`ManyToManyField class`): relation field from which through model is extracted

<a name="models.helpers.pydantic.get_pydantic_field"></a>
#### get\_pydantic\_field

```python
get_pydantic_field(field_name: str, model: Type["Model"]) -> "ModelField"
```

Extracts field type and if it's required from Model model_fields by passed
field_name. Returns a pydantic field with type of field_name field type.

**Arguments**:

- `field_name` (`str`): field name to fetch from Model and name of pydantic field
- `model` (`Model class`): type of field to register

**Returns**:

`pydantic.ModelField`: newly created pydantic field

<a name="models.helpers.pydantic.populate_pydantic_default_values"></a>
#### populate\_pydantic\_default\_values

```python
populate_pydantic_default_values(attrs: Dict) -> Tuple[Dict, Dict]
```

Extracts ormar fields from annotations (deprecated) and from namespace
dictionary of the class. Fields declared on model are all subclasses of the
BaseField class.

Trigger conversion of ormar field into pydantic FieldInfo, which has all needed
parameters saved.

Overwrites the annotations of ormar fields to corresponding types declared on
ormar fields (constructed dynamically for relations).
Those annotations are later used by pydantic to construct it's own fields.

**Arguments**:

- `attrs` (`Dict`): current class namespace

**Returns**:

`Tuple[Dict, Dict]`: namespace of the class updated, dict of extracted model_fields

<a name="models.helpers.pydantic.get_pydantic_base_orm_config"></a>
#### get\_pydantic\_base\_orm\_config

```python
get_pydantic_base_orm_config() -> Type[pydantic.BaseConfig]
```

Returns empty pydantic Config with orm_mode set to True.

**Returns**:

`pydantic Config`: empty default config with orm_mode set.

<a name="models.helpers.pydantic.get_potential_fields"></a>
#### get\_potential\_fields

```python
get_potential_fields(attrs: Dict) -> Dict
```

Gets all the fields in current class namespace that are Fields.

**Arguments**:

- `attrs` (`Dict`): current class namespace

**Returns**:

`Dict`: extracted fields that are ormar Fields

<a name="models.helpers.pydantic.remove_excluded_parent_fields"></a>
#### remove\_excluded\_parent\_fields

```python
remove_excluded_parent_fields(model: Type["Model"]) -> None
```

Removes pydantic fields that should be excluded from parent models

**Arguments**:

- `model` (`Type["Model"]`): 

