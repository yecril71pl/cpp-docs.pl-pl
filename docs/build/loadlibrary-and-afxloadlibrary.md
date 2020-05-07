---
title: LoadLibrary i AfxLoadLibrary
description: Używanie funkcji LoadLibrary i AfxLoadLibrary w celu jawnego ładowania bibliotek DLL w MSVC.
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821541"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary i AfxLoadLibrary

Przetwarza wywołanie funkcji [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) lub [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) w celu jawnego łączenia z biblioteką DLL. (Aplikacje MFC używają [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) lub [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)). Jeśli funkcja się powiedzie, mapuje określoną bibliotekę DLL do przestrzeni adresowej procesu wywołującego i zwraca dojście do biblioteki DLL. Dojście jest wymagane w innych funkcjach używanych do jawnego łączenia — na `GetProcAddress` przykład `FreeLibrary`i. Aby uzyskać więcej informacji, zobacz [jawne łączenie](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary`próbuje zlokalizować bibliotekę DLL przy użyciu tej samej sekwencji wyszukiwania, która jest używana do niejawnego łączenia. `LoadLibraryEx`zapewnia większą kontrolę nad kolejnością ścieżki wyszukiwania. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/dlls/dynamic-link-library-search-order). Jeśli system nie może odnaleźć biblioteki DLL lub jeśli funkcja punktu wejścia zwróci wartość FALSE, `LoadLibrary` zwraca wartość null. Jeśli wywołanie `LoadLibrary` określa moduł dll, który jest już mapowany do przestrzeni adresowej procesu wywołującego, funkcja zwraca dojście biblioteki DLL i zwiększa liczbę odwołań modułu.

Jeśli biblioteka DLL ma funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał `LoadLibrary` lub. `LoadLibraryEx` Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączona do procesu. Dzieje się tak, gdy poprzednie wywołanie `LoadLibrary` lub `LoadLibraryEx` dla biblioteki DLL nie ma odpowiedniego wywołania `FreeLibrary` funkcji.

W przypadku aplikacji MFC, które ładują biblioteki DLL rozszerzenia MFC, zalecamy `AfxLoadLibrary` użycie `AfxLoadLibraryEx` lub zamiast `LoadLibrary` lub `LoadLibraryEx`. Funkcje MFC obsługują synchronizację wątków przed jawne załadowaniem biblioteki DLL. Interfejsy (prototypy funkcji) `AfxLoadLibrary` do i `AfxLoadLibraryEx` są takie same jak `LoadLibrary` i. `LoadLibraryEx`

Jeśli system Windows nie może załadować biblioteki DLL, proces może próbować odzyskać sprawność po błędzie. Na przykład może powiadomić użytkownika o błędzie, a następnie poproszony o podanie innej ścieżki do biblioteki DLL.

> [!IMPORTANT]
> Upewnij się, że określono pełną ścieżkę do wszystkich bibliotek DLL. Bieżący katalog może być przeszukiwany w pierwszej kolejności, gdy `LoadLibrary`pliki są ładowane przez program. Jeśli nie masz w pełni kwalifikowanej ścieżki pliku, może zostać załadowany plik inny niż przewidziany. Podczas tworzenia biblioteki DLL Użyj opcji konsolidatora [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) , aby określić kolejność wyszukiwania dla statycznie połączonych bibliotek DLL. W bibliotekach DLL Użyj zarówno kompletnych ścieżek do jawnie załadowanych zależności `LoadLibraryEx` , `AfxLoadLibraryEx` jak i wywołań parametrów w celu określenia kolejności wyszukiwania w module. Aby uzyskać więcej informacji, zobacz temat w obszarze [biblioteka dołączana dynamicznie](/windows/win32/dlls/dynamic-link-library-security) i [kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary i AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Zobacz też

- [Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
