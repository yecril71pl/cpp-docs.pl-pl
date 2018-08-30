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
ms.openlocfilehash: e39b0b1ac94a759c4a8b30fce8c634ed49be4ff9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209482"
---
# <a name="notifyhandler"></a>NotifyHandler
Nazwa funkcji identyfikowane przez trzeci parametr makra NOTIFY_HANDLER na mapie komunikatów.  
  
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
 *idCtrl*  
 Identyfikator formantu wysyłania komunikatu.  
  
 *pnmh*  
 Adres [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) strukturę, która zawiera kod powiadomienia i dodatkowe informacje. Niektóre komunikaty powiadomień, ten parametr wskazuje większej struktury, która ma `NMHDR` struktury jako swojego pierwszego elementu członkowskiego.  
  
 *bHandled*  
 Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed *NotifyHandler* jest wywoływana. Jeśli *NotifyHandler* nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* do **FALSE** do wskazania wiadomość wymaga dalszego przetwarzania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)   
 [Mapy komunikatów](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

