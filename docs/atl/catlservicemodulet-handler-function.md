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
ms.openlocfilehash: dbc7c74e0fd6fdd34ba9a0c386c028469113c88e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767089"
---
# <a name="catlservicemodulethandler-function"></a>Funkcja CAtlServiceModuleT::Handler

`CAtlServiceModuleT::Handler` jest procedury, która wywołuje Menedżera sterowania usługami (SCM), można pobrać stanu usługi i nadaj mu różne instrukcje (na przykład zatrzymanie lub wstrzymanie). Menedżer sterowania usługami przekazuje kod operacji do `Handler` do wskazania, co należy zrobić. Domyślna usługa generowane ATL obsługuje tylko instrukcji zatrzymania. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje Menedżer sterowania usługami, program zostanie zatrzymana. Następnie wywołuje usługę `PostThreadMessage` publikować komunikat o sobie. To kończy pętli komunikatów, a usługa ostatecznie zostanie zamknięte.

Aby obsłużyć więcej instrukcji, musisz zmienić `m_status` zainicjować dane składowej w `CAtlServiceModuleT` konstruktora. Ten element członkowski danych informuje Menedżer sterowania usługami, które przyciski, aby umożliwić wybranie usługi w aplikacji Panelu sterowania usługami.

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)   
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

