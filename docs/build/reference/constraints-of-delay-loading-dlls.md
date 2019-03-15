---
title: Ograniczenia bibliotek DLL ładowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: e37890fcd757a52ddeff0ccd79289bbc0c35e042
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816584"
---
# <a name="constraints-of-delay-loading-dlls"></a>Ograniczenia bibliotek DLL ładowanych z opóźnieniem

Istnieją ograniczenia dotyczące ładowania opóźnienie importów.

- Nie można obsłużyć importuje dane. Obejście tego problemu jest jawnie obsługiwać importu danych przy użyciu polecenia `LoadLibrary` (lub `GetModuleHandle` po określeniu pomocnika opóźnionego ładowania została załadowana biblioteka DLL) i `GetProcAddress`.

- Opóźniaj ładowanie Kernel32.dll nie jest obsługiwane. Ta biblioteka DLL jest niezbędne dla procedur pomocnika opóźnionego ładowania przeprowadzić Opóźniaj ładowanie.

- [Powiązanie](binding-imports.md) wpisu punkty, które są przekazywane nie jest obsługiwana.

- Opóźnienie załadowanie biblioteki DLL nie może spowodować takie samo zachowanie proces w przypadku inicjowania procesu, występujących w punkcie wejścia biblioteki DLL ładowanych z opóźnieniem. Inne przypadki obejmują statyczne TLS (lokalny magazyn wątków), zadeklarowane za pomocą [__declspec(thread)](../../cpp/thread.md), który nie jest obsługiwany podczas ładowania biblioteki DLL za pomocą `LoadLibrary`. Dynamiczne TLS, za pomocą `TlsAlloc`, `TlsFree`, `TlsGetValue`, i `TlsSetValue`, jest nadal dostępny do użytku w statycznych lub ładowanych z opóźnieniem bibliotek DLL.

- Wskaźniki funkcji statycznej (globalna) powinien należy ponownie zainicjować importowanych funkcji po pierwszym wywołanie do funkcji. Jest to spowodowane wskaże pierwszym użyciu wskaźnik funkcji do osadzenia.

- Nie ma możliwości obecnie w celu opóźnienia ładowania tylko określonych procedur z biblioteki DLL podczas korzystania z mechanizmu normalne importu.

- Konwencje wywoływania niestandardowego (np. przy użyciu kodów stanu na x86 architektury) nie są obsługiwane. Ponadto rejestrów zmiennoprzecinkowych nie są zapisywane na dowolnej platformie. Użycie usługi niestandardowego elementu pomocniczego procedury lub procedury punktu zaczepienia typów zmiennoprzecinkowych, muszą całkowicie Zapisz i przywrócić stan zapisu zmiennoprzecinkowego na maszynach z rejestrem konwencje parametrami zmiennoprzecinkowych wywoływania. Należy zachować ostrożność podczas ładowania biblioteki DLL CRT, jeśli wywołanie funkcji CRT, które przyjmują parametry zmiennoprzecinkowych na stosie przetwarzający dane liczbowe (NDP) w funkcji pomocy opóźnienia.

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary — funkcja](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)<br/>
[GetModuleHandle — funkcja](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea)<br/>
[GetProcAddress — funkcja](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[Funkcja TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[Funkcja TlsFree — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue — funkcja](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
