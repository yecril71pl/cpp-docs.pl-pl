---
title: "Jeśli trzeba wywołać AtlAxWinTerm? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinTerm
dev_langs: C++
helpviewer_keywords: AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdba5255560f220a80a016f17e574721b12f486d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Jeśli trzeba wywołać AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowuje **"AtlAxWin80"** klasy okna. Powinny wywoływać tej funkcji (Jeśli nie trzeba tworzyć hosta z systemem windows), po wszystkich istniejących windows hosta zostały zniszczone. Nie można wywołać tej funkcji, klasę okna zostanie wyrejestrowane automatycznie gdy zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinInit  
[Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

