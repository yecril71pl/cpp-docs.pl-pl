---
title: "Komunikaty powiadomień dotyczących formantu drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e5044416ca38f6b3ead743c571ea7175022d51fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-notification-messages"></a>Komunikaty powiadomień dotyczących kontrolki drzewa
Formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła następujące komunikaty powiadomień jako **WM_NOTIFY** wiadomości:  
  
|Komunikat z powiadomieniem|Opis|  
|--------------------------|-----------------|  
|**TVN_BEGINDRAG**|Sygnalizuje uruchomienia operacji przeciągania i upuszczania|  
|**TVN_BEGINLABELEDIT**|Sygnalizuje początek Edytowanie etykiet w miejscu|  
|**TVN_BEGINRDRAG**|Sygnalizuje uruchomienia operacji przeciągania i upuszczania, za pomocą prawego przycisku myszy|  
|**TVN_DELETEITEM**|Sygnały usunięcia określonego elementu|  
|**TVN_ENDLABELEDIT**|Sygnalizuje koniec Edytowanie etykiet|  
|**TVN_GETDISPINFO**|Żąda informacji, że drzewie wymaga, aby wyświetlić elementy|  
|**TVN_ITEMEXPANDED**|Sygnały, że listy elementów podrzędnych elementu nadrzędnego został rozwinięte lub zwinięte|  
|**TVN_ITEMEXPANDING**|Sygnalizuje, że można rozwinięte lub zwinięte listy elementów podrzędnych elementu nadrzędnego|  
|**TVN_KEYDOWN**|Sygnały zdarzenia klawiatury|  
|**TVN_SELCHANGED**|Sygnalizuje, że zaznaczenie zostało zmienione z jednego elementu na inny|  
|**TVN_SELCHANGING**|Sygnalizuje, że zaznaczenie zostanie zmieniony z jednego elementu na inny|  
|**TVN_SETDISPINFO**|Powiadomienie, aby zaktualizować informacje dla elementu|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

