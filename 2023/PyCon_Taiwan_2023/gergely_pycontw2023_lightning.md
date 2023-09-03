---
theme: moon
---

# To Improve Your Python, Learn Rust

a very promising partnership

---

# ... Rust?

note: I know it's PyCon not RustCon, but... How man people used Rust here?

---
### You might be already using it!

[ruff](https://beta.ruff.rs/docs/): *black* but faster

[Pydantic](https://docs.pydantic.dev/latest/) 2.0: *Pydantic* but faster

[polars](about:blank): *Pandas* but faster

[tiktoken](https://github.com/openai/tiktoken): tokenizer for OpenAI models

...

note: these are the usual suspects, but there are a lot more

---

### Complementary skillset

two languages that complement each other

|          Python       |     |       Rust          |
| :---------------: | --- | :---------------: |
| Fast to develop | <-> | Fast to run     |
| Flexible        | <-> | Robust          |
| Large ecosystem | <-> | Small artefacts |
|                 |     |                 |

note: why do these projects above use Rust within?

---

### Getting started

generate a project skeleton with `maturin`

```shell
$ maturin new --mixed --bindings pyo3 something
```
↓
```shell
$ tree something

something
├── Cargo.toml
├── pyproject.toml
├── python
│   └── something
│       └── __init__.py
└── src
    └── lib.rs
```

note: how a brand new start would look like? create a project with maturin, where you have access both to Rust and Python. If it looks strange, it will become natural soon; cargo + maturin

---

#### Rust view
```rust
use pyo3::prelude::*;

#[pyfunction]
fn sum_as_string(a: usize, b: usize) -> PyResult<String> {
	Ok((a + b).to_string())
}

#[pymodule]
fn something(_py: Python, m: &PyModule) -> PyResult<()> {
  m.add_function(wrap_pyfunction!(sum_as_string, m)?)?;
  Ok(())
}
```
#### Python view
```python
from something import sum_as_string

print(sum_as_string(2, 2))
# 4
```

note: a very dummy example but shows the basic building blocks: functions, types, module export... now make it more more useful!

---

### Now do something more complex 🚀

Performance-sensitive task...

Concurrent tasks...

Memory pressured tasks...

Systems programming...

Image processing...

💭

note: and this is just scratching the surface

---

## Learn good practices from Rust

Make documentation a first class feature

Put more thought into error handling

User iterators & generators; pattern matching

Prefer immutable variables

... _[your insights here]_ ...

note: don't have to just use Rust code, can take some of the mindset as well

---

![Friendship|700](https://geekgirlpenpals.com/wp-content/uploads/2018/11/90sCasablanca.gif)

[maturin.rs](https://www.maturin.rs/ )

note: the world is different in the two sides but compatible. Start at maturin and dig in from there.