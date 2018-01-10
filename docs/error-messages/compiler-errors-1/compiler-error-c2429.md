---
title: "C2429 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2429
dev_langs: C++
helpviewer_keywords: C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6882804d1ddf2e4f83947e310cde4c8c114120d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2429"></a>C2429 błąd kompilatora

> "*funkcji języka*"wymaga flagi kompilatora"*— opcja kompilatora*"

Funkcja języka wymaga opcji kompilatora określonych dla pomocy technicznej.

Błąd **C2429: funkcja języka "zagnieżdżone namespace-definition" wymaga flagi kompilatora "/ std:c ++ 17'** jest generowany, gdy użytkownik próbuje określić *złożone przestrzeni nazw*, przestrzeni nazw, która zawiera jeden lub więcej nazwy zagnieżdżone w zakresie przestrzeni nazw w programie Visual Studio 2015 Update 5. (W programie Visual Studio 2017 wersji 15 ustęp 3, **/std:c ++ najnowsze** przełącznika jest wymagane.) Złożone przestrzeni nazw, definicje nie są dozwolone w języku C++ przed C ++ 17. Kompilator obsługuje definicje złożone przestrzeń nazw podczas [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) określono opcję kompilatora:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
