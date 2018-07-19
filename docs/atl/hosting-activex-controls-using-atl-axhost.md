---
title: Hosting kontrolek ActiveX przy użyciu ATL AXHost | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e26fd9e80b96c2b0196e3fd0e11b9c97f0f3bff3
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027209"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hosting kontrolek ActiveX przy użyciu ATL AXHost
Przykład w tym temacie pokazano, jak utworzyć AXHost oraz jak do hostowania kontrolki ActiveX przy użyciu różnych funkcji biblioteki ATL. Zawiera również instrukcje zdarzenia sink i kontroli dostępu (przy użyciu [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z formantu, który znajduje się. Przykład obsługuje formant kalendarza w głównym oknie lub okna podrzędnego.  
  
 Zwróć uwagę, definicji symbolu USE_METHOD. Możesz zmienić wartość tego symbolu będzie się różnić od 1 do 8. Wartość symbolu określa sposób tworzenia kontrolki:  
  
-   Parzystych wartości USE_METHOD, wywołanie w celu utworzenia podklasy hosta okna i konwertuje je do hosta kontroli. W przypadku wartości nieparzystą kod tworzy okno podrzędne, który działa jako host.  
  
-   Dla wartości USE_METHOD od 1 do 4, uzyskać dostęp do formantu i wychwytywania zdarzeń są wykonywane w wywołaniu, wzrasta, powstaje hosta. Wartości z zakresu od 5 do 8 zapytania hosta dla interfejsów i podłączyć ujścia.  
  
Poniżej przedstawiono podsumowanie:  
  
|USE_METHOD|Host|Kontrola dostępu i wychwytywania zdarzeń|Pokazano — funkcja|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Okno podrzędne|Jeden krok|CreateControlLicEx|  
|2|Okno główne|Jeden krok|AtlAxCreateControlLicEx|  
|3|Okno podrzędne|Jeden krok|CreateControlEx|  
|4|Okno główne|Jeden krok|AtlAxCreateControlEx|  
|5|Okno podrzędne|Wiele kroków|CreateControlLic|  
|6|Okno główne|Wiele kroków|AtlAxCreateControlLic|  
|7|Okno podrzędne|Wiele kroków|CreateControl —|  
|8|Okno główne|Wiele kroków|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [Klasa CAxWindow2T](../atl/reference/caxwindow2t-class.md)   
 [Interfejs IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)

