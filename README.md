# model-examples

Example models of [model-algebra](https://github.com/model-algebra/model-algebra), in the format of
[model-schema](https://github.com/model-algebra/model-schema). The tests of the other projects use them: this
repository is a Git submodule of model-algebra, model-algebra-typescript, ddl-bridge-typescript and
typescript-bridge.

## Models

| File | Model | |
|---|---|---|
| `user_core_model.json` | User | Core user fields: id, login and names |
| `user_extended_model.json` | User extended model | More user fields: birth date, address, phone with a regex, hair color with allowed values, height |
| `user_core_add_extended.json` | User | The union of the two above: what `add` must give |
| `all_types_model.json` | AllTypes | One field of every canonical type |
| `shop_database/*.json` | User, Product, Order, DeliveryType, Discount | Related models of a shop, with foreign keys between them |

## Invalid and other files

| File | |
|---|---|
| `invalid_model.json` | A model breaking the schema on purpose, for validator tests |
| `user_db_model.json` | An early draft of database options in a model; not valid against the schema |
| `town_core_model.json` | A JSON Schema of a Town model, not a model |

`user_extended_model.json` and `user_core_add_extended.json` use the type `date`. The bridges accept it, but
`model-schema.json` does not list it among the older lowercase types, so these two don't validate.

## Operation results

`processor/` holds two named lists of values and the expected result of each set operation on them:

| File | |
|---|---|
| `source1.json`, `source2.json` | The inputs |
| `result_union.json` | Entries of both, the first input's values winning |
| `result_intersection.json` | Entries both have |
| `result_subtraction.json` | Entries of the first that the second does not have |
| `result_xor.json` | Entries only one of them has |

Entries are matched by `name`; nested objects are combined the same way.

## License

MIT
