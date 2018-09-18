---
title: Definicje i deklaracje C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fcb83395313609fc5c9bad673416131b2332552
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019565"
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