---
title: Błąd kompilatora C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 6b487c0f94a00ec64e0c2178265c5a8c27544a51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761559"
---
# <a name="compiler-error-c3535"></a>Błąd kompilatora C3535

nie można wywnioskować typu dla elementu "type1" z elementu "type2"

Nie można wywnioskować typu zmiennej zadeklarowanej za pomocą słowa kluczowego `auto` na podstawie typu wyrażenia inicjującego. Na przykład ten błąd występuje, gdy wyrażenie inicjacji szacuje się na `void`, który nie jest typem.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że typ wyrażenia inicjowania nie jest `void`.

1. Upewnij się, że deklaracja nie jest wskaźnikiem do typu podstawowego. Aby uzyskać więcej informacji, zobacz [podstawowe typy](../../cpp/fundamental-types-cpp.md).

1. Upewnij się, że jeśli deklaracja jest wskaźnikiem do typu, wyrażenie inicjacji jest typem wskaźnika.

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ wyrażenie inicjacji szacuje się `void`.

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ instrukcja deklaruje zmienną `x` jako wskaźnik do typu wywnioskowanego, ale typ wyrażenia inicjatora jest podwójny. W związku z tym kompilator nie może wywnioskować typu zmiennej.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ zmienna `p` deklaruje wskaźnik do typu wywnioskowanego, ale wyrażenie inicjacji nie jest typem wskaźnika.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[Typy podstawowe](../../cpp/fundamental-types-cpp.md)
