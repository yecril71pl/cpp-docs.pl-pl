---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 292a1c6606585dc0694ee678ba8bc9b5fbc42681
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808225"
---
# <a name="notifyhandler"></a>NotifyHandler

Nazwa funkcji identyfikowane przez trzeci parametr makra NOTIFY_HANDLER na mapie komunikatów.

## <a name="syntax"></a>Składnia

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*idCtrl*<br/>
Identyfikator formantu wysyłania komunikatu.

*pnmh*<br/>
Adres [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) strukturę, która zawiera kod powiadomienia i dodatkowe informacje. Niektóre komunikaty powiadomień, ten parametr wskazuje większej struktury, która ma `NMHDR` struktury jako swojego pierwszego elementu członkowskiego.

*bHandled*<br/>
Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed *NotifyHandler* jest wywoływana. Jeśli *NotifyHandler* nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* do **FALSE** do wskazania wiadomość wymaga dalszego przetwarzania.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.

## <a name="remarks"></a>Uwagi

Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
