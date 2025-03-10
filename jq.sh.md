#command

**`jq`** (JSON Query) is a **command-line JSON processor** for Linux, used to parse, filter, manipulate, and format JSON data. .
```sh
sudo pacman -S jq
sudo apt install jq
sudo yum install jq
brew install jq
```
---
### **Basic Usage Examples**
```sh
# format json
echo '{"name": "Alice", "age": 25}' | jq

#output
{
  "name": "Alice",
  "age": 25
}
```

```sh
# Find value from name
echo '{"name": "Alice", "age": 25}' | jq '.name'

#output
"Alice"
```

```sh
#Filter an array
echo '[{"name": "Alice"}, {"name": "Bob"}]' | jq '.[].name'
#output
"Alice"
"Bob"
```
```sh
# Count Elements in an array
echo '[1,2,3,4,5]' | jq 'length'

#output
5
```
#### **5️⃣ Select Objects with a Condition**

```sh
# Select with a condition
echo '[{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]' | jq '.[] | select(.age > 25)'

#output
{
  "name": "Bob",
  "age": 30
}
```


```sh
# Add new key-value
echo '{"name": "Alice"}' | jq '. + {"age": 25}'

#output
{
  "name": "Alice",
  "age": 25
}
```
---