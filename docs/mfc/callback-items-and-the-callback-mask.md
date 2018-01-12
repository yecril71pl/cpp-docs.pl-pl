---
title: "Elementy wywołania zwrotnego i maska wywołania zwrotnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d9992b8a9db679b30624d85ede1a35bfd9826d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="callback-items-and-the-callback-mask"></a>Elementy wywołania zwrotnego i maska wywołania zwrotnego
Dla każdego z jego elementów formantu widoku listy zwykle przechowuje tekst etykiety, indeks obrazu listy ikon elementu i zestaw bit flagi stanu elementu. Poszczególne elementy można zdefiniować jako elementy wywołania zwrotnego, które są przydatne, jeśli aplikacja już przechowuje niektóre informacje dla elementu.  
  
 Zdefiniuj element jako element wywołania zwrotnego, określając odpowiednie wartości dla `pszText` i `iImage` członkami **LV_ITEM** struktury (zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Jeśli aplikacja przechowuje tekst elementu lub jego podelementu, określ **LPSTR_TEXTCALLBACK** wartość `pszText` elementu członkowskiego. Jeśli aplikacja przechowuje informacje o ikony dla elementu, określ **I_IMAGECALLBACK** wartość `iImage` elementu członkowskiego.  
  
 Oprócz definiujący elementy wywołania zwrotnego, można również zmodyfikować maska wywołania zwrotnego formantu. Ta maska ustawiono flagi bitów, które określają stanów elementu, dla których aplikacji, a nie formantu, zapisuje bieżące dane. Maska wywołania zwrotnego ma zastosowanie do wszystkich elementów formantu, w odróżnieniu od oznaczenie elementu wywołania zwrotnego, która ma zastosowanie do określonego elementu. Maska wywołania zwrotnego wynosi zero domyślnie, co oznacza, że kontrolka śledzi wszystkie stany elementu. Aby zmienić to zachowanie domyślne, należy zainicjować masce dowolną kombinację następujących wartości:  
  
-   `LVIS_CUT`Element jest oznaczony do operacji kopiowania i wklejania.  
  
-   `LVIS_DROPHILITED`Element zostanie wyróżniona jako element docelowy przeciągania i upuszczania.  
  
-   `LVIS_FOCUSED`Element ma fokus.  
  
-   `LVIS_SELECTED`Element jest zaznaczony.  
  
-   **LVIS_OVERLAYMASK** aplikacja przechowuje indeksu listy obrazów bieżącego obrazu nakładki dla każdego elementu.  
  
-   **LVIS_STATEIMAGEMASK** aplikacja przechowuje indeksu listy obrazów bieżącego obrazu stanu dla każdego elementu.  
  
 Aby uzyskać więcej informacji dotyczących pobierania i ustawiania ta maska, zobacz [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) i [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

