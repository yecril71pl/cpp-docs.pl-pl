---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: 65a8ce08e4f8606f168b101aa4daba23ef541051
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168673"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`jest nazwą funkcji identyfikowanej przez drugi parametr makra MESSAGE_HANDLER w mapie wiadomości.

## <a name="syntax"></a>Składnia

```cpp
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
Mapa komunikatów ustawia *bHandled* na wartość true przed `MessageHandler` wywołaniem. Jeśli `MessageHandler` komunikat nie jest w pełni obsługiwany, należy ustawić *bHandled* na wartość false, aby wskazać, że komunikat musi zostać przetworzony.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.

## <a name="remarks"></a>Uwagi

Przykład użycia tego programu obsługi komunikatów w mapie komunikatów znajduje się w temacie [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
