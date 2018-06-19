---
title: C deklaracje i definicje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c459999ab902a2498d4ffe4cc2d437a0a432b9b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381568"
---
# <a name="c-declarations-and-definitions"></a>Deklaracje i definicje języka C
"Deklaracji" ustanawia skojarzenie między konkretnej zmiennej, funkcji, lub typ i jego atrybuty. [Przegląd deklaracji](../c-language/overview-of-declarations.md) daje składnia ANSI `declaration` nonterminal. Deklaracja również określa, gdzie i kiedy identyfikator może być używane ("powiązanie" identyfikatora). Zobacz [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md) informacji o połączenie.  
  
 "definition" zmiennej ustanawia tego samego powiązania jako deklaracji, ale również powoduje magazynu do przydzielenia dla zmiennej.  
  
 Na przykład `main`, `find`, i `count` funkcje i `var` i `val` zmienne są definiowane w jeden plik źródłowy, w następującej kolejności:  
  
```  
int main() {}  
  
int var = 0;  
double val[MAXVAL];  
char find( fileptr ) {}  
int count( double f ) {}  
```  
  
 Zmienne `var` i `val` mogą być używane w `find` i `count` funkcje; są wymagane nie dalsze deklaracji. Te nazwy, ale są niewidoczne (nie można uzyskać dostępu do) `main`.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)