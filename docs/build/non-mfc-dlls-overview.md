---
title: 'Biblioteki DLL inne niż MFC: Omówienie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30a6fef31dee39cc6337b9b8b7dd3b66ee3adb67
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702588"
---
# <a name="non-mfc-dlls-overview"></a>Biblioteki DLL inne niż MFC: omówienie

Nie - MFC DLL jest biblioteki DLL, która nie używa MFC wewnętrznie i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub inne niż MFC. Funkcje eksportowane są zazwyczaj z DLL bez MFC za pomocą standardowego interfejsu C.

Aby uzyskać więcej informacji na temat dll bez MFC, zobacz [bibliotek dołączanych dynamicznie](https://msdn.microsoft.com/library/windows/desktop/ms682589) w zestawie Windows SDK.

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