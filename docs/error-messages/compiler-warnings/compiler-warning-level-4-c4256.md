---
title: Kompilatora (poziom 4) ostrzeżenie C4256 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ed1a40f0da75460c4306f69da0f26eb0888bef66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297225"
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