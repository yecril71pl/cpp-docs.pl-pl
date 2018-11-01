---
title: Komunikacja z kontrolką drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654191"
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z kontrolką drzewa

Możesz użyć różnych metod wywoływania funkcji elementów członkowskich [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiekt, w zależności od sposobu utworzenia obiektu:

- Jeśli kontrolka drzewa w oknie dialogowym, użyj zmiennej składowej typu `CTreeCtrl` utworzony w klasie okno dialogowe.

- Jeśli formant drzewa jest oknem podrzędnym, użyj `CTreeCtrl` obiektu (lub wskaźnik) użyty do utworzenia obiekt.

- Jeśli używasz `CTreeView` obiektu, należy użyć funkcji [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) można pobrać odwołania do formantu drzewa. Możesz zainicjować innego odwołania o tej wartości lub przypisać adres odwołania do `CTreeCtrl` wskaźnika.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

