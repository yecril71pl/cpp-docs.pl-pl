---
title: Ostrzeżenie kompilatora C4335 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036582"
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