# How to remove accents from String

```
const str = "Crème Brulée";
const result = str.normalize("NFD").replace(/[\u0300-\u036f]/g, "");

console.log(result);
// "Creme Brulee"
```

Two things are happening here:

1. `normalize("NFD")` decomposes combined graphemes into the combination of simple ones. E.g. The è of Crème ends up expressed as e +  ̀.
2. Using a regex character class to match the U+0300 → U+036F range, it is now trivial to globally get rid of the diacritics, which the Unicode standard conveniently groups as the Combining Diacritical Marks Unicode block.
