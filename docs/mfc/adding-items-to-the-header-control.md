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
ms.openlocfilehash: a6450d99b8df436c64337e52fc14244ecbb0edfc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206150"
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka
Po utworzeniu kontrolki nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) w okna nadrzędnego, Dodaj tyle nagłówek "items" według potrzeb: zazwyczaj jedna według kolumny.  
  
### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka  
  
1.  Przygotowanie [HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.  
  
2.  Wywołaj [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), przekazywanie struktury.  
  
3.  Powtórz kroki 1 i 2 dla dodatkowych elementów.  
  
 Aby uzyskać więcej informacji, zobacz [dodanie elementu do kontrolki nagłówka o](/windows/desktop/Controls/header-controls) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

