---
title: Automatyzacja w bibliotece DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cde5d0e400f1bdd3f5a851d47da581380273b04a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717789"
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

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)