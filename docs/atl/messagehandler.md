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
ms.openlocfilehash: 74a5e50eae425340bcb0f9a455422b43db0be0b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207113"
---
# <a name="messagehandler"></a>MessageHandler
`MessageHandler` jest nazwą funkcji identyfikowane przez drugi parametr makra MESSAGE_HANDLER na mapie komunikatów.  
  
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
 *uMsg*  
 Określa komunikat.  
  
 *wParam*  
 Dodatkowe informacje specyficzne dla wiadomości.  
  
 *lParam*  
 Dodatkowe informacje specyficzne dla wiadomości.  
  
 *bHandled*  
 Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed `MessageHandler` jest wywoływana. Jeśli `MessageHandler` nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)   
 [Mapy komunikatów](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

