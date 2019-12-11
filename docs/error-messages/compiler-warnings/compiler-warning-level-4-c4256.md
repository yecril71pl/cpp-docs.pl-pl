---
title: Ostrzeżenie kompilatora (poziom 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 1ec3e64548cead53cea906cdf2abd3dd25ee06d4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991385"
---
# <a name="compiler-warning-level-4-c4256"></a>Ostrzeżenie kompilatora (poziom 4) C4256

"Function": Konstruktor dla klasy z wirtualnymi bazami ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami wizualizacjiC++

Możliwa niezgodność.

Spójrz na poniższy przykład kodu. Jeśli definicja konstruktora S2:: S2 (int i,...) została skompilowana przy użyciu wersji kompilatora firmy Microsoft C++ , która jest wcześniejsza niż wersja 7, ale Poniższy przykład jest kompilowany przy użyciu bieżącej wersji, wywołanie konstruktora dla S3 nie działa poprawnie ze względu na szczególną zmianę w konwencji wywoływania przypadku. Jeśli obie zostały skompilowane przy użyciu C++ języka Visual 6,0, wywołanie nie będzie działało całkowicie po prawej stronie, chyba że żadne parametry nie zostały przesłane dla wielokropka.

Aby usunąć to ostrzeżenie,

1. Nie używaj wielokropka w konstruktorze.

1. Upewnij się, że wszystkie składniki w projekcie zostały skompilowane przy użyciu bieżącej wersji (łącznie z bibliotekami, które mogą definiować lub odwoływać się do tej klasy), a następnie Wyłącz ostrzeżenie przy użyciu dyrektywy pragma [ostrzeżenia](../../preprocessor/warning.md) .

Poniższy przykład generuje C4256:

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```
