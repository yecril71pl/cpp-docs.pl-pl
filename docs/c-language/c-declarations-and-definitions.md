---
title: C deklaracje i definicje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 526a7bb902374fb3df936d5ac81cf602e1871a4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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