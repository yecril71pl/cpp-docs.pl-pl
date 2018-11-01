---
title: Likwidowanie kontrolki listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 85089919ccb81003dad1eab439fa8a0d127fd9ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568353"
---
# <a name="destroying-the-list-control"></a>Likwidowanie kontrolki listy

W przypadku osadzenia swoje [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu jako element członkowski danych widoku lub w oknie dialogowym klasy jest niszczony, kiedy niszczony jest jego właścicielem. Jeśli używasz [CListView](../mfc/reference/clistview-class.md), struktura niszczy kontrolki, gdy niszczone widoku.

Można zorganizować dla niektórych danych listy mają być przechowywane w aplikacji, a nie kontrolki listy należy zorganizować jego dezalokacji. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Ponadto użytkownik jest odpowiedzialny dealokowanie żadnych list obrazów, utworzona i skojarzona z obiekt formantu listy.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

