---
title: Informacje o elementach kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: e0eb8af4fbbb6f59c0dda75ec3705183ce916350
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288899"
---
# <a name="tree-control-item-information"></a>Informacje o elementach kontrolki drzewa

Kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) oferują szereg funkcji elementów członkowskich, które pobierają informacje na temat elementów w formancie. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) funkcja elementu członkowskiego pobiera niektóre lub wszystkie dane skojarzone z elementem. Te dane mogą obejmować tekstu elementu, stan, obrazy, liczba elementów podrzędnych i wartością danych zdefiniowanych przez aplikację 32-bitowych. Istnieje również [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkcji, które można ustawić niektóre lub wszystkie dane skojarzone z elementem.

[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [getitemtext —](../mfc/reference/ctreectrl-class.md#getitemtext), [getitemdata —](../mfc/reference/ctreectrl-class.md#getitemdata), i [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) funkcji składowych pobierać poszczególne atrybuty element. Każda z tych funkcji ma funkcję odpowiedni zestaw do ustawiania atrybutów elementu.

[GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) funkcję członkowską pobiera element formantu drzewa, który ma określoną relację do bieżącego elementu. Ta funkcja może pobrać elementu nadrzędnego, poprzedniego lub następnego elementu widoczne, pierwszego elementu podrzędnego i tak dalej. Dostępne są również przechodzenia drzewa elementów członkowskich: [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), i [ GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).

[GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) funkcja elementu członkowskiego pobiera prostokąt otaczający dla elementu kontrolki drzewa. [GetCount](../mfc/reference/ctreectrl-class.md#getcount) i [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) funkcji składowych pobierać liczbę elementów kontrolki drzewa i liczbę elementów, które są obecnie widoczne w oknie Kontrola drzewa, odpowiednio. Upewnij się że określonego elementu jest widoczna, wywołując [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
