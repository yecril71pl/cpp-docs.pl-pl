---
title: "Jeśli trzeba wywołać AtlAxWinTerm? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c52c5295108ef01dc23ea9f945850e91a9806d6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Jeśli trzeba wywołać AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowuje **"AtlAxWin80"** klasy okna. Powinny wywoływać tej funkcji (Jeśli nie trzeba tworzyć hosta z systemem windows), po wszystkich istniejących windows hosta zostały zniszczone. Nie można wywołać tej funkcji, klasę okna zostanie wyrejestrowane automatycznie gdy zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinInit  
[Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

