---
title: Funkcja CAtlServiceModuleT::Handler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00158bbed5318d919c284b91cd651141a35bd441
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulethandler-function"></a>Funkcja CAtlServiceModuleT::Handler
`CAtlServiceModuleT::Handler`jest procedura, która wywołuje Menedżera sterowania usługami (SCM) można pobrać stanu usługi i nadaj mu różnych instrukcje (na przykład zatrzymanie lub wstrzymanie). Menedżer sterowania usługami przekazuje kod operacji `Handler` wskaż, jakie działanie ma wykonać usługi. Domyślna usługa wygenerowany ATL obsługuje tylko instrukcje stop. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje SCM program o zbliżającym się zatrzymać. Wywołuje usługę `PostThreadMessage` można wysłać komunikat o rezygnacji do samej siebie. To kończy pętlę komunikatów i usługa ostatecznie zostanie zamknięte.  
  
 Aby obsłużyć więcej instrukcji, musisz zmienić `m_status` zainicjować elementu członkowskiego danych w `CAtlServiceModuleT` konstruktora. Ten element członkowski danych informuje SCM, które przyciski umożliwiające wybranie usługę w aplikacji Panelu sterowania usługami.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

