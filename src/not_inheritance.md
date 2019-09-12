# (Not) Inheritance

<details open>
<summary>☕ Java</summary>

```java
public abstract class Parent {}
public interface Interface1 {}
public interface Interface2 {}

public class MyClass
    extends Parent
    implements Interface1, Interface2 {}
```
</details>

<details>
<summary>🦀 Rust</summary>

```rust
trait Trait1 {
    fn trait1(&self) { println!("one"); } // Default impl.
}
trait Trait2 {
    fn trait2(&self); // No default impl, must be implemented.
}
trait Trait3 {
    fn trait3() { println!("three"); }
}

struct Struct {}
impl Trait1 for Struct {}
impl Trait2 for Struct {
    fn trait2(&self) { println!("two"); }
}
impl Trait3 for Struct {}

fn main() {
    let s = Struct {};
    s.trait1();
    s.trait2();
    Struct::trait3();
}
```
</details>

<details>
<summary>🦀 Rust (fun)</summary>

```rust
# use std::time::Duration;
#
# trait DurationExt {
#     fn secs(self) -> Duration;
#     fn mins(self) -> Duration;
# }
#
# trait HumanDate {
#     fn readable(&self) -> String;
# }
#
# impl DurationExt for u64 {
#     fn secs(self) -> Duration { Duration::new(self, 0) }
#     fn mins(self) -> Duration { Duration::new(self * 60, 0) }
# }
#
# impl HumanDate for Duration {
#     fn readable(&self) -> String {
#         let mut buffer = String::with_capacity(256);
#         let total_seconds = self.as_secs();
#         let minutes = total_seconds / 60;
#         let seconds = total_seconds % 60;
#
#         format!("{} minutes {} seconds", minutes, seconds)
#     }
# }
#
fn main() {
    let duration = 45.secs() + 37.secs() + 2.mins();
    println!("{}", duration.readable());
}
```
</details>
