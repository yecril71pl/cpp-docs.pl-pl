---
title: Elementy wywołania zwrotnego i maska wywołania zwrotnego
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509138"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementy wywołania zwrotnego i maska wywołania zwrotnego

Dla każdego elementu, kontrolka widoku listy zazwyczaj przechowuje tekst etykiety, indeks listy obrazów ikon elementu oraz zestaw flag bitowych dla stanu elementu. Można definiować poszczególne elementy jako elementy wywołania zwrotnego, które są przydatne, jeśli aplikacja przechowuje już niektóre informacje dla elementu.

Element można zdefiniować jako element `pszText` wywołania zwrotnego, określając odpowiednie wartości dla i `iImage` elementów członkowskich `LVITEM` struktury (zobacz [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Jeśli aplikacja zachowuje tekst elementu lub podelementu, określ wartość **LPSTR_TEXTCALLBACK** dla `pszText` elementu członkowskiego. Jeśli aplikacja śledzi ikonę elementu, określ wartość `iImage` **I_IMAGECALLBACK** elementu członkowskiego.

Oprócz definiowania elementów wywołania zwrotnego można także zmodyfikować maskę wywołania zwrotnego kontrolki. Ta maska jest zestawem flag bitowych, które określają Stany elementów, dla których aplikacja, a nie kontrolka, przechowuje bieżące dane. Maska wywołania zwrotnego ma zastosowanie do wszystkich elementów kontrolki, w przeciwieństwie do oznaczenia elementu wywołania zwrotnego, który ma zastosowanie do określonego elementu. Domyślnie Maska wywołania zwrotnego jest równa zero, co oznacza, że kontrolka śledzi wszystkie Stany elementów. Aby zmienić to zachowanie domyślne, zainicjuj maskę do dowolnej kombinacji następujących wartości:

- **LVIS_CUT** Element jest oznaczony dla operacji wycinania i wklejania.

- **LVIS_DROPHILITED** Element zostanie wyróżniony jako element docelowy typu "przeciągnij i upuść".

- **LVIS_FOCUSED** Element ma fokus.

- **LVIS_SELECTED** Wybrano element.

- **LVIS_OVERLAYMASK** Aplikacja przechowuje indeks listy obrazów dla bieżącego obrazu nakładki dla każdego elementu.

- **LVIS_STATEIMAGEMASK** Aplikacja przechowuje indeks listy obrazów bieżącego stanu dla każdego elementu.

Aby uzyskać więcej informacji na temat pobierania i ustawiania tej maski, zobacz [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) i [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
