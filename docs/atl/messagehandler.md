---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageHandler
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: deb217e2f889d30ab5c4caa7d9812d5e612dcb62
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299351"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` jest nazwą funkcji identyfikowane przez drugi parametr makra MESSAGE_HANDLER na mapie komunikatów.

## <a name="syntax"></a>Składnia

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
Określa komunikat.

*wParam*<br/>
Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
Dodatkowe informacje specyficzne dla wiadomości.

*bHandled*<br/>
Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed `MessageHandler` jest wywoływana. Jeśli `MessageHandler` nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.

## <a name="remarks"></a>Uwagi

Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
