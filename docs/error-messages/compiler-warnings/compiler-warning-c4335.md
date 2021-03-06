---
title: Ostrzeżenie kompilatora C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627124"
---
# <a name="compiler-warning-c4335"></a>Ostrzeżenie kompilatora C4335

Wykryto format pliku Mac: Skonwertuj plik źródłowy do formatu DOS lub UNIX

Znak zakończenia wiersza pierwszego wiersza pliku źródłowego to Macintosh Style ("\r") w przeciwieństwie do systemu UNIX ("\n") lub DOS ("\r\n").

To ostrzeżenie jest zawsze emitowane jako błąd.  Aby uzyskać informacje na temat sposobu wyłączania tego ostrzeżenia, zobacz pragma [ostrzeżenia](../../preprocessor/warning.md) .  To ostrzeżenie jest również wydawane tylko raz na jednostka kompilacji. W związku z tym, jeśli istnieje wiele dyrektyw `#include`, które określają pliki w formacie Macintosh, C4335 zostanie wystawiony tylko raz.

Jednym ze sposobów generowania plików w formacie komputerów Macintosh jest użycie **zaawansowanych opcji zapisywania** (w menu **plik** ) w programie Visual Studio.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4335.

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
