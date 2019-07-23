---
title: Effects of Buffering
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: 23e241794455a92f9e3628a786d75a6d4c7b037e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376317"
---
# <a name="effects-of-buffering"></a>Effects of Buffering

Poniższy przykład pokazuje efekty buforowania. Może się spodziewać, że program `please wait`drukuje, odczeka 5 sekund, a następnie kontynuował. Nie będzie koniecznie działać w ten sposób, ponieważ dane wyjściowe są buforowane.

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

Aby program działał logicznie, `cout` obiekt musi być pusty, gdy zostanie wyświetlony komunikat. Aby opróżnić `ostream` obiekt, wyślij go do `flush` Manipulator:

```cpp
cout <<"Please wait..." <<flush;
```

Ten krok opróżnia bufor, upewniając się, że wiadomość jest drukowana przed oczekiwaniem. Można również użyć `endl` manipulator, która opróżnia bufor i wyprowadza znak wysuwu wiersza, lub `cin` użyć obiektu. Ten obiekt (z `cerr` obiektami lub `clog` ) `cout` jest zwykle powiązany z obiektem. W `cin` takim przypadku użycie (lub `cerr` obiektów lub `clog` ) opróżnia `cout` obiekt.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
