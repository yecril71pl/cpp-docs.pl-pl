---
title: "Manipulatory strumieni wyjściowych z jednym argumentem (int lub long) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 418b9e1f982e1bb37559ee35b6953d7d3f198b61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulatory strumieni wyjściowych z jednym argumentem (int lub long)
Iostream — Biblioteka klas zapewnia zbiór makra do tworzenia manipulatory sparametryzowana. Manipulatory za pomocą jednej `int` lub `long` argumentu są szczególnych przypadkach. Aby utworzyć manipulatora strumienia wyjściowego, który akceptuje pojedynczy `int` lub `long` argumentu (takich jak `setw`), należy użyć makra _Smanip, która jest zdefiniowana w \<iomanip — >. W tym przykładzie definiuje `fillblank` manipulatora, która wstawia określoną liczbę puste wartości do strumienia:  
  
## <a name="example"></a>Przykład  
  
```cpp  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe manipulatory z argumentami](../standard-library/custom-manipulators-with-arguments.md)

