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

Po wybraniu opcji Automatyzacja w Kreatorze MFC DLL, Kreator udostępnia następujące informacje:

- Język opisu obiektu początkowego (. ODL) — plik

- Dyrektywa include w pliku STDAFX. h dla Afxole. h

- Implementacja `DllGetClassObject` funkcji, która wywołuje funkcję **AfxDllGetClassObject**

- Implementacja `DllCanUnloadNow` funkcji, która wywołuje funkcję **AfxDllCanUnloadNow**

- Implementacja `DllRegisterServer` funkcji, która wywołuje funkcję [COleObjectFactory:: UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Serwery automatyzacji](../mfc/automation-servers.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
