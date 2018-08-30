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
ms.openlocfilehash: 1ad124f0819dbfd9cfd0117cb91fbcffba05a400
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201279"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` czy funkcja jest identyfikowana przez trzeci parametr makra COMMAND_HANDLER na mapie komunikatów.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 *wNotifyCode*  
 Kod powiadomienia.  
  
 *wID*  
 Identyfikator elementu menu, formant lub klawiszy skrótów.  
  
 *hWndCtl*  
 Dojście do kontrolki okna.  
  
 *bHandled*  
 Ustawia mapy wiadomości *bHandled* na wartość TRUE, przed `CommandHandler` jest wywoływana. Jeśli `CommandHandler` nie obsługuje w pełni komunikat, należy ją ustawić *bHandled* na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania wiadomości. 0, jeśli kończy się pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać przykład korzystania z tej obsługi wiadomości w mapie komunikatów, zobacz [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)   
 [Mapy komunikatów](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

