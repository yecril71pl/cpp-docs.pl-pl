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
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360657"
---
# <a name="automation-in-a-dll"></a>Automatyzacja w bibliotece DLL
Po wybraniu opcji automatyzacji MFC DLL kreatora, Kreator udostępnia z następujących czynności:  
  
-   Język opisu obiektów starter (. Plik ODL)  
  
-   Dyrektywa include w pliku STDAFX.h Afxole.h  
  
-   Implementacja interfejsu `DllGetClassObject` funkcji, która wywołuje **AfxDllGetClassObject** — funkcja  
  
-   Implementacja interfejsu `DllCanUnloadNow` funkcji, która wywołuje **AfxDllCanUnloadNow** — funkcja  
  
-   Implementacja interfejsu `DllRegisterServer` funkcji, która wywołuje [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) — funkcja  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Serwery automatyzacji](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)