---
title: "Dodawanie elementów do formantu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1469209307f5bfc3016a7232095c36f47b38855b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-items-to-the-control"></a>Dodawanie elementów do formantu
Do dodawania elementów do formantu listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), wywoływanie jednego z kilku wersji [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) funkcji członkowskiej, w zależności od tego, jakie informacje. Trwa jednej wersji [LV_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) struktury, którego można przygotować. Ponieważ `LV_ITEM` struktura zawiera wiele elementów członkowskich, masz większą kontrolę nad atrybuty kontrolki elementu listy.  
  
 Dwie ważne członków (widok raportu) w zakresie `LV_ITEM` struktury są `iItem` i `iSubItem` elementów członkowskich. `iItem` Element członkowski jest liczony od zera indeks elementu odwołuje się do struktury i `iSubItem` element członkowski jest jeden indeks podelementów lub zero, jeśli struktura zawiera informacje o elemencie. Z tych dwóch elementów członkowskich należy określić, na element, typ i wartość podelementu informacje, które jest wyświetlane, gdy formant listy znajduje się w widoku raportu. Aby uzyskać więcej informacji, zobacz [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).  
  
 Dodatkowe elementy członkowskie Określ tekst, ikona, stanu i danych elementu elementu. "Element danych" jest skojarzony z elementu widoku listy wartości zdefiniowane przez aplikację. Aby uzyskać więcej informacji na temat `LV_ITEM` struktury, zobacz [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).  
  
 Inne wersje `InsertItem` wykonać jedną lub więcej wartości oddzielne, odpowiadający elementów członkowskich w `LV_ITEM` struktury, dzięki czemu można zainicjować tylko członkowie mają być obsługiwane. Ogólnie rzecz biorąc kontrolki listy zarządza Magazyn dla elementów listy, ale można przechowywać niektóre informacje w aplikacji, za pomocą "elementy wywołania zwrotnego." Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](../mfc/callback-items-and-the-callback-mask.md) w tym temacie i [elementy wywołania zwrotnego i maska wywołania zwrotnego](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie widoku listy elementów i podelementów](http://msdn.microsoft.com/library/windows/desktop/bb774736).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

