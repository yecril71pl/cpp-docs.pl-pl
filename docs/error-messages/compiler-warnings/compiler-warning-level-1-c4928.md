---
title: Kompilator ostrzeżenie (poziom 1) C4928
ms.date: 11/04/2016
f1_keywords:
- C4928
helpviewer_keywords:
- C4928
ms.assetid: 77235d7f-9360-45cb-8348-d148c605c4a3
ms.openlocfilehash: 9357e5775e6cfc9a44c43104c4ffd3fd34084e51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526483"
---
# <a name="compiler-warning-level-1-c4928"></a>Kompilator ostrzeżenie (poziom 1) C4928

nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika

Znaleziono więcej niż jeden procedury konwersji zdefiniowanej przez użytkownika. Kompilator wykonać kod w wszystkich tych procedur.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4928:

```
// C4928.cpp
// compile with: /W1
#pragma warning(default: 4928)

struct I
{
};

struct I1 : I
{
};

struct I2 : I
{
};

template <class T>
struct Ptr
{
   operator T*()
   {
      return 0;
   }

   Ptr()
   {
   }

   Ptr(I*)
   {
   }
};

int main()
{
   Ptr<I1> p1;
   Ptr<I2> p2 = p1;   // C4928
   // try one of the following two lines to resolve this error
   // Ptr<I2> p2(p1);
   // Ptr<I2> p2 = (I1*) p1;
}
```