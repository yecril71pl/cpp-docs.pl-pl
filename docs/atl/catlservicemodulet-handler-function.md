---
title: Funkcja CAtlServiceModuleT::Handler
ms.date: 11/04/2016
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: fffdeddce7f3fa27d798ea7abafe85c9a13d9d97
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815544"
---
# <a name="catlservicemodulethandler-function"></a>Funkcja CAtlServiceModuleT::Handler

`CAtlServiceModuleT::Handler` jest procedury, która wywołuje Menedżera sterowania usługami (SCM), można pobrać stanu usługi i nadaj mu różne instrukcje (na przykład zatrzymanie lub wstrzymanie). Menedżer sterowania usługami przekazuje kod operacji do `Handler` do wskazania, co należy zrobić. Domyślna usługa generowane ATL obsługuje tylko instrukcji zatrzymania. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje Menedżer sterowania usługami, program zostanie zatrzymana. Następnie wywołuje usługę `PostThreadMessage` publikować komunikat o sobie. To kończy pętli komunikatów, a usługa ostatecznie zostanie zamknięte.

Aby obsłużyć więcej instrukcji, musisz zmienić `m_status` zainicjować dane składowej w `CAtlServiceModuleT` konstruktora. Ten element członkowski danych informuje Menedżer sterowania usługami, które przyciski, aby umożliwić wybranie usługi w aplikacji Panelu sterowania usługami.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
