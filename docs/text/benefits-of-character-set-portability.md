---
title: Zalety znak przenośności zestawu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="benefits-of-character-set-portability"></a>Zalety przenośności zestawu znaków
Możesz mogą korzystać z funkcji środowiska wykonawczego przenośność MFC i C nawet wtedy, gdy użytkownik nie jest obecnie planowane internationalize aplikacji:  
  
-   Kodowanie portably sprawia, że kod podstawowa elastyczne. Można później przenieść go łatwo Unicode lub MBCS.  
  
-   Przy użyciu Unicode spowoduje, że aplikacje dla systemu Windows większą wydajność. Ponieważ system Windows używa Unicode, ciągów Unicode z systemem innym niż przekazany do i z systemu operacyjnego musi translacji, który wiąże obciążenie.  

  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Obsługa formatu Unicode](../text/support-for-unicode.md)