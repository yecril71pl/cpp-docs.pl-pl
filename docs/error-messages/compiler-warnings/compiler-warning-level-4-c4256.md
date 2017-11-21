---
title: "Kompilatora (poziom 4) ostrzeżenie C4256 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4256
dev_langs: C++
helpviewer_keywords: C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3bb16c84a03bddad1eeb7dd5cfc6c652857d83b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4256"></a>Kompilator C4256 ostrzegawcze (poziom 4)
"Funkcja": konstruktor dla klasy z wirtualnymi typami podstawowymi ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami programu Visual C++  
  
 Możliwa niezgodność.  
  
 Rozważmy poniższy przykład kodu. Jeśli definicji konstruktora S2::S2 (int i,...) został skompilowany przy użyciu wersji kompilatora Visual C++ przed w wersji 7, ale poniższy przykład jest skompilowana przy użyciu bieżącej wersji, wywołanie konstruktora dla S3 nie będzie działać poprawnie z powodu Zmiana Konwencja wywoływania przypadków specjalnych. Jeśli oba zostały skompilowane przy użyciu programu Visual C++ 6.0, połączenie nie będzie działało końca albo, chyba że żadne parametry zostały przekazane do wielokropka.  
  
 Aby naprawić tego ostrzeżenia  
  
1.  Nie używaj wielokropka w konstruktorze.  
  
2.  Upewnij się, że wszystkie składniki w ich projektu są wbudowane w bieżącej wersji (w tym żadnych bibliotek, które mogą zdefiniować lub odwołać się do tej klasy), a następnie wyłączyć za pomocą ostrzeżenie [ostrzeżenie](../../preprocessor/warning.md) pragma.  
  
 Poniższy przykład generuje C4256:  
  
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