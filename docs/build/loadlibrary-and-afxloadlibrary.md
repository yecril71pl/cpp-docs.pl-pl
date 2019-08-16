---
title: LoadLibrary i AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493209"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary i AfxLoadLibrary

Przetwarza wywołanie [LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) lub [LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (lub [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) w celu jawnego łączenia z biblioteką DLL. Jeśli funkcja się powiedzie, mapuje określoną bibliotekę DLL do przestrzeni adresowej procesu wywołującego i zwraca dojście do biblioteki DLL, która może być używana z innymi funkcjami w przypadku jawnego łączenia — na `GetProcAddress` przykład `FreeLibrary`i.

`LoadLibrary`próbuje zlokalizować bibliotekę DLL przy użyciu tej samej sekwencji wyszukiwania, która jest używana do niejawnego łączenia. Jeśli system nie może odnaleźć biblioteki DLL lub jeśli funkcja punktu wejścia zwróci wartość false, `LoadLibrary` zwraca wartość null. Jeśli wywołanie `LoadLibrary` określa moduł dll, który jest już mapowany do przestrzeni adresowej procesu wywołującego, funkcja zwraca dojście biblioteki DLL i zwiększa liczbę odwołań modułu.

Jeśli biblioteka DLL ma funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączona do procesu ze względu na poprzednie wywołanie `LoadLibrary` , które nie ma odpowiedniego wywołania `FreeLibrary` funkcji.

W przypadku aplikacji MFC, które ładują biblioteki DLL rozszerzenia MFC, zalecamy `AfxLoadLibrary` użycie `LoadLibrary`zamiast. `AfxLoadLibrary`obsługuje synchronizację wątków przed wywołaniem `LoadLibrary`. Interfejs (prototyp funkcji) `AfxLoadLibrary` jest taki sam jak. `LoadLibrary`

Jeśli system Windows nie może załadować biblioteki DLL, proces może próbować odzyskać sprawność po błędzie. Na przykład proces może powiadomić użytkownika o błędzie i polecić użytkownikowi określenie innej ścieżki do biblioteki DLL.

> [!IMPORTANT]
> Upewnij się, że określono pełną ścieżkę do wszystkich bibliotek DLL. Bieżący katalog jest przeszukiwany w pierwszej kolejności podczas ładowania plików. Jeśli nie kwalifikujesz się do ścieżki pliku, może zostać załadowany plik, który nie jest zamierzonym. Innym sposobem na uniknięcie tego jest użycie opcji konsolidatora [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) .

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary i AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Zobacz także

- [Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)
