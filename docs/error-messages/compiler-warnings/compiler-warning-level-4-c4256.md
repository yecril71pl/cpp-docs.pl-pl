---
title: Kompilator ostrzeżenie (poziom 4) C4256 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4256
dev_langs:
- C++
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6112a541f4bc7efc0ab36feb14f285cf132b08e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075371"
---
# <a name="compiler-warning-level-4-c4256"></a>Kompilator ostrzeżenie (poziom 4) C4256

'Funkcja': konstruktor dla klasy z bazami wirtualnymi ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami programu Visual C++

Możliwa niezgodność.

Rozważmy następujący przykład kodu. Jeśli definicja Konstruktor S2::S2 (int i...) został skompilowany przy użyciu wersji kompilatora Visual C++ przed wersją 7, ale poniższy przykład jest kompilowany przy użyciu bieżącej wersji, wywołanie konstruktora S3 nie będzie działać poprawnie z powodu szczególny zmiana Konwencja wywoływania. Jeśli oba zostały skompilowane przy użyciu Visual C++ 6.0, połączenie nie będzie działać końca albo, chyba, że nie parametry zostały przekazane do wielokropka.

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