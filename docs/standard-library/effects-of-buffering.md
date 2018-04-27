---
title: Efekty buforowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c387ce96d17e1db0dfefac6783dbdc87deeb94fb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="effects-of-buffering"></a>Effects of Buffering

W poniższym przykładzie przedstawiono efekty buforowania. Może spodziewać się być `please wait`, Zaczekaj 5 sekund, a następnie kontynuuj. Nie zawsze działa on w ten sposób, ponieważ dane wyjściowe są buforowane.

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

Aby program działa logicznie, `cout` obiektu musi się pustej, gdy komunikat jest wyświetlany. Aby opróżnić `ostream` obiektów, wysłać `flush` manipulatora:

```cpp
cout <<"Please wait..." <<flush;
```

Ten krok opróżnia bufor, zapewnienie, że komunikat wyświetla przed czas oczekiwania. Można również użyć `endl` manipulatora, które opróżnia bufor i wyprowadza wysuwu wiersza powrotu karetki, lub można użyć `cin` obiektu. Ten obiekt (z `cerr` lub `clog` obiektów) jest zwykle powiązane `cout` obiektu. W związku z tym jakimkolwiek użyciem `cin` (lub `cerr` lub `clog` obiektów) opróżnia `cout` obiektu.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
