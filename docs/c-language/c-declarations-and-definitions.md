---
title: Deklaracje i definicje języka C
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: d0dbd74dd54b6ee80fc1f02cf1cb07379a778be0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427966"
---
# <a name="c-declarations-and-definitions"></a>Deklaracje i definicje języka C

"Deklaracją" ustanawia skojarzenie między określonej zmiennej, funkcji, lub typu i jego atrybuty. [Przegląd deklaracji](../c-language/overview-of-declarations.md) podaje składnię ANSI dla `declaration` nieterminalnych. Deklaracja określa również, gdzie i kiedy identyfikator może być używane ("powiązanie" identyfikatora). Zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md) uzyskać informacji na temat połączeń.

Ustanawia tego samego powiązania jako deklaracja "definition" zmienną, ale również powoduje, że magazynu do przydzielenia dla zmiennej.

Na przykład `main`, `find`, i `count` funkcje i `var` i `val` zmienne są definiowane w jednym pliku źródłowym, w następującej kolejności:

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

Zmienne `var` i `val` mogą być używane w `find` i `count` funkcje; są wymagane nie dalsze deklaracji. Jednak te nazwy są niewidoczne (nie są dostępne) `main`.

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)