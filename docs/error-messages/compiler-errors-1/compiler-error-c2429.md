---
title: Błąd kompilatora C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: a5d1e98e91c541729a93f731eede9b047589c63a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447981"
---
# <a name="compiler-error-c2429"></a>Błąd kompilatora C2429

> "*funkcja językowa*"wymaga flagi kompilatora"*— opcja kompilatora*"

Funkcja języka wymaga określonych kompilator pomocy technicznej.

Błąd **C2429: funkcji języka "zagnieżdżone namespace-definition" wymaga flagi kompilatora "/ STD: c ++ 17"** jest generowany, jeśli zostanie podjęta próba zdefiniować *złożone przestrzeni nazw*, obszar nazw, który zawiera jeden lub więcej nazwy zagnieżdżonej zakresu przestrzeni nazw, począwszy od programu Visual Studio 2015 Update 5. (W programie Visual Studio 2017 w wersji 15.3, **/STD: c ++ najnowsze** przełącznika jest wymagane.) Złożone przestrzeni nazw, których definicje nie są dozwolone w języku C++ przed C ++ 17. Definicje nazw złożonego obsługiwanych przez kompilator podczas [/STD: c ++ 17](../../build/reference/std-specify-language-standard-version.md) określono opcję kompilatora:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
