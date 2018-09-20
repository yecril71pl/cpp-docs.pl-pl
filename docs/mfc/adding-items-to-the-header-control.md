---
title: Dodawanie elementów do formantu nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0eb06a15cac87b063ada1cbe8f130b3464be0b0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447183"
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka

Po utworzeniu kontrolki nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) w okna nadrzędnego, Dodaj tyle nagłówek "items" według potrzeb: zazwyczaj jedna według kolumny.

### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka

1. Przygotowanie [HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.

1. Wywołaj [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), przekazywanie struktury.

1. Powtórz kroki 1 i 2 dla dodatkowych elementów.

Aby uzyskać więcej informacji, zobacz [dodanie elementu do kontrolki nagłówka o](/windows/desktop/Controls/header-controls) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

