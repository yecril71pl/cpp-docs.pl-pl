---
title: Ostrzeżenie kompilatora (poziom 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 8ea4212eaddf14546827728b31299063021a959f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989639"
---
# <a name="compiler-warning-level-4-c4714"></a>Ostrzeżenie kompilatora (poziom 4) C4714

Funkcja "Function" oznaczona jako __forceinline nie została wbudowana

Dana funkcja została wybrana do rozwijania wbudowanego, ale kompilator nie przeprowadził tworzenia konspektu.

Chociaż `__forceinline` jest silniejszym wskazaniem kompilatora niż `__inline`, funkcja tworzenia konspektu jest nadal wykonywana na podstawie uznania kompilatora, ale nie są używane żadne algorytmy heurystyczne w celu określenia korzyści ze stosowania tej funkcji.

W niektórych przypadkach kompilator nie będzie wbudowanej określonej funkcji dla powodów mechanicznych. Na przykład kompilator nie będzie wbudowany:

- Funkcja, jeśli spowoduje to mieszanie zarówno SEH, jak i C++ EH.

- Niektóre funkcje z funkcją Kopiuj skonstruowane obiekty przekazaną przez wartość, gdy-GX/zdrowie/EHa jest włączona.

- Funkcje zwracają obiekt niebędący w trybie wiatru przez wartość, gdy-GX/zdrowie/EHa jest włączona.

- Funkcje z wbudowanym zestawem podczas kompilowania bez-Og/Ox-/O1/O2.

- Działa z listą argumentów zmiennych.

- Funkcja z instrukcją **try** (C++ obsługa wyjątków).

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
