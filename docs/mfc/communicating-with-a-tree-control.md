---
title: Komunikacja z formantem drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: f480cdad2fce53f830b8067083a8a4be4b4e4848
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619645"
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z formantem drzewa

Używasz różnych metod wywoływania funkcji Członkowskich w obiekcie [CTreeCtrl](reference/ctreectrl-class.md) w zależności od sposobu utworzenia obiektu:

- Jeśli formant drzewa znajduje się w oknie dialogowym, użyj zmiennej składowej typu `CTreeCtrl` , która została utworzona w klasie okna dialogowego.

- Jeśli formant drzewa jest oknem podrzędnym, użyj `CTreeCtrl` obiektu (lub wskaźnika) użytego do konstruowania obiektu.

- Jeśli używasz `CTreeView` obiektu, użyj funkcji [CTreeView:: funkcji GetTreeCtrl](reference/ctreeview-class.md#gettreectrl) , aby pobrać odwołanie do kontrolki drzewa. Możesz zainicjować inne odwołanie z tą wartością lub przypisać adres odwołania do `CTreeCtrl` wskaźnika.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](using-ctreectrl.md)<br/>
[Formanty](controls-mfc.md)
