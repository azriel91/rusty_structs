# Newtype

```rust
use std::ops::Mul;

pub struct MyString(pub String);

impl Mul<u32> for MyString {
    type Output = Self;

    fn mul(self, rhs: u32) -> Self {
        let s = String::with_capacity(5 * self.0.len());
        let concatenated = (0..rhs)
            .fold(s, |mut s, _| {
                s.push_str(&self.0);
                s
            });

        MyString(concatenated)
    }
}

fn main() {
    let my_string = MyString(String::from("hello"));
    let my_string = my_string * 5;

    println!("my_string: {}", &my_string.0);
}
```

<details>
<summary>Use Cases</summary>

* Strongly typed instead of stringly typed.
* Circumventing orphan rule.

    Not allowed to implement a trait on a type if your crate does not define at least one of them.
</details>
