---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 16fb330d2da83ddfd013e33a2d4b688b2711103b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492305"
---
# <a name="notifyhandler"></a>NotifyHandler

Nazwa funkcji identyfikowanej przez trzeci parametr makra NOTIFY_HANDLER w mapie wiadomości.

## <a name="syntax"></a>Składnia

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*idCtrl*<br/>
Identyfikator kontrolki wysyłającej wiadomość.

*pnmh*<br/>
Adres struktury [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) , która zawiera kod powiadomienia i dodatkowe informacje. W przypadku niektórych komunikatów powiadomień ten parametr wskazuje większą strukturę, która ma `NMHDR` strukturę jako pierwszy element członkowski.

*bHandled*<br/>
Mapa komunikatów ustawia *bHandled* na true przed wywołaniem *NotifyHandler* . Jeśli *NotifyHandler* nie obsługuje w pełni komunikatu, należy ustawić **wartość false** dla *bHandled* , aby wskazać, że komunikat musi zostać przetworzony.

## <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.

## <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem użycia tego programu obsługi komunikatów w mapie komunikatów, zobacz [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Zobacz także

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
