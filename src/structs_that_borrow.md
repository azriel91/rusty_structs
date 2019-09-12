# Structs that Borrow

```rust,editable
struct Book {
    title: String,
}

struct Borrower<'bk> {
    book: &'bk Book,
}

fn main() {
    let book = Book { title: String::from("The Rust Programming Language") };
    let borrower = Borrower { book: &book };

    drop(book);
    drop(borrower);

    println!("Result: Ok!")
}
```

<details>
<summary>Use Cases</summary>

* Not allocating memory unnecessarily.
* Parameter object: A "view" over data retrieved from multiple sources.
</details>

