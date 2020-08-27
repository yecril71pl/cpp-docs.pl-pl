---
title: Oczyszczanie zasobów
description: Informacje o zwalnianiu zasobów podczas procedury obsługi wyjątków strukturalnych w obsłudze.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: dae92a515db25b9985a890d7d08cc213f88ecfea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898436"
---
# <a name="cleaning-up-resources"></a>Oczyszczanie zasobów

Podczas wykonywania procedury obsługi nie można wiedzieć, które zasoby zostały nabyte przed wywołaniem procedury obsługi zakończenia. Istnieje możliwość **`__try`** przerwania bloku instrukcji przed pozyskaniem wszystkich zasobów, dzięki czemu nie wszystkie zasoby zostały otwarte.

Aby można było bezpiecznie, należy sprawdzić, które zasoby są otwarte przed kontynuowaniem oczyszczania obsługi zakończenia. Zalecaną procedurą jest:

1. Zainicjuj uchwyty do wartości NULL.

1. W **`__try`** bloku instrukcji Uzyskaj zasoby. Dojścia są ustawione na wartości dodatnie w miarę nabycia zasobu.

1. W **`__finally`** bloku instrukcji Zwolnij każdy zasób, którego odpowiedni uchwyt lub zmienna flagi jest różna od zera lub nie ma wartości null.

## <a name="example"></a>Przykład

Na przykład poniższy kod używa procedury obsługi zakończenia, aby zamknąć trzy pliki i zwolnić blok pamięci. Te zasoby zostały uzyskane w **`__try`** bloku instrukcji. Przed oczyszczeniem zasobu, kod najpierw sprawdza, czy zasób został pobrany.

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

## <a name="see-also"></a>Zobacz też

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
