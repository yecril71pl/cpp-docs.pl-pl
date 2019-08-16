---
title: Dodawanie elementów do formantu
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 6c03be6f04746ec2e3146916d72cad637a204187
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509324"
---
# <a name="adding-items-to-the-control"></a>Dodawanie elementów do formantu

Aby dodać elementy do kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), wywołaj jedną z kilku wersji funkcji składowej [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) , w zależności od posiadanych informacji. Jedna wersja przyjmuje przygotowaną strukturę [LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw) . `LVITEM` Ponieważ struktura zawiera wiele elementów członkowskich, masz większą kontrolę nad atrybutami elementu kontrolki listy.

Dwa ważne elementy członkowskie (w odniesieniu do widoku raportu) `LVITEM` struktury `iItem` są elementami i `iSubItem` . Składowa jest indeksem (liczonym od zera) elementu, do którego odwołuje się `iSubItem` struktura, a składowa jest indeksem jednego z nich, lub zero, jeśli struktura zawiera informacje o elemencie. `iItem` Za pomocą tych dwóch elementów członkowskich, które można określić dla każdego elementu, typ i wartość informacji o podelementach, które są wyświetlane, gdy kontrolka listy jest w widoku raportu. Aby uzyskać więcej informacji, zobacz [CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem).

Dodatkowe elementy członkowskie określają tekst, ikonę, stan i dane elementu elementu. "Dane elementu" to zdefiniowana przez aplikację wartość skojarzona z elementem widoku listy. Aby uzyskać więcej informacji na `LVITEM` temat struktury, zobacz [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem).

Inne wersje `InsertItem` mają jedną lub więcej oddzielnych wartości, które odpowiadają członkom `LVITEM` struktury, co pozwala na zainicjowanie tylko tych członków, które mają być obsługiwane. Ogólnie rzecz biorąc, kontrolka list zarządza magazynem dla elementów listy, ale zamiast tego można przechowywać niektóre informacje w aplikacji, używając "elementów wywołania zwrotnego". Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i Maska wywołania zwrotnego](../mfc/callback-items-and-the-callback-mask.md) w tym temacie oraz [elementy wywołania zwrotnego i Maska wywołania zwrotnego](/windows/win32/Controls/using-list-view-controls) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [Dodawanie listy elementów i elementów](/windows/win32/Controls/using-list-view-controls)SubItems.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
