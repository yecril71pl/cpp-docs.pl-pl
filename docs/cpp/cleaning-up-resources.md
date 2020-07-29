---
title: Oczyszczanie zasobów
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: b172695044057f58771af0f4cfcb5ca869b36678
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229054"
---
# <a name="cleaning-up-resources"></a>Oczyszczanie zasobów

Podczas wykonywania procedury obsługi nie można wiedzieć, które zasoby są faktycznie przydzielono przed wywołaniem procedury obsługi zakończenia. Istnieje możliwość przerwania bloku instrukcji **__try** przed przydzieleniem wszystkich zasobów, dzięki czemu nie wszystkie zasoby zostały otwarte.

W związku z tym należy sprawdzić, które zasoby są rzeczywiście otwarte przed kontynuowaniem oczyszczania do obsługi zakończenia. Zalecaną procedurą jest:

1. Zainicjuj uchwyty do wartości NULL.

1. W bloku instrukcji **__try** Przydziel zasoby. Dojścia są ustawione na wartości dodatnie w miarę przydzielenia zasobu.

1. W **`__finally`** bloku instrukcji Zwolnij każdy zasób, którego odpowiedni uchwyt lub zmienna flagi jest różna od zera lub nie ma wartości null.

## <a name="example"></a>Przykład

Na przykład poniższy kod używa procedury obsługi zakończenia, aby zamknąć trzy pliki i blok pamięci, który został przydzielony w bloku instrukcji **__try** . Przed oczyszczeniem zasobu, kod najpierw sprawdza, czy zasób został przydzielony.

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
