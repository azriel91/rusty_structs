# Unit, Tuple, Named

There are 3 kinds of `struct`s:

* Unit

    ```rust
    // No fields.
    struct UnitStruct;
    ```

* Tuple

    ```rust
    # struct UnitStruct;
    # //
    // Fields have no names:
    struct TupleStruct(u32, UnitStruct);

    // Visibility modifiers are per field.
    pub struct TupleStruct(pub u32, pub UnitStruct);

    // Unnamed tuple:
    type Unnamed = (u32, UnitStruct);
    ```

    <details>
    <summary>Uses</summary>

    - Returning multiple values

        ```rust
        fn dimensions() -> (u32, u32) {
            (800, 600)
        }

        let (w, h) = dimensions();
        ```

    - Iterator closure arguments

        ```rust
        let numbers = vec![10, 23, 34];
        numbers
            .iter()
            .enumerate()
            .for_each(|(index, number)| {
                println!("{}: {}", index, number);
            })
        ```

    </details>

* Named

    ```rust
    # struct UnitStruct;
    # //
    struct NamedStruct {
        pub pub_field: u32,
        private_field: UnitStruct,
    }
    ```
