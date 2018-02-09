---
title: "Zalety znak przenośności zestawu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce02fa834c39f629990d4f3c9785de94bd02196
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="benefits-of-character-set-portability"></a>Zalety przenośności zestawu znaków
Możesz mogą korzystać z funkcji środowiska wykonawczego przenośność MFC i C nawet wtedy, gdy użytkownik nie jest obecnie planowane internationalize aplikacji:  
  
-   Kodowanie portably sprawia, że kod podstawowa elastyczne. Można później przenieść go łatwo Unicode lub MBCS.  
  
-   Przy użyciu Unicode spowoduje, że aplikacje dla systemu Windows większą wydajność. Ponieważ system Windows używa Unicode, ciągów Unicode z systemem innym niż przekazany do i z systemu operacyjnego musi translacji, który wiąże obciążenie.  

  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Obsługa formatu Unicode](../text/support-for-unicode.md)