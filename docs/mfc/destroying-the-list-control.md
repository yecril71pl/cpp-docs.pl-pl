---
title: Likwidowanie formantu listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 963da9e6db2f0fe063dee1ca19ab23f545ed5e76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392892"
---
# <a name="destroying-the-list-control"></a>Likwidowanie formantu listy

W przypadku osadzenia swoje [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu jako element członkowski danych widoku lub w oknie dialogowym klasy jest niszczony, kiedy niszczony jest jego właścicielem. Jeśli używasz [CListView](../mfc/reference/clistview-class.md), struktura niszczy kontrolki, gdy niszczone widoku.

Można zorganizować dla niektórych danych listy mają być przechowywane w aplikacji, a nie kontrolki listy należy zorganizować jego dezalokacji. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Ponadto użytkownik jest odpowiedzialny dealokowanie żadnych list obrazów, utworzona i skojarzona z obiekt formantu listy.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
