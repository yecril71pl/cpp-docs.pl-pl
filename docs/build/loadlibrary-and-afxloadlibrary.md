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
ms.openlocfilehash: 03815ac535033d9b0fdf0146c0200be16e5ae91a
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465989"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary i AfxLoadLibrary

Przetwarza wywołanie [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) (lub [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) Aby jawnie utworzyć łącze do biblioteki DLL. Jeśli funkcja się powiedzie, mapuje daną bibliotekę DLL do przestrzeni adresowej procesu wywołującego i zwraca uchwyt do biblioteki DLL, która może być używany z innymi funkcjami jawnego łączenia — na przykład `GetProcAddress` i `FreeLibrary`.

`LoadLibrary` próbuje zlokalizować bibliotekę DLL przy użyciu tej samej kolejności wyszukiwania, która jest używana w przypadku łączenia niejawnego. Jeśli system nie może odnaleźć biblioteki DLL lub jeśli funkcja punktu wejścia zwraca wartość FALSE, `LoadLibrary` zwraca wartość NULL. Jeśli wywołanie `LoadLibrary` Określa moduł DLL, który jest już zmapowany do przestrzeni adresowej procesu wywołującego, funkcja zwraca uchwyt DLL i zwiększa odczyt licznika odwołań modułu.

Jeśli biblioteka DLL pełni funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączony do procesu ze względu na poprzednie wywołanie `LoadLibrary` , nie ma odpowiedniego wywołania do `FreeLibrary` funkcji.

Dla aplikacji MFC, które ładują biblioteki DLL rozszerzeń MFC, firma Microsoft zaleca użycie `AfxLoadLibrary` zamiast `LoadLibrary`. `AfxLoadLibrary` obsługuje synchronizację wątków, zanim wywołasz `LoadLibrary`. Interfejs (prototyp funkcji) do `AfxLoadLibrary` jest taka sama jak `LoadLibrary`.

Jeśli Windows nie może załadować biblioteki DLL, proces może próbować odzyskać sprawność po błędzie. Na przykład ten proces może powiadomić użytkownika o błędzie i poprosić użytkownika, aby określić inną ścieżkę do pliku DLL.

> [!IMPORTANT]  
> Upewnij się określić pełną ścieżkę do każdej biblioteki dll. Bieżący katalog jest przeszukiwany w pierwszej kolejności gdy pliki są ładowane. Jeśli nie kwalifikuje się ścieżkę pliku, może załadować pliku, który nie jest to zamierzone. Innym sposobem, aby zapobiec takiej sytuacji jest za pomocą [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) — opcja konsolidatora.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Jak połączyć niejawnie biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary i AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Zobacz także

- [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)