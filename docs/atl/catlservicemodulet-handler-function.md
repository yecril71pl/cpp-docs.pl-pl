---
title: Funkcja CAtlServiceModuleT::Handler
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: 74c52e07f5be4ac16c8f9a20115a623c53f46090
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553689"
---
# <a name="catlservicemodulethandler-function"></a>Funkcja CAtlServiceModuleT::Handler

`CAtlServiceModuleT::Handler` jest procedury, która wywołuje Menedżera sterowania usługami (SCM), można pobrać stanu usługi i nadaj mu różne instrukcje (na przykład zatrzymanie lub wstrzymanie). Menedżer sterowania usługami przekazuje kod operacji do `Handler` do wskazania, co należy zrobić. Domyślna usługa generowane ATL obsługuje tylko instrukcji zatrzymania. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje Menedżer sterowania usługami, program zostanie zatrzymana. Następnie wywołuje usługę `PostThreadMessage` publikować komunikat o sobie. To kończy pętli komunikatów, a usługa ostatecznie zostanie zamknięte.

Aby obsłużyć więcej instrukcji, musisz zmienić `m_status` zainicjować dane składowej w `CAtlServiceModuleT` konstruktora. Ten element członkowski danych informuje Menedżer sterowania usługami, które przyciski, aby umożliwić wybranie usługi w aplikacji Panelu sterowania usługami.

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

