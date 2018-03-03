---
title: "Jeśli trzeba wywołać AtlAxWinInit? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69dfcfbe0c8c05d275a5f3a8f86c30b0e59bd3a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Jeśli trzeba wywołać AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje **"AtlAxWin80"** okna klasy (oraz kilka niestandardowych komunikatów okien), dlatego ta funkcja musi być wywołana przed próbą utworzenia okna hosta. Jednak nie należy zawsze jawnie, wywołanie tej funkcji, ponieważ hostowania interfejsów API (i klasy, które z nich korzystają) często wymagają tej funkcji. Nie powoduje żadnych problemów w wywołaniu tej funkcji w więcej niż raz. .  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinTerm     
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)
