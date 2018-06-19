---
title: Co to jest obiekt hosta? (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d197f02949f6eaaeee50b428338684135d1db27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357737"
---
# <a name="what-is-a-host-object"></a>Co to jest obiekt hosta?
Obiekt hosta jest obiekt COM, który reprezentuje kontenera formantu ActiveX, które są dostarczane przez ATL dla poszczególnego okna. Obiekt hosta podklasy okna kontenera, aby go odzwierciedlają wiadomości do kontrolki, zapewnia interfejsy kontenera niezbędne do użycia przez formant i udostępnia ona [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) i [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfejsów, co pozwala na skonfigurowanie środowiska formantu.  
  
 Obiekt hosta służy do ustawiania właściwości otoczenia kontenera.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

