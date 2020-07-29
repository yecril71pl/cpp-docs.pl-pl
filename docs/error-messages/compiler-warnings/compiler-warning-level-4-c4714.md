---
title: Ostrzeżenie kompilatora (poziom 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 286a9e6e12643d3dadd070e7c4cf4b2dd350c02c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219862"
---
# <a name="compiler-warning-level-4-c4714"></a>Ostrzeżenie kompilatora (poziom 4) C4714

> Funkcja "Function" oznaczona jako __forceinline nie została wbudowana

Dana funkcja została wybrana do rozwijania wbudowanego, ale kompilator nie przeprowadził tworzenia konspektu.

Chociaż **`__forceinline`** jest to silniejszy wskaźnik do kompilatora niż **`__inline`** , jest nadal wykonywane na podstawie uznania kompilatora, ale nie są używane żadne algorytmy heurystyczne w celu określenia korzyści ze stosowania tej funkcji.

W niektórych przypadkach kompilator nie będzie wbudowanej określonej funkcji dla powodów mechanicznych. Na przykład kompilator nie będzie wbudowany:

- Funkcja, jeśli spowoduje to mieszanie zarówno SEH, jak i C++ EH.

- Niektóre funkcje z funkcją Kopiuj skonstruowane obiekty przekazaną przez wartość, gdy-GX/zdrowie/EHa jest włączona.

- Funkcje zwracają obiekt niebędący w trybie wiatru przez wartość, gdy-GX/zdrowie/EHa jest włączona.

- Funkcje z wbudowanym zestawem podczas kompilowania bez-Og/Ox-/O1/O2.

- Działa z listą argumentów zmiennych.

- Funkcja z **`try`** instrukcją (obsługa wyjątków C++).

Poniższy przykład generuje C4714:

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
