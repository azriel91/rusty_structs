# Implementing Structs

```rust
# struct UnitStruct;
# //
struct NamedStruct {
    pub pub_field: u32,
    private_field: UnitStruct,
}
```

<details>
<summary>Class methods (static)</summary>

```rust
# struct UnitStruct;
# //
# struct NamedStruct {
#     pub pub_field: u32,
#     private_field: UnitStruct,
# }
impl NamedStruct {
    /// Returns a new `NamedStruct`.
    pub fn new() -> Self { // `Self` is an alias for `NamedStruct`
        NamedStruct {
            pub_field: 123,
            private_field: UnitStruct,
        }
    }

    // Note: no overloading.
    pub fn new_with_value(pub_field: u32) -> Self {
        # // let named_struct = NamedStruct {
        # //     pub_field: pub_field,
        # //     private_field: UnitStruct,
        # // };
        # // return named_struct;
        # //
        NamedStruct {
            pub_field,
            private_field: UnitStruct,
        }
    }

    fn private_function() -> u32 {
        3
    }

    // ..
}

# fn main() {
#     let _named_struct = NamedStruct::new();
# }
```
</details>

<details>
<summary>Instance methods</summary>

```rust
# struct UnitStruct;
# //
# struct NamedStruct {
#     pub pub_field: u32,
#     private_field: UnitStruct,
# }
# //
impl NamedStruct {
    // ..

    pub fn method_immutable(&self) -> u32 {
        // self.pub_field = 3; // Error: trying to mutate `self` which is immutable.
        self.pub_field
    }

    pub fn method_mutable(&mut self) {
        self.pub_field = Self::private_function();
    }

    // Uses:
    //
    // * Preventing use of a variable, e.g. `stream.close()`.
    // * Builder pattern, e.g. `struct_builder.build()`.
    pub fn consume_self(self) {}
# //
#     fn private_function() -> u32 {
#         3
#     }
}
```
</details>

## Example Usages

```rust
# struct UnitStruct;
# //
# struct NamedStruct {
#     pub pub_field: u32,
#     private_field: UnitStruct,
# }
# //
# impl NamedStruct {
#     pub fn new() -> Self {
#         NamedStruct {
#             pub_field: 123,
#             private_field: UnitStruct,
#         }
#     }
# //
#     pub fn new_with_value(pub_field: u32) -> Self {
#         NamedStruct {
#             pub_field,
#             private_field: UnitStruct,
#         }
#     }
# //
#     pub fn method_immutable(&self) -> u32 {
#         // self.pub_field = 3; // Error: trying to mutate `self` which is immutable.
#         self.pub_field
#     }
# //
#     pub fn method_mutable(&mut self) {
#         self.pub_field = Self::private_function();
#     }
# //
#     pub fn consume_self(self) {}
# //
#     fn private_function() -> u32 {
#         3
#     }
# }
# //
# fn main() {
let named_struct = NamedStruct::new();
assert_eq!(named_struct.method_immutable(), 123);

let named_struct = NamedStruct::new_with_value(1);
assert_eq!(named_struct.method_immutable(), 1);

// named_struct.method_mutable(); // Error: `named_struct` is immutable.

let mut named_struct = named_struct;
named_struct.method_mutable();

assert_eq!(named_struct.method_immutable(), 3);
#   println!("Result: Ok!");
# }
```
