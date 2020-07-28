---
title: Ostrzeżenie kompilatora (poziomy 3 i 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: cadba931af9c4497ec78938c37f94fe13daab0af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214324"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Ostrzeżenie kompilatora (poziomy 3 i 4) C4244

Konwersja "konwersji" z "type1" na "type2", możliwa utrata danych

Typ Integer jest konwertowany na mniejszy typ Integer. Jest to ostrzeżenie poziomu 4, jeśli *Type1* jest **`int`** i *Type2* jest mniejsze niż **`int`** . W przeciwnym razie jest to poziom 3 (przypisana wartość typu [__int64](../../cpp/int8-int16-int32-int64.md) do zmiennej typu **`unsigned int`** ). Mogła wystąpić utrata danych.

W przypadku uzyskania C4244 należy zmienić program tak, aby korzystał z zgodnych typów, lub dodać do kodu logikę, aby upewnić się, że zakres możliwych wartości będzie zawsze zgodny z typami, z których korzystasz.

C4244 może również wyzwalać na poziomie 2; Aby uzyskać więcej informacji, zobacz [Ostrzeżenie kompilatora (poziom 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) .

Konwersja może mieć problem z powodu niejawnych konwersji.

Poniższy przykład generuje C4244:

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

Aby uzyskać więcej informacji, zobacz [typowe konwersje arytmetyczne](../../c-language/usual-arithmetic-conversions.md).

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

Ostrzeżenie C4244 może wystąpić podczas kompilowania kodu dla 64-bitowych elementów docelowych, które nie generują ostrzeżenia podczas kompilowania dla elementów docelowych 32-bitowych. Na przykład różnica między wskaźnikami jest 32-bitową ilością na platformach 32-bitowych, ale z 64-bitową ilością na platformach 64-bitowych.

Poniższy przykład generuje C4244 podczas kompilowania dla elementów docelowych 64-bitowych:

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
