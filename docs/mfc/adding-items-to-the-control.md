---
title: Dodawanie elementów do kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc1d4cefd7d292333c4797afea369104733d117d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385069"
---
# <a name="adding-items-to-the-control"></a>Dodawanie elementów do formantu

Aby dodać elementy do kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), wywołać jedną z kilku różnych wersji [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) funkcja elementu członkowskiego, w zależności od tego, jakie informacje należy. Trwa jednej wersji [LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) struktury, które należy przygotować. Ponieważ `LV_ITEM` struktura zawiera wiele elementów członkowskich, masz większą kontrolę nad atrybuty elementu kontrolki listy.

Dwie ważne elementy członkowskie (rozumieniu widok raportu) `LV_ITEM` struktury są `iItem` i `iSubItem` elementów członkowskich. `iItem` Element członkowski jest liczony od zera indeks elementu, który odwołuje się do struktury i `iSubItem` element członkowski jest indeksu liczonego od jednego podelement lub zero, jeśli struktura zawiera informacje o elemencie. Za pomocą tych dwóch członków można ustalić, dla elementu, typ i wartość informacji podelement, które jest wyświetlane, gdy kontrolka listy znajduje się w widoku raportu. Aby uzyskać więcej informacji, zobacz [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).

Dodatkowe elementy członkowskie określenia elementu tekstu, ikony, stanu i danych elementów. "Element data" jest skojarzony z elementu widoku listy wartością zdefiniowanych przez aplikację. Aby uzyskać więcej informacji na temat `LV_ITEM` struktury, zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).

Inne wersje `InsertItem` wykonać co najmniej jeden oddzielny wartości odpowiadające elementy członkowskie w `LV_ITEM` struktury, dzięki czemu możesz zainicjować tylko członkowie mają być obsługiwane. Ogólnie rzecz biorąc formant listy zarządza magazynem dla elementów listy, ale można zapisać niektórych informacji w aplikacji zamiast tego za pomocą ""wywołania zwrotnego items. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](../mfc/callback-items-and-the-callback-mask.md) w tym temacie i [elementy wywołania zwrotnego i maska wywołania zwrotnego](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [Dodawanie widoku listy elementów i podelementów](/windows/desktop/Controls/using-list-view-controls).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

