---
title: "Informacje o formantach ATL: Klasy obsługi ogólne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.controls
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6164fc5cb25c724cf8999c3e6f3f2d71ade0589
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="controls-general-support-classes"></a>Kontrolki: Klasy obsługi ogólne
Następujące klasy zapewniają ogólne obsługę formantów ATL:  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) składa się z pomocy funkcji i danych elementów członkowskich, które są niezbędne do kontrolek ALT.  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) udostępnia metody wymagane dla formantów.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) udostępnia metody głównej za pomocą których kontener komunikuje się z formantem. Zarządza Aktywacja i dezaktywacja formantów w miejscu.  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) łączy inicjowania do pojedynczego wywołanie w celu ułatwienia kontenery uniknąć opóźnienia podczas ładowania kontrolki.  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) zapewnia interakcji z myszą minimalnego dla formantu w przeciwnym razie nieaktywne.  
  
## <a name="sample-program"></a>Przykładowy Program  
 [ATLFire](../visual-cpp-samples.md)  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [ALT — samouczek](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)

