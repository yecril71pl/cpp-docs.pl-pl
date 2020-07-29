---
title: Błąd kompilatora C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 18ca9f7d61d96dcc81935bd3563f57bc37da8cd7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228807"
---
# <a name="compiler-error-c3533"></a>Błąd kompilatora C3533

"Type": parametr nie może mieć typu zawierającego element "Auto"

Nie można zadeklarować metody lub parametru szablonu za pomocą **`auto`** słowa kluczowego, jeśli jest włączona domyślna opcja [/Zc:](../../build/reference/zc-auto-deduce-variable-type.md) autokompilator.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Usuń **`auto`** słowo kluczowe z deklaracji parametru.

## <a name="example"></a>Przykład

Poniższy przykład daje C3533, ponieważ deklaruje parametr funkcji ze **`auto`** słowem kluczowym i jest kompilowany za pomocą **/Zc:** Auto.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3533 w trybie C++ 14, ponieważ deklaruje parametr szablonu ze **`auto`** słowem kluczowym i jest kompilowany za pomocą **/Zc:** Auto. (W języku C++ 17 jest to poprawna definicja szablonu klasy z pojedynczym parametrem szablonu bez typu, którego typ jest wywnioskowany).

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Zobacz także

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto(wywnioskowanie typu zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)
