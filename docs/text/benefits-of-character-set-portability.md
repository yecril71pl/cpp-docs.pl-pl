---
title: "Zalety znak przenośności zestawu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 93bd0356e8e2192e44053c9090ffb63ea72cfeca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="benefits-of-character-set-portability"></a>Zalety przenośności zestawu znaków
Możesz mogą korzystać z funkcji środowiska wykonawczego przenośność MFC i C nawet wtedy, gdy użytkownik nie jest obecnie planowane internationalize aplikacji:  
  
-   Kodowanie portably sprawia, że kod podstawowa elastyczne. Można później przenieść go łatwo Unicode lub MBCS.  
  
-   Przy użyciu Unicode spowoduje, że aplikacje dla systemu Windows 2000 większą wydajność. Ponieważ system Windows 2000 używa Unicode, ciągów Unicode z systemem innym niż przekazany do i z systemu operacyjnego musi translacji, który wiąże obciążenie.  
  
-   Przy użyciu MBCS umożliwia obsługę rynkach międzynarodowych na platformach Win32 innych niż Windows 2000, takich jak system operacyjny Windows 95 lub Windows 98.  
  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Obsługa formatu Unicode](../text/support-for-unicode.md)