---
title: Style formantu postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b29d0df8342ce00a2ddb0d46970d9504a06edd8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956684"
---
# <a name="styles-for-the-progress-control"></a>Style formantu postępu
Utworzenie początkowo formantu postępu ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), użyj *dwStyle* parametr, aby określić żądaną okna Style formantu postępu. Poniższa lista zawiera szczegóły style odpowiednie okna. Formant ignoruje wszystkie styl okna innych niż wymienione w tym miejscu. Należy zawsze twórz formant jako okna podrzędnego, zazwyczaj z nadrzędnego — okno dialogowe.  
  
|Styl okna|Efekt|  
|------------------|------------|  
|WS_BORDER —|Tworzy obramowanie okna.|  
|WS_CHILD —|Tworzy okno podrzędne (zawsze powinna być używana do `CProgressCtrl`).|  
|WS_CLIPCHILDREN —|Wyklucza obszar okien podrzędnych podczas rysowania okna nadrzędnego. Używane podczas tworzenia okna nadrzędnego.|  
|WS_CLIPSIBLINGS —|Okno podrzędne klipy względem siebie.|  
|WS_DISABLED —|Tworzy okno, które jest początkowo wyłączone.|  
|WS_VISIBLE —|Tworzy okno, która jest widoczna od początku.|  
|WS_TABSTOP —|Określa, czy formant może odebrać fokus, gdy użytkownik naciśnie klawisz TAB, aby przenieść do niego.|  
  
 Ponadto można określić dwa style, które mają zastosowanie tylko do formantu postępu pbs_vertical — i pbs_smooth —.  
  
 Pbs_vertical — umożliwia Orientacja formantu w pionie, a nie w poziomie. Pbs_smooth — umożliwia wypełnienia kontrolki całkowicie, zamiast wyświetlanie małych kwadratów nakreślono, które przyrostowo wypełnienia kontrolki.  
  
 Bez pbs_smooth — styl:  
  
 ![Style paska postępu standardowe](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 Przy użyciu stylów pbs_smooth — i pbs_vertical —:  
  
 ![Postęp stylu, płynne i pionowego paska](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 Aby uzyskać więcej informacji, zobacz [Style okna](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) w *odwołania MFC*.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)

