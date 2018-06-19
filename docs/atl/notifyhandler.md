---
title: NotifyHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74fbdd99c162b4362339d8c1b45ddc281d30eeee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356456"
---
# <a name="notifyhandler"></a>NotifyHandler
Nazwa funkcji identyfikowane przez trzeci parametr funkcji `NOTIFY_HANDLER` makra mapy wiadomości.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 `idCtrl`  
 Identyfikator formantu wysyłania wiadomości.  
  
 *pnmh*  
 Adres [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) strukturę, która zawiera kod powiadomienia i dodatkowe informacje. Niektóre komunikaty powiadomień, ten parametr wskazuje większej struktury, która ma **NMHDR** struktury jako swojego pierwszego elementu członkowskiego.  
  
 `bHandled`  
 Ustawia mapy komunikatów `bHandled` do **TRUE** przed *NotifyHandler* jest wywoływana. Jeśli *NotifyHandler* nie obsługuje pełni komunikatu, należy ją ustawić `bHandled` do **FALSE** wskazująca wiadomość wymaga dalsze przetwarzanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania komunikatów. 0 w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład za pomocą tej obsługi wiadomości w mapie komunikatów, zobacz [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)   
 [Mapy komunikatów](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

