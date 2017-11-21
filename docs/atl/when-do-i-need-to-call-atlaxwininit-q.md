---
title: "Jeśli trzeba wywołać AtlAxWinInit? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinInit
dev_langs: C++
helpviewer_keywords: AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ec7d8d15b8219071b593368ed539d92ff3c9032
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Jeśli trzeba wywołać AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje **"AtlAxWin80"** okna klasy (oraz kilka niestandardowych komunikatów okien), dlatego ta funkcja musi być wywołana przed próbą utworzenia okna hosta. Jednak nie należy zawsze jawnie, wywołanie tej funkcji, ponieważ hostowania interfejsów API (i klasy, które z nich korzystają) często wymagają tej funkcji. Nie powoduje żadnych problemów w wywołaniu tej funkcji w więcej niż raz. .  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinTerm     
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)
