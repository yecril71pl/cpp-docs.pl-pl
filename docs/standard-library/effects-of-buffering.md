---
title: Effects of Buffering
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: e10b28edffdfe3411f86c031bfd12ea886410e20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631442"
---
# <a name="effects-of-buffering"></a>Effects of Buffering

Efekty buforowania można znaleźć w poniższym przykładzie. Można by oczekiwać program, aby wydrukować `please wait`poczekaj 5 sekund, a następnie przejść. Jej będzie działać w ten sposób, ponieważ dane wyjściowe są buforowane.

```cpp
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

Zapewnienie pracę logicznie programu `cout` obiektu musi pustej sam, gdy komunikat jest wyświetlany. Aby opróżnić `ostream` obiektu, wysłać `flush` manipulator:

```cpp
cout <<"Please wait..." <<flush;
```

W tym kroku opróżnia bufor, zapewnienie, że komunikat wyświetla przed czas oczekiwania. Można również użyć `endl` manipulator, które opróżnia bufor i generuje wysuwu wiersza powrotu karetki, lub możesz użyć `cin` obiektu. Ten obiekt (przy użyciu `cerr` lub `clog` obiektów) są zazwyczaj powiązane `cout` obiektu. Dlatego jakiekolwiek wykorzystanie `cin` (lub `cerr` lub `clog` obiektów) opróżnia `cout` obiektu.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
