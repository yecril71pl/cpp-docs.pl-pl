---
title: Kompilator ostrzeżenie (poziom 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3e8a3ab1b11c719730016e6a0cd248770cd89af8
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447776"
---
# <a name="compiler-warning-level-4-c4256"></a>Kompilator ostrzeżenie (poziom 4) C4256

'Funkcja': konstruktor dla klasy z bazami wirtualnymi ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami programu Visual C++

Możliwa niezgodność.

Rozważmy następujący przykład kodu. Jeśli definicja Konstruktor S2::S2 (int i...) został skompilowany przy użyciu wersji Microsoft C++ kompilatora przed w wersji 7, ale poniższy przykład jest kompilowany przy użyciu bieżącej wersji, wywołanie konstruktora S3 nie będzie działać poprawnie ze względu na zmiany Konwencja wywoływania szczególny. Jeśli oba zostały skompilowane przy użyciu Visual C++ 6.0, połączenie nie będzie działać końca albo, chyba, że nie parametry zostały przekazane do wielokropka.

Aby rozwiązać tego ostrzeżenia

1. Nie używaj wielokropek w konstruktorze.

1. Upewnij się, że wszystkie składniki we własnym projekcie są tworzone za pomocą bieżącej wersji (w tym wszystkie biblioteki, które może zdefiniować lub odwołaj się do tej klasy), a następnie wyłączone używanie ostrzeżenie [ostrzeżenie](../../preprocessor/warning.md) pragmy.

Poniższy przykład spowoduje wygenerowanie C4256:

```
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