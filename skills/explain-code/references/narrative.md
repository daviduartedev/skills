# Narrative

Print these headings in this order.

## Call path

Who calls whom for the named module, from the public entry to the store. Cite `path:line`.

## Seams

The public interface a test or another module should hit.

## What the tests lock

Each relevant test named and mapped to a behaviour. Untested behaviour is stated as untested.

## Mismatch with product docs

Only when a named product source disagrees with the code. Otherwise one line that they agree, or that no product source was found.
