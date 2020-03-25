---
title: 'Porady: unieruchamianie wskaźników oraz tablic'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: 8dc42690f0f56b97b2af3ed54dfb17d49b081695
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172220"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Porady: unieruchamianie wskaźników oraz tablic

Przypinanie obiektu podrzędnego zdefiniowanego w obiekcie zarządzanym ma wpływ na przypinanie całego obiektu.  Na przykład, jeśli jakikolwiek element tablicy jest przypięty, cała tablica jest również przypięta. Brak rozszerzeń języka do deklarowania przypiętej tablicy. Aby przypiąć tablicę, zadeklaruj przypinany wskaźnik do jego typu elementu i Przypnij jeden z jego elementów.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Zobacz też

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
