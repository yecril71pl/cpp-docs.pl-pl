---
title: Hosting formantów za pomocą biblioteki ATL AXHost | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5057a077e8e778fa3d943b736d51d19af8f60fc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hosting formantów za pomocą ATL AXHost
Próbki w tym temacie przedstawiono sposób tworzenia AXHost oraz sposobu hostowania formantu ActiveX, przy użyciu różnych funkcji ATL. Przedstawiono również sposób zdarzeń odbioru i kontroli dostępu (przy użyciu [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z formantu, który jest obsługiwany. Przykład obsługuje formant kalendarza w głównym oknie lub okna podrzędnego.  
  
 Zwróć uwagę, definicji `USE_METHOD` symbolu. Można zmienić wartość tego symbolu do różnią się od 1 do 8. Wartość symbolu określa sposób tworzenia kontrolki:  
  
-   Dla wartości parzystych `USE_METHOD`, wywołanie w celu utworzenia podklasy hosta okna i konwertuje ją na hosta formantu. Nieparzystą wartości kod tworzy okno podrzędne, który działa jako hosta.  
  
-   Dla wartości `USE_METHOD` od 1 do 4 dostępu do formantu i wychwytywanie zdarzeń są wykonywane w wywołaniu, które tworzy także hosta. Wartości od 5 do 8 zapytania hosta dla interfejsów i utworzenie punktu zaczepienia sink.  
  
 Poniżej przedstawiono podsumowanie:  
  
|USE_METHOD|Host|Kontrola dostępu i wychwytywanie zdarzeń|Przedstawiona — funkcja|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Okno podrzędne|Krok|CreateControlLicEx|  
|2|Okno główne|Krok|AtlAxCreateControlLicEx|  
|3|Okno podrzędne|Krok|CreateControlEx|  
|4|Okno główne|Krok|AtlAxCreateControlEx|  
|5|Okno podrzędne|Wiele kroków|CreateControlLic|  
|6|Okno główne|Wiele kroków|AtlAxCreateControlLic|  
|7|Okno podrzędne|Wiele kroków|CreateControl|  
|8|Okno główne|Wiele kroków|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [Klasa CAxWindow2T](../atl/reference/caxwindow2t-class.md)   
 [Interfejs IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)

