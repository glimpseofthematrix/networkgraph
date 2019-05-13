# A Glimpse of the Matrix: Measurement Data #
An anonymized snapshot of the network structure of the Matrix network from 2018-07-25.
We used the [petgraph](https://crates.io/crates/petgraph) library for creating and analyzing this graph,
which is why the graph is in a json format native to the library's data structure.

*TODO: Convert to well-known formats*

## How to parse the format in Rust ##
Minimal [Rust](https://www.rust-lang.org/) example using [serde_json](https://crates.io/crates/serde_json)
and [petgraph](https://crates.io/crates/petgraph):

```rust
use std::path::Path;
use std::fs;
use std::io;

pub fn read_graph<P: AsRef<Path>>(path: P) -> Result<petgraph::Graph<Node, (), petgraph::Undirected>, serde_json::Error> {
    let file = fs::File::open(path).unwrap();
    let reader = io::BufReader::new(file);
    serde_json::from_reader(reader)
}
```

## Format Example ##
A small example graph pretty-printed would look like this:

```json
{
   "edge_property" : "undirected",
   "edges" : [
      [ 0, 5, null ],
      [ 1, 6, null ],
      [ 2, 7, null ],
      [ 3, 7, null ],
      [ 4, 8, null ],
      [ 0, 9, null ],
      [ 5, 9, null ],
      [ 1, 9, null ],
      [ 6, 9, null ],
      [ 0, 10, null ],
      [ 5, 10, null ],
      [ 1, 10, null ],
      [ 6, 10, null ],
      [ 2, 10, null ],
      [ 3, 10, null ],
      [ 7, 10, null ],
      [ 4, 10, null ],
      [ 8, 10, null ],
      [ 2, 11, null ],
      [ 3, 11, null ],
      [ 7, 11, null ]
   ],
   "node_holes" : [],
   "nodes" : [
      { "id" : 0, "kind" : "User" },
      { "id" : 1, "kind" : "User" },
      { "id" : 2, "kind" : "User" },
      { "id" : 3, "kind" : "User" },
      { "id" : 4, "kind" : "User" },
      { "id" : 5, "kind" : "Server" },
      { "id" : 6, "kind" : "Server" },
      { "id" : 7, "kind" : "Server" },
      { "id" : 8, "kind" : "Server" },
      { "id" : 9, "kind" : "Room" },
      { "id" : 10, "kind" : "Room" },
      { "id" : 11, "kind" : "Room" }
   ]
}
```

## License ##
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
