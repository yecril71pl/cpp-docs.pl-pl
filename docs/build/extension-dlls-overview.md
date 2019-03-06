---
title: 'Biblioteki DLL rozszerzeń: Omówienie'
ms.date: 11/04/2016
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: 0ad5c82d72a3cd9b4801274aefd40d96afdbcdd1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425058"
---
# <a name="mfc-extension-dlls-overview"></a>Biblioteki DLL rozszerzeń MFC Omówienie

Rozszerzenia MFC biblioteki DLL jest biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku pochodzące z istniejących klas biblioteki klas Microsoft Foundation. Biblioteki DLL rozszerzeń MFC są tworzone przy użyciu wersji biblioteki DLL MFC (znany także jako udostępnionej wersja MFC). Tylko pliki wykonywalne MFC (aplikacji lub zwykłych bibliotekach MFC dll), które są tworzone za pomocą udostępnionej wersja MFC można użyć rozszerzenia MFC biblioteki DLL. Za pomocą rozszerzenia MFC biblioteki DLL może wyprowadzać nowe klasy niestandardowej z MFC i następnie oferują tej rozszerzonej wersji biblioteki MFC do aplikacji, które wywołują bibliotekę DLL.

Biblioteki DLL rozszerzeń również może służyć do przekazywania obiekty pochodzące z MFC między aplikacją a biblioteki DLL. Funkcje elementów członkowskich skojarzonych z przekazany obiekt istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są prawidłowo wyeksportowana, korzystając z udostępnionej wersja dll biblioteki MFC, można przekazać za darmo MFC lub wskaźniki obiektów klasy pochodnej MFC między aplikacją a rozszerzenia MFC biblioteki dll, ładuje.

Na przykład bibliotekę DLL, która spełnia wymagania podstawowe rozszerzenia MFC biblioteki DLL, zobacz próbki MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). W szczególności Przyjrzyj się pliki Testdll1.cpp i Testdll2.cpp.

Pamiętaj, że termin AFXDLL nie jest już używany w dokumentacji języka Visual C++. Rozszerzenia MFC biblioteki DLL ma takie same charakterystyki jak wcześniejsze AFXDLL.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie biblioteki DLL rozszerzenia MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)

- [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Biblioteki innego typu niż DLL MFC: omówienie](../build/non-mfc-dlls-overview.md)

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Tworzenie biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Zobacz także

[Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)
