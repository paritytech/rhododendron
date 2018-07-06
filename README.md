# Rhododendron

Futures-based BFT in Rust. Mostly works, but not ready for production.

Most of the work is done with the `agree` function:
```rust
pub fn agree<C: Context, I, O>(context: C, nodes: usize, max_faulty: usize, input: I, output: O)
	-> Agreement<C, I, O>
{
    // ...
}
```

There are three parts to invoking `agree`:
  - A `Context`, encapsulating value type to be agreed upon, as well as generation, evaluation, and signatures on values.
  - An input stream of messages from other nodes.
  - An output sink of messages which will reach all other honest nodes.

This yields an `Agreement` which can be run on an event loop to completion.