---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492455"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`jest funkcją identyfikowaną przez trzeci parametr makra COMMAND_HANDLER w mapie wiadomości.

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
Identyfikator elementu menu, kontrolki lub akceleratora.

*hWndCtl*<br/>
Uchwyt do kontrolki okna.

*bHandled*<br/>
Mapa komunikatów ustawia *bHandled* na wartość true przed `CommandHandler` wywołaniem. Jeśli `CommandHandler` komunikat nie jest w pełni obsługiwany, należy ustawić *bHandled* na wartość false, aby wskazać, że komunikat musi zostać przetworzony.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.

## <a name="remarks"></a>Uwagi

Przykład użycia tego programu obsługi komunikatów w mapie komunikatów można znaleźć w temacie [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
