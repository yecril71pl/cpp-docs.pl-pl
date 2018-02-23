---
title: MessageHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7247868f85a30cbecef416c690f181f068f7eaf2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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

