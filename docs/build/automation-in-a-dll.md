---
title: Automatyzacja w bibliotece DLL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 69b5d723da2ac67de3c381b6a5bc09645c1f4341
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)