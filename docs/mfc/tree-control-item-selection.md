---
title: Wybór elementu kontrolki drzewa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fd6632a44dd4806b8f13683b50cad76b5eebe27a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212584"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa
Gdy zmieni się zaznaczenie z jednego elementu do innej kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) i [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) wiadomości z powiadomieniami. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcia lub naciśnięcia klawisza. Powiadomienia obejmują także informacji na temat elementu, który zyskuje zaznaczenie i element, który jest utraty zaznaczenia. Można ustawić atrybuty elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na `TVN_SELCHANGING` zapobiega wybór Zmienianie; zwracanie **FALSE** umożliwia zmianę.  
  
 Aplikację można zmienić wybór, wywołując [selectitem —](../mfc/reference/ctreectrl-class.md#selectitem) funkcja elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

