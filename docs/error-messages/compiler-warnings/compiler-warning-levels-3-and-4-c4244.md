---
title: Kompilator ostrzeżenie (poziomy 3 i 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: af06dbf5bb4a1dd133c277d63c40da2a8a54770b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359933"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Kompilator ostrzeżenie (poziomy 3 i 4) C4244

'conversion' konwersja z 'Typ1' na 'Typ2', możliwa utrata danych

Typ liczby całkowitej jest konwertowany na mniejszy typ liczby całkowitej. Jeśli jest to ostrzeżenie poziom 4 *type1* jest `int` i *type2* jest mniejszy niż `int`. W przeciwnym razie jest to poziom 3 (przypisane wartości typu [__int64](../../cpp/int8-int16-int32-int64.md) do zmiennej typu `unsigned int`). Może wystąpić możliwa utrata danych.

Jeśli C4244, powinny albo zmienić program, aby używać zgodnych typów lub dodać logikę do kodu, aby upewnić się, że zakres możliwych wartości zawsze będzie zgodny z typami, którego używasz.

C4244 można również wyzwalać na poziomie 2; zobacz [ostrzeżenie kompilatora (poziom 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) Aby uzyskać więcej informacji.

Konwersja może być problem z powodu konwersji niejawnych.

Poniższy przykład spowoduje wygenerowanie C4244:

```
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

Aby uzyskać więcej informacji, zobacz [zwykle konwersje arytmetyczne](../../c-language/usual-arithmetic-conversions.md).

```
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

Ostrzeżenie C4244 może wystąpić, gdy tworzenie kod dla 64-bitowym, który nie generuje ostrzeżenia podczas kompilowania dla celów 32-bitowych. Na przykład różnica między wskaźników jest ilość 32-bitowego na platformach 32-bitowych, ale ilość 64-bitowego na platformach 64-bitowych.

Poniższy przykład spowoduje wygenerowanie C4244 podczas kompilowania dla celów 64-bitowych:

```
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```