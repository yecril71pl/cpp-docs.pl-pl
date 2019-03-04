---
title: Dodawanie elementów do formantu
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 88e008f06fb669db1c13872b1a58555eeb357d86
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304603"
---
# <a name="adding-items-to-the-control"></a>Dodawanie elementów do formantu

Aby dodać elementy do kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), wywołać jedną z kilku różnych wersji [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) funkcja elementu członkowskiego, w zależności od tego, jakie informacje należy. Trwa jednej wersji [LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) struktury, które należy przygotować. Ponieważ `LV_ITEM` struktura zawiera wiele elementów członkowskich, masz większą kontrolę nad atrybuty elementu kontrolki listy.

Dwie ważne elementy członkowskie (rozumieniu widok raportu) `LV_ITEM` struktury są `iItem` i `iSubItem` elementów członkowskich. `iItem` Element członkowski jest liczony od zera indeks elementu, który odwołuje się do struktury i `iSubItem` element członkowski jest indeksu liczonego od jednego podelement lub zero, jeśli struktura zawiera informacje o elemencie. Za pomocą tych dwóch członków można ustalić, dla elementu, typ i wartość informacji podelement, które jest wyświetlane, gdy kontrolka listy znajduje się w widoku raportu. Aby uzyskać więcej informacji, zobacz [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).

Dodatkowe elementy członkowskie określenia elementu tekstu, ikony, stanu i danych elementów. "Element data" jest skojarzony z elementu widoku listy wartością zdefiniowanych przez aplikację. Aby uzyskać więcej informacji na temat `LV_ITEM` struktury, zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).

Inne wersje `InsertItem` wykonać co najmniej jeden oddzielny wartości odpowiadające elementy członkowskie w `LV_ITEM` struktury, dzięki czemu możesz zainicjować tylko członkowie mają być obsługiwane. Ogólnie rzecz biorąc formant listy zarządza magazynem dla elementów listy, ale można zapisać niektórych informacji w aplikacji zamiast tego za pomocą ""wywołania zwrotnego items. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](../mfc/callback-items-and-the-callback-mask.md) w tym temacie i [elementy wywołania zwrotnego i maska wywołania zwrotnego](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [Dodawanie widoku listy elementów i podelementów](/windows/desktop/Controls/using-list-view-controls).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
