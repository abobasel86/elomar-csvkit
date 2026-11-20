# csvkit

Read and write CSV (RFC 4180): quoted fields, quotes and line breaks inside fields, other separators, and rows as maps.

قراءة ملفات CSV وكتابتها (RFC 4180): الحقول بين علامات تنصيص، وعلامات التنصيص وفواصل الأسطر داخل الحقول، وفواصل أخرى، والصفوف كقواميس.

Requires Elomar-Lang 0.2.0 or later.

## Install

```text
elomar add csvkit
```

or in `elomar.toml`:

```toml
[dependencies]
csvkit = "0.1"
```

## Use

```elomar
use csvkit.csv

fn main() {
    match csv.records("name,city\nLina,Amman\nOmar,Cairo\n") {
        Ok(rows) => {
            for row in rows {
                print("{row["name"]} lives in {row["city"]}")
            }
        }
        Err(e) => print("bad CSV: {e}")
    }
    print(csv.stringify([["id", "note"], ["1", "with, comma"]]))
}
```

| Function (`csv.…`) | |
|---|---|
| `parse(text) -> Result<List<List<String>>, String>` | rows of fields |
| `parse_with(text, separator)` | the same with `;`, `\t` or another separator |
| `records(text) -> Result<List<Map<String, String>>, String>` | rows as maps keyed by the header row |
| `stringify(rows) -> String` | CSV text, quoting fields that need it (lines end with `\r\n`) |
| `stringify_with(rows, separator) -> String` | the same with another separator |
| `quote(field, separator) -> String` | one field as CSV |

## بالعربية

ثبّت الحزمة بالأمر `elomar add csvkit`، ثم استوردها بـ `use csvkit.csv`. الأمثلة
والدوال أعلاه تعمل كما هي، والحزمة تحتاج Elomar-Lang 0.2.0 أو أحدث.

## Development

```text
elomar test
elomar fmt --check .
```

## License

MIT or Apache-2.0, at your option.
