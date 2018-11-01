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
ms.openlocfilehash: ce52eb43fa8f371b68d836f01163003f056f34c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530237"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary i AfxFreeLibrary

Procesy, które jawnie utworzyć łącze do wywołania biblioteki DLL [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary) działa, gdy moduł DLL nie jest już potrzebny. Ta funkcja zmniejsza liczbę odwołań modułu i jeśli licznik odwołań wynosi zero, unmaps go z przestrzeni adresowej procesu.

W aplikacji MFC, należy użyć [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) zamiast `FreeLibrary` wyładować bibliotekę DLL rozszerzenia MFC. Interfejs (prototyp funkcji) `AfxFreeLibrary` jest taka sama jak `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Jak połączyć niejawnie biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)