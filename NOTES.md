Notes
=====

DNS Check
---------
The DNS check is done via host and not via nslookup, because [the latter is said to be deprecated](http://en.wikipedia.org/wiki/Nslookup).
The nslookup line is `nslookup -querytype=A $1.wiktionary.org - $dnsServer >> /dev/null`.

Wikimedia API return format
---------------------------
The possible values for format are: json, jsonfm, php, phpfm, wddx, wddxfm, xml, xmlfm, yaml, yamlfm, rawfm, txt, txtfm, dbg, dbgfm, dump, dumpfm, none.

The last one outputs nothing, so here is the encoding difference for all the others:

- json, jsonfm, yaml, yamlfm, rawfm use unicodebig encoding
- xml, xmlfm, php, phpfm, wddx, wddxfm, txt, txtfm, dbg, dbgfm, dump, dumpfm use utf-8 encoding

Since this is a CLI script, UTF-8 is way more suitable. So it's not possible to use json or yaml (which produce the exact same output btw).
In the end, the more handy format is txt.
