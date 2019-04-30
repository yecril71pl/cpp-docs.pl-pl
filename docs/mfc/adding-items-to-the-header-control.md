---
title: Dodawanie elementów do formantu nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 897612c6d5ac96704cc0a945df65146e6a01480a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394757"
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka

Po utworzeniu kontrolki nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) w okna nadrzędnego, Dodaj tyle nagłówek "items" według potrzeb: zazwyczaj jedna według kolumny.

### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka

1. Przygotowanie [HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.

1. Wywołaj [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), przekazywanie struktury.

1. Powtórz kroki 1 i 2 dla dodatkowych elementów.

Aby uzyskać więcej informacji, zobacz [dodanie elementu do kontrolki nagłówka o](/windows/desktop/Controls/header-controls) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
