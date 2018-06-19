---
title: Wybór elementu formantu drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb08fcbb1bd77cc80fdbe014d8c9e8a0851254d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385901"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa
Gdy zmieni się zaznaczenie z jednego elementu na inny formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) i [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) komunikaty powiadomień. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcie myszą lub naciśnięcie klawisza. Powiadomienia obejmują również informacji na temat elementu, który jest uzyskanie zaznaczenie i elementu, który jest utraty zaznaczenia. Można ustawić atrybutów elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na **TVN_SELCHANGING** uniemożliwia wybór z zmiana; zwracanie **FALSE** umożliwia zmianę.  
  
 Aplikację można zmienić wybór, wywołując [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

