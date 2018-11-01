---
title: Ostrzeżenie kompilatora C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: 43c2f5d9092cdbad14e429349bd7d04e236b75e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447284"
---
# <a name="compiler-warning-c4335"></a>Ostrzeżenie kompilatora C4335

Wykryto format pliku Mac: Skonwertuj plik źródłowy do formatu DOS lub systemu UNIX

Znak zakończenia wiersza pierwszego wiersza pliku źródłowego jest styl dla komputerów Macintosh ('\r'), w przeciwieństwie do systemu UNIX ('\n') lub systemu DOS ("\r\n").

To jest zawsze ostrzeżenie jako błąd.  Zobacz [ostrzeżenie](../../preprocessor/warning.md) pragma, aby uzyskać informacje o sposobie wyłączyć to ostrzeżenie.  Ponadto to tylko ostrzeżenie raz na compiland —. W związku z tym jeśli dostępnych jest wiele `#include` dyrektyw, które określają pliki w formacie dla komputerów Macintosh, C4335 tylko pojawi się jeden raz.

Jednym ze sposobów ma generować pliki w formacie dla komputerów Macintosh polega na użyciu **zaawansowane opcje zapisywania** (na **pliku** menu) w programie Visual Studio.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```