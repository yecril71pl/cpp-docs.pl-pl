---
title: FreeLibrary i AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821554"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary i AfxFreeLibrary

Procesy, które jawnie łączą się z biblioteką DLL, wywołują funkcję [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) , gdy moduł dll nie jest już wymagany. Ta funkcja zmniejsza liczbę odwołań modułu. A jeśli licznik odwołań ma wartość zero, nie jest mapowany z przestrzeni adresowej procesu.

W aplikacji MFC Użyj [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) zamiast, `FreeLibrary` aby zwolnić bibliotekę DLL rozszerzenia MFC. Interfejs (prototyp funkcji) dla `AfxFreeLibrary` jest taki sam jak. `FreeLibrary`

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [LoadLibrary i AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
