---
title: LoadLibrary i AfxLoadLibrary | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- LoadLibrary
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc3be5d374995c657021952184794f146c37f4dc
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753591"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary i AfxLoadLibrary

Przetwarza wywołanie [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) (lub [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) jawnie powiązać biblioteki DLL. Jeśli funkcja zakończy się powodzeniem, mapy określonej biblioteki DLL do przestrzeni adresowej procesu wywołującego i zwraca dojście do pliku DLL, które mogą być używane z innych funkcji w Konsolidacja jawna — na przykład `GetProcAddress` i `FreeLibrary`.

`LoadLibrary` próbuje zlokalizować biblioteki DLL przy użyciu takiej samej kolejności wyszukiwania, używaną niejawne łączenia. Jeśli system nie może odnaleźć biblioteki DLL lub punkt wejścia funkcja zwraca wartość FALSE, `LoadLibrary` zwraca wartość NULL. Jeśli wywołanie `LoadLibrary` Określa moduł biblioteki DLL, który jest już zamapowany do przestrzeni adresowej procesu wywołującego, funkcja zwraca uchwyt DLL i zwiększa liczbę odwołanie do modułu.

Jeśli funkcja punktu wejścia biblioteki DLL, system operacyjny wywołuje funkcję w kontekście wątku, który wywołuje `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, gdy biblioteka DLL jest już dołączony do procesu z powodu poprzedniego wywołania `LoadLibrary` mający nie odpowiedniego wywołania `FreeLibrary` funkcji.

Aplikacje MFC, których załadować biblioteki DLL rozszerzeń MFC, zaleca się używanie `AfxLoadLibrary` zamiast `LoadLibrary`. `AfxLoadLibrary` Synchronizacja wątku uchwytów przed wywołaniem `LoadLibrary`. Interfejs (prototypu funkcji) do `AfxLoadLibrary` jest taka sama jak `LoadLibrary`.

Jeśli system Windows nie może załadować biblioteki DLL, proces może próbować odzyskać sprawność po błędzie. Na przykład proces może powiadamia użytkownika o błędzie i poprosić użytkownika, aby określić inną ścieżkę do pliku DLL.

> [!IMPORTANT]  
> Upewnij się określić pełną ścieżkę żadnych bibliotek DLL. Bieżący katalog jest najpierw przeszukiwane, gdy pliki są ładowane. Jeśli nie kwalifikujesz ścieżkę pliku, może załadować pliku, który nie jest to zamierzone. Inny sposób, aby zapobiec takiej sytuacji polega na użyciu [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) — opcja konsolidatora.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Jak połączyć niejawnie z biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Określić jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?

- [Kolejność wyszukiwania biblioteki dll](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)

- [FreeLibrary i AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Zobacz także

- [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)