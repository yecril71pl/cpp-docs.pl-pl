---
title: Jeśli trzeba wywołać AtlAxWinInit? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9aa1dd14ccae555d4ab9acbbac15e9b66cafe6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Jeśli trzeba wywołać AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje **"AtlAxWin80"** okna klasy (oraz kilka niestandardowych komunikatów okien), dlatego ta funkcja musi być wywołana przed próbą utworzenia okna hosta. Jednak nie należy zawsze jawnie, wywołanie tej funkcji, ponieważ hostowania interfejsów API (i klasy, które z nich korzystają) często wymagają tej funkcji. Nie powoduje żadnych problemów w wywołaniu tej funkcji w więcej niż raz. .  
  
## <a name="see-also"></a>Zobacz też  
 Jeśli trzeba wywołać AtlAxWinTerm     
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)
