---
title: Komunikacja z kontrolką drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78bb6a6d6421a5336f8efbffc7d24a6121e208e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432157"
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z kontrolką drzewa

Możesz użyć różnych metod wywoływania funkcji elementów członkowskich [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiekt, w zależności od sposobu utworzenia obiektu:

- Jeśli kontrolka drzewa w oknie dialogowym, użyj zmiennej składowej typu `CTreeCtrl` utworzony w klasie okno dialogowe.

- Jeśli formant drzewa jest oknem podrzędnym, użyj `CTreeCtrl` obiektu (lub wskaźnik) użyty do utworzenia obiekt.

- Jeśli używasz `CTreeView` obiektu, należy użyć funkcji [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) można pobrać odwołania do formantu drzewa. Możesz zainicjować innego odwołania o tej wartości lub przypisać adres odwołania do `CTreeCtrl` wskaźnika.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

