---
title: Manipulatory strumieni wyjściowych z jednym argumentem (int lub long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e093512af2741329c58db0b613453f3388bacdf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370804"
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
