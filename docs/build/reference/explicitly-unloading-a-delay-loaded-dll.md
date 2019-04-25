---
title: Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: 9909a3e179aa6c0af3a622c7bf1b545326f90bbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293462"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem

[/Opóźnienie](delay-delay-load-import-settings.md): unload — opcja konsolidatora pozwala wyładować bibliotekę DLL, które było ładowane z opóźnieniem. Domyślnie, gdy kod zwalnia DLL (przy użyciu/DELAY: Unload i **__FUnloadDelayLoadedDLL2**), importów załadowanych z opóźnieniem pozostają w tabeli adresów importowania (IAT). Jednak jeśli używasz/DELAY: Unload w wierszu polecenia konsolidatora funkcji pomocnika będzie obsługiwać jawne zwalnianie bibliotek DLL, zresetowanie IAT do ich oryginalnej formie; wskaźniki obecnie nieprawidłowym zostaną zastąpione. IAT jest polem w [ImgDelayDescr](calling-conventions-parameters-and-return-type.md) zawierający adres kopię oryginalnego IAT (jeśli istnieje).

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>Komentarze

Ważne uwagi na zwalnianie bibliotek DLL ładowanych z opóźnieniem:

- Można znaleźć implementacji **__FUnloadDelayLoadedDLL2** funkcji w pliku \VC7\INCLUDE\DELAYHLP. CPP.

- Nazwa parametru **__FUnloadDelayLoadedDLL2** funkcja musi dokładnie odpowiadać (z uwzględnieniem wielkości liter) biblioteki importowanej zawartość (czyli ciąg też w Tabela importu na obrazie). Można wyświetlić zawartość biblioteki importu za pomocą [DUMPBIN /DEPENDENTS](dependents.md). Jeśli konieczne jest dopasowanie bez uwzględniania wielkości liter ciągu, możesz zaktualizować **__FUnloadDelayLoadedDLL2** użycia jednej z funkcji CRT w ciągu lub wywołanie interfejsu API Windows.

Zobacz [zwalnianie bibliotek DLL z Delay-Loaded](unloading-a-delay-loaded-dll.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
