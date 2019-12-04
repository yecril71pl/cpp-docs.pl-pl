---
title: Błąd kompilatora C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755645"
---
# <a name="compiler-error-c3533"></a>Błąd kompilatora C3533

"Type": parametr nie może mieć typu zawierającego element "Auto"

Nie można zadeklarować metody lub parametru szablonu za pomocą słowa kluczowego `auto`, jeśli domyślna opcja [/Zc:](../../build/reference/zc-auto-deduce-variable-type.md) autokompilatora jest włączona.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Usuń słowo kluczowe `auto` z deklaracji parametru.

## <a name="example"></a>Przykład

Poniższy przykład daje C3533, ponieważ deklaruje parametr funkcji ze słowem kluczowym `auto` i jest kompilowany za pomocą **/Zc:** Auto.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3533 w trybie C++ 14, ponieważ deklaruje parametr szablonu ze słowem kluczowym `auto` i jest kompilowany z **/Zc:** Auto. (W języku C++ 17 jest to poprawna definicja szablonu klasy z pojedynczym parametrem szablonu bez typu, którego typ jest wywnioskowany).

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)
