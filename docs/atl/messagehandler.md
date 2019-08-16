---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492312"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`jest nazwą funkcji identyfikowanej przez drugi parametr makra MESSAGE_HANDLER w mapie wiadomości.

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
Mapa komunikatów ustawia *bHandled* na wartość true przed `MessageHandler` wywołaniem. Jeśli `MessageHandler` komunikat nie jest w pełni obsługiwany, należy ustawić *bHandled* na wartość false, aby wskazać, że komunikat musi zostać przetworzony.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.

## <a name="remarks"></a>Uwagi

Przykład użycia tego programu obsługi komunikatów w mapie komunikatów można znaleźć w temacie [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
