---
title: Co to jest obiekt hosta? (ATL) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da735caa84c133b9cdf63fae5df8bdd3d5f774b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-host-object"></a>Co to jest obiekt hosta?
Obiekt hosta jest obiekt COM, który reprezentuje kontenera formantu ActiveX, które są dostarczane przez ATL dla poszczególnego okna. Obiekt hosta podklasy okna kontenera, aby go odzwierciedlają wiadomości do kontrolki, zapewnia interfejsy kontenera niezbędne do użycia przez formant i udostępnia ona [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) i [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfejsów, co pozwala na skonfigurowanie środowiska formantu.  
  
 Obiekt hosta służy do ustawiania właściwości otoczenia kontenera.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

