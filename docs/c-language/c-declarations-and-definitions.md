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

"Deklaracja" ustanawia skojarzenie między określoną zmienną, funkcją lub typem a jej atrybutami. [Przegląd deklaracji](../c-language/overview-of-declarations.md) zawiera składnię ANSI dla `declaration` nieterminalu. Deklaracja określa również, gdzie i kiedy można uzyskać dostęp do identyfikatora ("powiązanie" identyfikatora). Zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md) , aby uzyskać informacje dotyczące powiązania.

"Definicja" zmiennej ustanawia te same skojarzenia jak Deklaracja, ale również powoduje przydzielenie magazynu dla zmiennej.

Na `main`przykład,, `find`, i `count` zmienne `var` i `val` są zdefiniowane w jednym pliku źródłowym, w następującej kolejności:

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

Zmienne `var` i `val` mogą być używane w funkcjach `find` i `count` ; dalsze deklaracje nie są zbędne. Ale te nazwy nie są widoczne (nie można uzyskać do nich `main`dostępu) w.

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)
