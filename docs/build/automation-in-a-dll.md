---
title: Automatyzacja w bibliotece DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 3cc5ca456842707a2c3de7b2fd74abc73d9a5307
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422289"
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

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)
