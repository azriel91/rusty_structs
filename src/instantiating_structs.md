# Instantiating Structs

* Unit

    ```rust
    struct UnitStruct;

    fn main() {
        let _ = UnitStruct;
    #
    #   println!("Result: Ok!");
    }
    ```

* Tuple

    ```rust
    # #[derive(Debug, PartialEq)]
    # struct UnitStruct;
    #
    struct TupleStruct(u32, UnitStruct);
    type Unnamed = (u32, UnitStruct);

    fn main() {
        let named_tuple = TupleStruct(1, UnitStruct);

        assert_eq!(named_tuple.0, 1);
        assert_eq!(named_tuple.1, UnitStruct);

        // ---

        let unnamed_tuple = (1, UnitStruct);

        assert_eq!(unnamed_tuple.0, 1);
        assert_eq!(unnamed_tuple.1, UnitStruct);
    #
    #   println!("Result: Ok!");
    }
    ```

* Named

    ```rust
    # struct UnitStruct;
    #
    struct NamedStruct {
        pub pub_field: u32,
        private_field: UnitStruct,
    }

    fn main() {
        let named_struct = NamedStruct {
            pub_field: 1,
            private_field: UnitStruct,
        };

        assert_eq!(named_struct.pub_field, 1);
    #
    #   println!("Result: Ok!");
    }
    ```
