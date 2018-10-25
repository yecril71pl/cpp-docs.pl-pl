---
title: MessageHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0c7d76ff3b1e05d482b365150c9072a9fdd8d5c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076714"
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

## <a name="see-also"></a>Zobacz też

[Implementowanie okna](../atl/implementing-a-window.md)<br/>
[Mapy komunikatów](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)
