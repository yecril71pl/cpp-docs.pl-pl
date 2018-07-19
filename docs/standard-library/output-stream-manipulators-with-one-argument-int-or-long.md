---
title: Stream manipulatory wyjściowych z jednym argumentem (int lub long) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f569b064d2ee5de5bd1aa39c9d443c8a49ca2677
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961854"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulatory strumieni wyjściowych z jednym argumentem (int lub long)

Iostream — Biblioteka klas zawiera zbiór makra do tworzenia manipulatory sparametryzowanych. Manipulatory za pomocą jednego **int** lub **długie** argument jest przypadkiem szczególnym. Do utworzenia manipulator strumienia wyjściowego, który akceptuje pojedynczy **int** lub **długie** argumentu (takich jak `setw`), należy użyć makro _Smanip, która jest zdefiniowana w \<iomanip >. Ten przykład definiuje `fillblank` manipulator, który wstawia określoną liczbę wartości pustych w strumieniu:

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

## <a name="see-also"></a>Zobacz także

[Niestandardowe manipulatory z argumentami](../standard-library/custom-manipulators-with-arguments.md)<br/>
