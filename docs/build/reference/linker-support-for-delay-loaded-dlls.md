---
title: Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 2ff5143b8c3850386f73ff713e7986fdc3b59fd1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301392"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem

Konsolidator Visual C++ obsługuje teraz opóźnionym ładowaniem bibliotek DLL. To zwalnia z konieczność użycia funkcji zestawu SDK Windows **LoadLibrary** i **GetProcAddress** do zaimplementowania opóźnione ładowanie bibliotek DLL.

Przed Visual C++ 6.0, jedynym sposobem, aby załadować biblioteki DLL w czasie wykonywania, było wystosowanie **LoadLibrary** i **GetProcAddress**; system operacyjny będzie załadować biblioteki DLL gdy plik wykonywalny lub biblioteka DLL używająca została załadowana.

Visual C++ 6.0, począwszy od podczas niejawnie łączenia z biblioteką DLL, konsolidator zawiera opcje, aby opóźnić załadować biblioteki DLL, dopóki program wywołuje funkcję w tej bibliotece DLL.

Aplikację można opóźnić załadować biblioteki DLL przy użyciu [/delayload (Opóźnij importowanie ładowania)](../../build/reference/delayload-delay-load-import.md) — opcja konsolidatora przy użyciu funkcji pomocnika (Domyślna implementacja dostarczone przez Visual C++). Funkcja pomocnika będzie załadować biblioteki DLL w czasie wykonywania przez wywołanie metody **LoadLibrary** i **GetProcAddress** dla Ciebie.

Należy wziąć pod uwagę Opóźniaj ładowanie biblioteki DLL, jeśli:

- Program nie może wywołać funkcję w bibliotece DLL.

- Funkcji w bibliotece DLL nie może zostać wywołana do czasu opóźnienia podczas wykonywania programu.

Można określić podczas kompilacji albo opóźnionego ładowania biblioteki dll. Plik EXE lub. Projekt biblioteki DLL. ELEMENT. Projekt biblioteki DLL, który opóźnia ładowanie jedną lub więcej bibliotek DLL nie powinien się wywoływać punktem wejścia ładowanych z opóźnieniem w funkcji Dllmain.

Opóźniaj ładowanie bibliotek DLL można znaleźć w następujących tematach:

- [Określanie bibliotek DLL w celu opóźnienia ładowania](../../build/reference/specifying-dlls-to-delay-load.md)

- [Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

- [Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)

- [Powiązywanie importów](../../build/reference/binding-imports.md)

- [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)

- [Zrzucanie importów załadowanych z opóźnieniem](../../build/reference/dumping-delay-loaded-imports.md)

- [Ograniczenia bibliotek DLL ładowanych z opóźnieniem](../../build/reference/constraints-of-delay-loading-dlls.md)

- [Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)

- [Tworzenie własnej funkcji Pomocnik](../../build/reference/developing-your-own-helper-function.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../../build/dlls-in-visual-cpp.md)<br/>
[Konsolidacja](../../build/reference/linking.md)
