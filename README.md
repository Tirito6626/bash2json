# bash2json
The most bash-based JSON parser

![logo](https://repo.tirito.de/assets/images/bash2json_banner.jpg)

* Only uses awk, sed and builtins
* JSON validation
* Associative/indexed arrays to JSON and vice versa
* Pipes support
* Single executable

## Usage examples:
Getting "world": 
```bash
./bash2json --query '{ "hello": "world" }' 'hello'
"world"
``` 

Getting "good":
```bash
root@bash2json: ./bash2json --query '{ "hello": { "world": "good" } }' 'hello.world'
"good"
``` 

Removing double quotes:

```bash
root@bash2json: ./bash2json --query -r '{ "hello": { "world": "good" } }' 'hello.world'
good
``` 

Appending root JSON:

```bash
root@bash2json: ./bash2json --append '{ "hello": "world" }' '' 'goodbye' 'world'
{"hello":"world","goodbye":"world"}
``` 

Appending 'hello' object:

```bash
root@bash2json: ./bash2json --append '{ "hello": { "world": "good" } }' 'hello' 'goodbye' 'world'
{"hello":{"world":"good","goodbye":"world"}}
``` 

Converting JSON into associative array:
```bash
root@bash2json: ./bash2json --from-json '{ "hello": { "world": "good", "goodbye": "world" } }'
array_24740 # output array name to create array with and add items to it
array_24740[hello.world]="good"
array_24740[hello.goodbye]="world"
``` 
