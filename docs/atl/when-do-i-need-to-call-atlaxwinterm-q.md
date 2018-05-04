---
title: Jeśli trzeba wywołać AtlAxWinTerm? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61830023d3fb67d331784769f32cda4eee8355b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Jeśli trzeba wywołać AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowuje **"AtlAxWin80"** klasy okna. Powinny wywoływać tej funkcji (Jeśli nie trzeba tworzyć hosta z systemem windows), po wszystkich istniejących windows hosta zostały zniszczone. Nie można wywołać tej funkcji, klasę okna zostanie wyrejestrowane automatycznie gdy zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinInit  
[Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

