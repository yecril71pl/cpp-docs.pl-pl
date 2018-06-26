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
ms.openlocfilehash: 4f3608fbc0c7e34de4ae67ae60a12af23e9ac885
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931691"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementy wywołania zwrotnego i maska wywołania zwrotnego
Dla każdego z jego elementów formantu widoku listy zwykle przechowuje tekst etykiety, indeks obrazu listy ikon elementu i zestaw bit flagi stanu elementu. Poszczególne elementy można zdefiniować jako elementy wywołania zwrotnego, które są przydatne, jeśli aplikacja już przechowuje niektóre informacje dla elementu.  
  
 Zdefiniuj element jako element wywołania zwrotnego, określając odpowiednie wartości dla `pszText` i `iImage` członkami **LV_ITEM** struktury (zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Jeśli aplikacja przechowuje tekst elementu lub jego podelementu, określ **LPSTR_TEXTCALLBACK** wartość `pszText` elementu członkowskiego. Jeśli aplikacja przechowuje informacje o ikony dla elementu, określ **I_IMAGECALLBACK** wartość `iImage` elementu członkowskiego.  
  
 Oprócz definiujący elementy wywołania zwrotnego, można również zmodyfikować maska wywołania zwrotnego formantu. Ta maska ustawiono flagi bitów, które określają stanów elementu, dla których aplikacji, a nie formantu, zapisuje bieżące dane. Maska wywołania zwrotnego ma zastosowanie do wszystkich elementów formantu, w odróżnieniu od oznaczenie elementu wywołania zwrotnego, która ma zastosowanie do określonego elementu. Maska wywołania zwrotnego wynosi zero domyślnie, co oznacza, że kontrolka śledzi wszystkie stany elementu. Aby zmienić to zachowanie domyślne, należy zainicjować masce dowolną kombinację następujących wartości:  
  
-   **LVIS_CUT** element jest oznaczony do operacji kopiowania i wklejania.  
  
-   **LVIS_DROPHILITED** element zostanie wyróżniona jako element docelowy przeciągania i upuszczania.  
  
-   **LVIS_FOCUSED** element ma fokus.  
  
-   **LVIS_SELECTED** element jest zaznaczony.  
  
-   **LVIS_OVERLAYMASK** aplikacja przechowuje indeksu listy obrazów bieżącego obrazu nakładki dla każdego elementu.  
  
-   **LVIS_STATEIMAGEMASK** aplikacja przechowuje indeksu listy obrazów bieżącego obrazu stanu dla każdego elementu.  
  
 Aby uzyskać więcej informacji dotyczących pobierania i ustawiania ta maska, zobacz [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) i [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

