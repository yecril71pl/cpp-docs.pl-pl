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
ms.openlocfilehash: fc533046695db409067ff603e30cedbe11ad5ca4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953560"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa
Gdy zmieni się zaznaczenie z jednego elementu na inny formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) i [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) komunikaty powiadomień. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcie myszą lub naciśnięcie klawisza. Powiadomienia obejmują również informacji na temat elementu, który jest uzyskanie zaznaczenie i elementu, który jest utraty zaznaczenia. Można ustawić atrybutów elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na `TVN_SELCHANGING` uniemożliwia wybór z zmiana; zwracanie **FALSE** umożliwia zmianę.  
  
 Aplikację można zmienić wybór, wywołując [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

