---
title: "Style formantu postępu | Dokumentacja firmy Microsoft"
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
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6186372dc3ac8bc1000a71706971c9ff72078c5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="styles-for-the-progress-control"></a>Style formantu postępu
Utworzenie początkowo formantu postępu ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), użyj `dwStyle` parametr, aby określić żądaną okna Style formantu postępu. Poniższa lista zawiera szczegóły style odpowiednie okna. Formant ignoruje wszystkie styl okna innych niż wymienione w tym miejscu. Należy zawsze twórz formant jako okna podrzędnego, zazwyczaj z nadrzędnego — okno dialogowe.  
  
|Styl okna|Efekt|  
|------------------|------------|  
|`WS_BORDER`|Tworzy obramowanie okna.|  
|**WS_CHILD —**|Tworzy okno podrzędne (zawsze powinna być używana do `CProgressCtrl`).|  
|**WS_CLIPCHILDREN —**|Wyklucza obszar okien podrzędnych podczas rysowania okna nadrzędnego. Używane podczas tworzenia okna nadrzędnego.|  
|**WS_CLIPSIBLINGS —**|Okno podrzędne klipy względem siebie.|  
|**WS_DISABLED —**|Tworzy okno, które jest początkowo wyłączone.|  
|**WS_VISIBLE —**|Tworzy okno, która jest widoczna od początku.|  
|**WS_TABSTOP —**|Określa, czy formant może odebrać fokus, gdy użytkownik naciśnie klawisz TAB, aby przenieść do niego.|  
  
 Ponadto można określić dwa style, które mają zastosowanie tylko do formantu postępu `PBS_VERTICAL` i `PBS_SMOOTH`.  
  
 Użyj `PBS_VERTICAL` do Orientacja formantu w pionie, a nie w poziomie. Użyj `PBS_SMOOTH` do wypełnienia kontrolki całkowicie, zamiast wyświetlanie małych kwadratów nakreślono, które przyrostowo wypełnienia kontrolki.  
  
 Bez `PBS_SMOOTH` stylu:  
  
 ![Style paska postępu standardowe](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 Z `PBS_SMOOTH` i `PBS_VERTICAL` style:  
  
 ![Postęp stylu, płynne i pionowego paska](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 Aby uzyskać więcej informacji, zobacz [Style okna](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) w *odwołania MFC*.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)

