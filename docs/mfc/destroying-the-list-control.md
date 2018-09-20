---
title: Likwidowanie kontrolki listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25642357e3dd9117ae2817307ed5fa3c4a0921d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424545"
---
# <a name="destroying-the-list-control"></a>Likwidowanie kontrolki listy

W przypadku osadzenia swoje [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu jako element członkowski danych widoku lub w oknie dialogowym klasy jest niszczony, kiedy niszczony jest jego właścicielem. Jeśli używasz [CListView](../mfc/reference/clistview-class.md), struktura niszczy kontrolki, gdy niszczone widoku.

Można zorganizować dla niektórych danych listy mają być przechowywane w aplikacji, a nie kontrolki listy należy zorganizować jego dezalokacji. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Ponadto użytkownik jest odpowiedzialny dealokowanie żadnych list obrazów, utworzona i skojarzona z obiekt formantu listy.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

