+++
date = '2026-05-19T22:41:13+05:30'
title = 'Bencode'
description = 'Bencode is a form of encoding technique used by BitTorrent algorith to store data in .torrent file'
+++

This is a way of serializing the data or representing data in torrent, ex; we use JSON while dealing with APIs, and BSON while dealing with mongodb.

why torrent chose bencoding over json:

- json does not support binary format
- bloated
- mixed/varying key:value pairs

These above following drawbacks made the creators of torrent to chose bencoding over JSON in 2001, Bencoding is simple, deterministic, supports binary and extremely simple.

Bencoding supports **ONLY 4** datatypes:

| datatype   | representation        | example                  | intrepretation                                        |
| ---------- | --------------------- | ------------------------ | ----------------------------------------------------- |
| Integer    | `i<number>e`          | `i-45e`, `i0e`, `i99e`   | 45, 0, 99                                             |
| String     | `length:string`       | `5:hello`, `0:`, `3:foo` | "hello", "", "foo"                                    |
| List       | `l<item1><item2>...e` | `li32e5:hello3:bye`      | `[32, "hello","bye"]`                                 |
| Dictionary | `d<key><value>...e`   | `d3:key4:valuee`         | `{"key":"value"}`<br>lexicographically sorted by keys |

**Bencoding is recursive in nature**, which means we can nest `list` inside `dictionary` and vice versa infinitely. ex:

```text
d
  4:name
  8:file.txt
  6:length
  i123e
  5:files
  l
    d3:foo3:bare
  e
e

// actual structure:
{
	"name"   : "file.txt",
	"length" : 123,
	"files"  : [{"foo" : "bar"}]
}
```
