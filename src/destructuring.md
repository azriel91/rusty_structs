# Destructuring

```rust
struct Sub {
    pub name: String,
}

struct NamedStruct {
    pub sub: Sub,
    pub number_0: u32,
    pub number_1: u32,
}

fn main() {
    let named_struct = NamedStruct {
        sub: Sub {
            name: String::from("sub_name"),
        },
        number_0: 0,
        number_1: 1,
    };

    let NamedStruct {
        sub,
        number_0: abc_0,
        number_1: abc_1,
    } = &named_struct;

    println!("Sub::name: {}", &sub.name);
    println!("number_0: {}", abc_0);
    println!("number_1: {}", abc_1);
    println!();

    f(&named_struct);
}

fn f(named_struct: &NamedStruct) {
    let NamedStruct {
        sub: Sub { name },
        ..
    } = named_struct;

    println!("Sub::name: {}", name);
}
```

<details>
<summary>Use Cases</summary>

* Destructuring enum variants
* Procedural macros

    ```rust,ignore
    let ast = parse_macro_input!(item as DeriveInput);

    if let Data::Struct(DataStruct {
        fields: Fields::Named(fields_named),
        ..
    }) = &ast.data
    {
        // do something with `fields_named`.
    } else {
        panic!("This macro must be used on a struct with named fields.");
    }
    ```

</details>
