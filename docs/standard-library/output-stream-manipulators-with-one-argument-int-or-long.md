---
title: Manipulatory strumieni wyjściowych z jednym argumentem (int lub long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453006"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulatory strumieni wyjściowych z jednym argumentem (int lub long)

Biblioteka klas iostream zawiera zestaw makr do tworzenia sparametryzowanych manipulowania. Manipulowanie za pomocą pojedynczego argumentu **int** lub **Long** jest szczególnym przypadkiem. Aby utworzyć strumień danych wyjściowych manipulator, który akceptuje pojedynczy argument **int** lub **Long** ( `setw`na przykład), należy użyć makra _Smanip, który jest zdefiniowany w \<iomanip >. Ten przykład definiuje `fillblank` manipulator, który wstawia określoną liczbę pustych znaków do strumienia:

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

[Niestandardowe manipulatory z argumentami](../standard-library/custom-manipulators-with-arguments.md)
