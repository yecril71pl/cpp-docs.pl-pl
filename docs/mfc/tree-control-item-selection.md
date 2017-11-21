---
title: "Wybór elementu formantu drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fac551ed757cf0510f0a8b61522bc969c6b6be6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa
Gdy zmieni się zaznaczenie z jednego elementu na inny formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) i [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) komunikaty powiadomień. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcie myszą lub naciśnięcie klawisza. Powiadomienia obejmują również informacji na temat elementu, który jest uzyskanie zaznaczenie i elementu, który jest utraty zaznaczenia. Można ustawić atrybutów elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na **TVN_SELCHANGING** uniemożliwia wybór z zmiana; zwracanie **FALSE** umożliwia zmianę.  
  
 Aplikację można zmienić wybór, wywołując [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Formanty](../mfc/controls-mfc.md)

