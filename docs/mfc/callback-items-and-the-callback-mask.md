---
title: Elementy wywołania zwrotnego i maska wywołania zwrotnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0711fccb142d9774c37f2cb2d8f576bf7fddd128
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422847"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementy wywołania zwrotnego i maska wywołania zwrotnego

Dla każdego z jego elementów kontrolka widoku listy zazwyczaj przechowuje tekst etykiety, indeks listy obrazu ikony elementu i zestaw bit flagi stanu elementu. Poszczególne elementy można zdefiniować jako elementy wywołania zwrotnego, które są przydatne, jeśli aplikacja już zapisuje niektóre informacje dla elementu.

Zdefiniuj element jako element wywołania zwrotnego, określając odpowiednie wartości dla `pszText` i `iImage` członkowie **LV_ITEM** struktury (zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Jeśli aplikacja przechowuje tekst elementu lub podelementu firmy, należy określić **LPSTR_TEXTCALLBACK** wartość `pszText` elementu członkowskiego. Jeśli aplikacja przechowuje informacje o ikonę elementu, należy określić **I_IMAGECALLBACK** wartość `iImage` elementu członkowskiego.

Oprócz definiowania elementy wywołania zwrotnego, można również zmodyfikować formantu maska wywołania zwrotnego. Tę maskę ustawiono flagi bitowe, które określają stany elementów, dla których aplikacji, a nie dla kontrolki, zapisuje bieżące dane. Maska wywołania zwrotnego ma zastosowanie do wszystkich elementów formantu, w przeciwieństwie do oznaczenia element wywołania zwrotnego, która odnosi się do określonego elementu. Maska wywołania zwrotnego wynosi zero, domyślnie, co oznacza, że kontrolka śledzi wszystkie stany elementów. Aby zmienić to zachowanie domyślne, należy zainicjować maski do dowolnej kombinacji następujących wartości:

- **LVIS_CUT** element jest oznaczony dla operacji kopiowania i wklejania.

- **LVIS_DROPHILITED** element zostanie wyróżniony jako element docelowy przeciągania i upuszczania.

- **LVIS_FOCUSED** element ma fokus.

- **LVIS_SELECTED** element jest zaznaczony.

- **LVIS_OVERLAYMASK** aplikacja przechowuje indeks listy obrazu bieżącego obrazu nakładki dla każdego elementu.

- **LVIS_STATEIMAGEMASK** aplikacja przechowuje indeks listy obrazu bieżącego obrazu stanu dla każdego elementu.

Aby uzyskać więcej informacji na temat pobierania i ustawiania tę maskę zobacz [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) i [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

