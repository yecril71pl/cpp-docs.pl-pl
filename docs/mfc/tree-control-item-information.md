---
title: Informacje o elementach formantu drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 724e9d7c4e0ee7db80f024c30e363612cb40fed1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385368"
---
# <a name="tree-control-item-information"></a>Informacje o elementach kontrolki drzewa
Kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) oferują szereg funkcji elementów członkowskich, które pobrać informacji na temat elementów w formancie. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) funkcji członkowskiej pobiera niektóre lub wszystkie dane skojarzone z elementem. Dane te mogą obejmować tekstu elementu, stan, obrazów, liczbę elementów podrzędnych i wartość zdefiniowane przez aplikację 32-bitowych danych. Istnieje również [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkcji, które mogą zostać umieszczone niektóre lub wszystkie dane skojarzone z elementem.  
  
 [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext), [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata), i [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) funkcje Członkowskie pobrania pojedynczych atrybutów element. Każda z tych funkcji ma odpowiednie zestaw funkcji do ustawiania atrybutów elementu.  
  
 [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) funkcji członkowskiej pobiera elementu formantu drzewa, który posiada określonej relacji do bieżącego elementu. Tej funkcji można pobrać elementu nadrzędnego, poprzedniego lub następnego elementu widoczne, pierwszy element podrzędny i tak dalej. Dostępne są także funkcje Członkowskie przechodzenia drzewa: [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), i [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).  
  
 [GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) funkcji członkowskiej pobiera prostokąt ograniczający dla elementu formantu drzewa. [GetCount](../mfc/reference/ctreectrl-class.md#getcount) i [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) funkcje Członkowskie pobrać liczbę elementów w formancie drzewa oraz liczbę elementów, które są widoczne w oknie kontrolki drzewa, odpowiednio. Można upewnij się, że danego elementu jest widoczny, wywołując [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

