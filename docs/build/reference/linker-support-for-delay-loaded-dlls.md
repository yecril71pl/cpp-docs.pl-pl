---
title: Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 384ea563853906a76e2c9993cbcedb3b15c354f2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217588"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem

Konsolidator MSVC obsługuje teraz opóźnionym ładowaniem bibliotek DLL. To zwalnia z konieczność użycia funkcji zestawu SDK Windows **LoadLibrary** i **GetProcAddress** do zaimplementowania opóźnione ładowanie bibliotek DLL.

Przed Visual C++ 6.0, jedynym sposobem, aby załadować biblioteki DLL w czasie wykonywania, było wystosowanie **LoadLibrary** i **GetProcAddress**; system operacyjny będzie załadować biblioteki DLL gdy plik wykonywalny lub biblioteka DLL używająca została załadowana.

Visual C++ 6.0, począwszy od podczas niejawnie łączenia z biblioteką DLL, konsolidator zawiera opcje, aby opóźnić załadować biblioteki DLL, dopóki program wywołuje funkcję w tej bibliotece DLL.

Aplikację można opóźnić załadować biblioteki DLL przy użyciu [/delayload (Opóźnij importowanie ładowania)](delayload-delay-load-import.md) — opcja konsolidatora przy użyciu funkcji pomocnika (Domyślna implementacja dostarczone przez Visual C++). Funkcja pomocnika będzie załadować biblioteki DLL w czasie wykonywania przez wywołanie metody **LoadLibrary** i **GetProcAddress** dla Ciebie.

Należy wziąć pod uwagę Opóźniaj ładowanie biblioteki DLL, jeśli:

- Program nie może wywołać funkcję w bibliotece DLL.

- Funkcji w bibliotece DLL nie może zostać wywołana do czasu opóźnienia podczas wykonywania programu.

Można określić podczas kompilacji albo opóźnionego ładowania biblioteki dll. Plik EXE lub. Projekt biblioteki DLL. ELEMENT. Projekt biblioteki DLL, który opóźnia ładowanie jedną lub więcej bibliotek DLL nie powinien się wywoływać punktem wejścia ładowanych z opóźnieniem w funkcji Dllmain.

Opóźniaj ładowanie bibliotek DLL można znaleźć w następujących tematach:

- [Określanie bibliotek DLL w celu opóźnienia ładowania](specifying-dlls-to-delay-load.md)

- [Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem](explicitly-unloading-a-delay-loaded-dll.md)

- [Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem](loading-all-imports-for-a-delay-loaded-dll.md)

- [Powiązywanie importów](binding-imports.md)

- [Obsługa błędów oraz powiadomienia](error-handling-and-notification.md)

- [Zrzucanie importów załadowanych z opóźnieniem](dumping-delay-loaded-imports.md)

- [Ograniczenia bibliotek DLL ładowanych z opóźnieniem](constraints-of-delay-loading-dlls.md)

- [Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)

- [Tworzenie własnej funkcji Pomocnik](developing-your-own-helper-function.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](../dlls-in-visual-cpp.md)<br/>
[Dokumentacja konsolidatora MSVC](linking.md)
