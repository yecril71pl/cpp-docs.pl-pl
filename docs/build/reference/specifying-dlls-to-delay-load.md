---
title: Określanie bibliotek DLL w celu opóźnienia ładowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e9becc0a686d3add5db140b239f1997f81a45be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722582"
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

## <a name="see-also"></a>Zobacz też

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)