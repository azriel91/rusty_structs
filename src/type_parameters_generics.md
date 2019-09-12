# Type Parameters (Generics)

<details open>
<summary>☕ Java</summary>

```java
// MyClass.java
public class MyClass<T> {
    private T t;

    public MyClass(final T t) {
        this.t = t;
    }

    public T getT() {
        return this.t;
    }
}
```
</details>

<details>
<summary>🦀 Rust</summary>

```rust
struct TupleStruct<T>(T);

struct NamedStruct<T> {
    t: T,
}

impl<T> NamedStruct<T> {
    pub fn t(&self) -> &T {
        &self.t
    }
}

fn main() {
    let _: TupleStruct<u32> = TupleStruct(1);
    let _: TupleStruct<_> = TupleStruct(true);
    let _ = TupleStruct(TupleStruct(1));

    let _ = NamedStruct { t: TupleStruct(1) };
}
```
</details>

<details>
<summary>🦀 Rust (difficult)</summary>

```rust,editable
struct FunctionHolder<F, T>
where
    F: FnOnce() -> T
{
    pub f: F,
    // marker: std::marker::PhantomData<T>,
}

fn main() {
    let f = FunctionHolder {
        f: || { println!("hello"); 123 },
        // marker: std::marker::PhantomData,
    };

    let v = (f.f)();
    println!("{}", v);
}
```
</details>
