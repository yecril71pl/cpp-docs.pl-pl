---
title: Ograniczenia bibliotek DLL ładowanych z opóźnieniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40774d6307eb9b423ebd4fd303a48acbd87eda24
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465991"
---
# <a name="constraints-of-delay-loading-dlls"></a>Ograniczenia bibliotek DLL ładowanych z opóźnieniem
Istnieją ograniczenia dotyczące ładowania opóźnienie importów.  
  
-   Nie można obsłużyć importuje dane. Obejście tego problemu jest jawnie obsługiwać importu danych przy użyciu polecenia `LoadLibrary` (lub `GetModuleHandle` po określeniu pomocnika opóźnionego ładowania została załadowana biblioteka DLL) i `GetProcAddress`.  
  
-   Opóźniaj ładowanie Kernel32.dll nie jest obsługiwane. Ta biblioteka DLL jest niezbędne dla procedur pomocnika opóźnionego ładowania przeprowadzić Opóźniaj ładowanie.  
  
-   [Powiązanie](../../build/reference/binding-imports.md) wpisu punkty, które są przekazywane nie jest obsługiwana.  
  
-   Opóźnienie załadowanie biblioteki DLL nie może spowodować takie samo zachowanie proces w przypadku inicjowania procesu, występujących w punkcie wejścia biblioteki DLL ładowanych z opóźnieniem. Inne przypadki obejmują statyczne TLS (lokalny magazyn wątków), zadeklarowane za pomocą [__declspec(thread)](../../cpp/thread.md), który nie jest obsługiwany podczas ładowania biblioteki DLL za pomocą `LoadLibrary`. Dynamiczne TLS, za pomocą `TlsAlloc`, `TlsFree`, `TlsGetValue`, i `TlsSetValue`, jest nadal dostępny do użytku w statycznych lub ładowanych z opóźnieniem bibliotek DLL.  
  
-   Wskaźniki funkcji statycznej (globalna) powinien należy ponownie zainicjować importowanych funkcji po pierwszym wywołanie do funkcji. Jest to spowodowane wskaże pierwszym użyciu wskaźnik funkcji do osadzenia.  
  
-   Nie ma możliwości obecnie w celu opóźnienia ładowania tylko określonych procedur z biblioteki DLL podczas korzystania z mechanizmu normalne importu.  
  
-   Konwencje wywoływania niestandardowego (np. przy użyciu kodów stanu na x86 architektury) nie są obsługiwane. Ponadto rejestrów zmiennoprzecinkowych nie są zapisywane na dowolnej platformie. Użycie usługi niestandardowego elementu pomocniczego procedury lub procedury punktu zaczepienia typów zmiennoprzecinkowych, muszą całkowicie Zapisz i przywrócić stan zapisu zmiennoprzecinkowego na maszynach z rejestrem konwencje parametrami zmiennoprzecinkowych wywoływania. Należy zachować ostrożność podczas ładowania biblioteki DLL CRT, jeśli wywołanie funkcji CRT, które przyjmują parametry zmiennoprzecinkowych na stosie przetwarzający dane liczbowe (NDP) w funkcji pomocy opóźnienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary — funkcja](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [GetModuleHandle — funkcja](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress — funkcja](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [Funkcja TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)   
 [Funkcja TlsFree — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)   
 [TlsGetValue — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)   
 [TlsSetValue — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)