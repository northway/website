---
icon: lucide/shredder

tags:
  - linux
  - shred
---

# Shred

Overwrite the specified FILE(s) repeatedly, in order to make it harder for even very expensive hardware probing to recover the data.

https://linux.die.net/man/1/shred

## Fill up a file with zeros

```bash
shred -zv file
```

## Fill a file up with zeros then delete it

```bash
shred -zvu file
```

## Recurisve shred

```bash
find <directory> -depth -type f -exec shred -v -z {} \;

find <directory> -depth -type f -exec shred -v -z -u {} \;
```

## After shredding

```bash
sync
```
