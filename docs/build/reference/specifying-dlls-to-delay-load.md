---
title: Określanie bibliotek DLL w celu opóźnienia ładowania
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: b1ca214d8c840d9e993d5a89823b63868a664bec
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424889"
---
# <a name="specifying-dlls-to-delay-load"></a>Określanie bibliotek DLL w celu opóźnienia ładowania

Można określić, które biblioteki dll w celu opóźnienia ładowania przy użyciu [/delayload](../../build/reference/delayload-delay-load-import.md):`dllname` — opcja konsolidatora. Jeśli użytkownik nie chce używać własnej wersji funkcji pomocnika, możesz również połączyć program jest połączony z delayimp.lib (dla aplikacji klasycznych) lub dloadhelper.lib (dla aplikacji ze sklepu).

Poniżej przedstawiono prosty przykład biblioteki DLL ładowanych z opóźnieniem:

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

Tworzenie wersji debugowania projektu. Przejrzyj kod za pomocą debugera i zauważą, że user32.dll jest załadowany, tylko wtedy, gdy wywołanie `MessageBox`.

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)
