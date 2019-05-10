---
title: 'Biblioteki DLL rozszerzeń: Omówienie'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221370"
---
# <a name="mfc-extension-dlls-overview"></a>Biblioteki DLL rozszerzeń MFC Omówienie

Rozszerzenia MFC biblioteki DLL jest biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku pochodzące z istniejących klas biblioteki klas Microsoft Foundation. Biblioteki DLL rozszerzeń MFC są tworzone przy użyciu wersji biblioteki DLL MFC (znany także jako udostępnionej wersja MFC). Tylko pliki wykonywalne MFC (aplikacji lub zwykłych bibliotekach MFC dll), które są tworzone za pomocą udostępnionej wersja MFC można użyć rozszerzenia MFC biblioteki DLL. Za pomocą rozszerzenia MFC biblioteki DLL może wyprowadzać nowe klasy niestandardowej z MFC i następnie oferują tej rozszerzonej wersji biblioteki MFC do aplikacji, które wywołują bibliotekę DLL.

Biblioteki DLL rozszerzeń również może służyć do przekazywania obiekty pochodzące z MFC między aplikacją a biblioteki DLL. Funkcje elementów członkowskich skojarzonych z przekazany obiekt istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są prawidłowo wyeksportowana, korzystając z udostępnionej wersja dll biblioteki MFC, można przekazać za darmo MFC lub wskaźniki obiektów klasy pochodnej MFC między aplikacją a rozszerzenia MFC biblioteki dll, ładuje.

Na przykład bibliotekę DLL, która spełnia wymagania podstawowe rozszerzenia MFC biblioteki DLL, zobacz próbki MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). W szczególności Przyjrzyj się pliki Testdll1.cpp i Testdll2.cpp.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie biblioteki DLL rozszerzenia MFC](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Biblioteki DLL rozszerzeń MFC](extension-dlls.md)

- [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Biblioteki innego typu niż DLL MFC: omówienie](non-mfc-dlls-overview.md)

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Tworzenie biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Zobacz także

[Rodzaje bibliotek DLL](kinds-of-dlls.md)
