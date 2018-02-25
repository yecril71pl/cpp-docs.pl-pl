---
title: Efekty buforowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 460bc234ed438a92328d49c3821079bfb688da21
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="effects-of-buffering"></a>Effects of Buffering
W poniższym przykładzie przedstawiono efekty buforowania. Może spodziewać się być `please wait`, Zaczekaj 5 sekund, a następnie kontynuuj. Nie zawsze działa on w ten sposób, ponieważ dane wyjściowe są buforowane.  
  
```  
// effects_buffering.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <time.h>  
using namespace std;  
  
int main( )  
{  
   time_t tm = time( NULL ) + 5;  
   cout << "Please wait...";  
   while ( time( NULL ) < tm )  
      ;  
   cout << "\nAll done" << endl;  
}  
```  
  
 Aby program działa logicznie, `cout` obiektu musi się pustej, gdy komunikat jest wyświetlany. Aby opróżnić `ostream` obiektów, wysłać `flush` manipulatora:  
  
```  
cout <<"Please wait..." <<flush;  
```  
  
 Ten krok opróżnia bufor, zapewnienie, że komunikat wyświetla przed czas oczekiwania. Można również użyć `endl` manipulatora, które opróżnia bufor i wyprowadza wysuwu wiersza powrotu karetki, lub można użyć `cin` obiektu. Ten obiekt (z `cerr` lub `clog` obiektów) jest zwykle powiązane `cout` obiektu. W związku z tym jakimkolwiek użyciem `cin` (lub `cerr` lub `clog` obiektów) opróżnia `cout` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)

