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
ms.openlocfilehash: ec0fd88def88f7d31fce078fec0c860f4f21f51c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356370"
---
# <a name="messagehandler"></a>MessageHandler
**MessageHandler** jest nazwą funkcji identyfikowane przez drugi parametr funkcji `MESSAGE_HANDLER` makra mapy wiadomości.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
    LRESULT 
    MessageHandler 
 (
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 `uMsg`  
 Określa komunikat.  
  
 `wParam`  
 Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 Dodatkowe informacje specyficzne dla wiadomości.  
  
 `bHandled`  
 Ustawia mapy komunikatów `bHandled` do **TRUE** przed `MessageHandler` jest wywoływana. Jeśli `MessageHandler` nie obsługuje pełni komunikatu, należy ją ustawić `bHandled` do **FALSE** wskazująca wiadomość wymaga dalsze przetwarzanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład za pomocą tej obsługi wiadomości w mapie komunikatów, zobacz [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)   
 [Mapy komunikatów](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

