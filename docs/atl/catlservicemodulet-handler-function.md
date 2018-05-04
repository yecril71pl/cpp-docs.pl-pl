---
title: Funkcja CAtlServiceModuleT::Handler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0c0386cd17e7a33628790520e356c706f9743b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemodulethandler-function"></a>Funkcja CAtlServiceModuleT::Handler
`CAtlServiceModuleT::Handler` jest procedura, która wywołuje Menedżera sterowania usługami (SCM) można pobrać stanu usługi i nadaj mu różnych instrukcje (na przykład zatrzymanie lub wstrzymanie). Menedżer sterowania usługami przekazuje kod operacji `Handler` wskaż, jakie działanie ma wykonać usługi. Domyślna usługa wygenerowany ATL obsługuje tylko instrukcje stop. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje SCM program o zbliżającym się zatrzymać. Wywołuje usługę `PostThreadMessage` można wysłać komunikat o rezygnacji do samej siebie. To kończy pętlę komunikatów i usługa ostatecznie zostanie zamknięte.  
  
 Aby obsłużyć więcej instrukcji, musisz zmienić `m_status` zainicjować elementu członkowskiego danych w `CAtlServiceModuleT` konstruktora. Ten element członkowski danych informuje SCM, które przyciski umożliwiające wybranie usługę w aplikacji Panelu sterowania usługami.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

