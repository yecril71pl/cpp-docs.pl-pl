---
title: Commandhandler — obiekt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5a4d4c359fb4a90bfd25801f7c73f5bc4d7d501
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019474"
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

## <a name="see-also"></a>Zobacz też

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

