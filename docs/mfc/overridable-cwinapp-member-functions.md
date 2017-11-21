---
title: "Funkcje Członkowskie CWinApp z możliwością przesłonięcia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3de4444aaeb55ab30ec6ce7e0ebd187c8468f673
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia
[Cwinapp —](../mfc/reference/cwinapp-class.md) udostępnia kilka kluczowe funkcje Członkowskie możliwym do zastąpienia (`CWinApp` zastępuje te elementy członkowskie z klasy [cwinthread —](../mfc/reference/cwinthread-class.md), z którego `CWinApp` pochodzi):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [Uruchom](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 Jedynym `CWinApp` jest funkcji członkowskiej, który należy zastąpić `InitInstance`.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
