---
title: Automatyzacja w bibliotece DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 4ac60c44348ea21f490cb312285ae88ac682cf7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341663"
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

[Biblioteki DLL w programie Visual C++](dlls-in-visual-cpp.md)
