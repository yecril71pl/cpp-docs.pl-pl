---
title: 'Biblioteki DLL inne niż MFC: omówienie'
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 15cceb80b0f771c0c304572e2263b1479d6b0db7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693027"
---
# <a name="non-mfc-dlls-overview"></a>Biblioteki DLL inne niż MFC: omówienie

Nie - MFC DLL jest biblioteki DLL, która nie używa MFC wewnętrznie i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub inne niż MFC. Funkcje eksportowane są zazwyczaj z DLL bez MFC za pomocą standardowego interfejsu C.

Aby uzyskać więcej informacji na temat dll bez MFC, zobacz [bibliotek dołączanych dynamicznie](/windows/desktop/dlls/dynamic-link-libraries) w zestawie Windows SDK.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Wskazówki: Tworzenie i używanie biblioteki dołączanej dynamicznie](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)

- [Łączenie pliku wykonywalnego z biblioteką DLL](../build/linking-an-executable-to-a-dll.md)

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)