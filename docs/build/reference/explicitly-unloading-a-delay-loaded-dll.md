---
title: Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 171acf9689c01649b86c2383d17136c926e25c57
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374177"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem
[/Delay](../../build/reference/delay-delay-load-import-settings.md): unload — opcja konsolidatora można zwolnić bibliotekę DLL, która załadowane z opóźnieniem. Domyślnie po kodzie zwalnia biblioteki DLL (przy użyciu/DELAY: Unload i **__FUnloadDelayLoadedDLL2**), pozostają Importy załadowane z opóźnieniem w tabelę adresów importu (IAT). Jednak jeśli używasz/DELAY: Unload w wierszu polecenia konsolidatora funkcji Pomocnik będzie obsługiwać ładowanej biblioteki DLL zresetowanie IAT do postaci oryginalnej; wskaźniki obecnie nieprawidłowym zostaną zastąpione. IAT jest polem w [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) zawierający adres kopię oryginalnej IAT (jeśli istnieje).  
  
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
 Ważne uwagi na zwalnianie bibliotek DLL załadowanych z opóźnieniem:  
  
-   Wdrożenia można znaleźć **__FUnloadDelayLoadedDLL2** funkcji w pliku \VC7\INCLUDE\DELAYHLP. CPP.  
  
-   Nazwa parametru **__FUnloadDelayLoadedDLL2** funkcja musi dokładnie odpowiadać (w tym przypadku) biblioteki importu zawartość (który ciągu jest również importowanie tabeli w obrazie). Można wyświetlić zawartość biblioteki importu z [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Jeśli konieczne jest dopasowanie ciągu bez uwzględniania wielkości liter, możesz je zaktualizować **__FUnloadDelayLoadedDLL2** użycia jednej z funkcji CRT ciągów lub wywołanie interfejsu API systemu Windows.  
  
 Zobacz [zwalnianie bibliotek DLL z Delay-Loaded](../../build/reference/unloading-a-delay-loaded-dll.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)