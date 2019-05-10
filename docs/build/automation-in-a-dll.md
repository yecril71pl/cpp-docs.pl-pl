---
title: Automatyzacja w bibliotece DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220920"
---
# <a name="automation-in-a-dll"></a>Automatyzacja w bibliotece DLL

Po wybraniu opcji automatyzacji w Kreatorze MFC DLL, Kreator umożliwia następujące czynności:

- Język opisu obiektów starter (. Plik ODL)

- Dyrektywa include w pliku STDAFX.h Afxole.h

- Implementacja `DllGetClassObject` funkcji, która wywołuje **AfxDllGetClassObject** — funkcja

- Implementacja `DllCanUnloadNow` funkcji, która wywołuje **AfxDllCanUnloadNow** — funkcja

- Implementacja `DllRegisterServer` funkcji, która wywołuje [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) — funkcja

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Serwery automatyzacji](../mfc/automation-servers.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
