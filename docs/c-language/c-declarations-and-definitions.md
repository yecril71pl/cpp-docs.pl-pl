---
title: Deklaracje i definicje języka C
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: 3be9cd72e9f4dbad4d279cc1bb65dfb92a61cd42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326056"
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

## <a name="see-also"></a>Zobacz także

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)
