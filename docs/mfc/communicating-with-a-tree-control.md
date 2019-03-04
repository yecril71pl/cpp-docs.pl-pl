---
title: Komunikacja z formantem drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 920608724ebb362b91efdcb3eab50b80acd20474
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289887"
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z formantem drzewa

Możesz użyć różnych metod wywoływania funkcji elementów członkowskich [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiekt, w zależności od sposobu utworzenia obiektu:

- Jeśli kontrolka drzewa w oknie dialogowym, użyj zmiennej składowej typu `CTreeCtrl` utworzony w klasie okno dialogowe.

- Jeśli formant drzewa jest oknem podrzędnym, użyj `CTreeCtrl` obiektu (lub wskaźnik) użyty do utworzenia obiekt.

- Jeśli używasz `CTreeView` obiektu, należy użyć funkcji [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) można pobrać odwołania do formantu drzewa. Możesz zainicjować innego odwołania o tej wartości lub przypisać adres odwołania do `CTreeCtrl` wskaźnika.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
