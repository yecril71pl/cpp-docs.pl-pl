---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 743be3e0bc9cc96fc6b22d0806d399ab5e160a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235067"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` czy funkcja jest identyfikowana przez trzeci parametr makra COMMAND_HANDLER na mapie komunikatów.

## <a name="syntax"></a>Składnia

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia.

*wID*<br/>
Identyfikator elementu menu, formant lub klawiszy skrótów.

*hWndCtl*<br/>
Dojście do kontrolki okna.

*bHandled*<br/>
Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed `CommandHandler` jest wywoływana. Jeśli `CommandHandler` nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.

## <a name="remarks"></a>Uwagi

Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
