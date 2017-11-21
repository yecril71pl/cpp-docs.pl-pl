---
title: "Listy obrazów formantu drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b4864f4ac15a1d07deb4c3cb8a8d533b8cc4b82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-image-lists"></a>Listy obrazów kontrolki drzewa
Każdy element formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) może mieć dwa obrazy mapy bitowej skojarzonych z nim. Obrazy są wyświetlane po lewej stronie etykiety elementu. Jeden obraz jest wyświetlane, gdy element jest zaznaczony, a drugi jest wyświetlany, gdy nie wybrano elementu. Na przykład element może być wyświetlany Otwórz folder, jeśli jest zaznaczone i folder zamknięty, gdy nie jest zaznaczona.  
  
 Aby używać obrazów elementów, należy utworzyć listy obrazów, tworząc [CImageList](../mfc/reference/cimagelist-class.md) obiekt i przy użyciu [CImageList::Create](../mfc/reference/cimagelist-class.md#create) funkcji, aby utworzyć listę skojarzony obraz. Następnie dodaj żądaną bitmap do listy i skojarzyć listy z formantem drzewa za pomocą [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) funkcję elementu członkowskiego. Domyślnie wszystkie elementy wyświetlane pierwszy obraz obrazu na liście wybranych i nonselected stanów. Domyślne zachowanie dla danego elementu można zmienić, określając indeksy wybranych i nonselected obrazów, podczas dodawania elementu przy użyciu formantu drzewa [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcję elementu członkowskiego. Indeksy można zmienić po dodaniu elementu za pomocą [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) funkcję elementu członkowskiego.  
  
 Listy obrazów kontrolki drzewa może również zawierać nakładki obrazów, które mają być nałożoną na obrazów elementów. Wartość różną od zera w bitach 8 – 11 stanu elementu formantu drzewa Określa indeks obrazu nakładki jedynki (0 oznacza brak obrazu nakładki). Nakładki obrazów indeksu 4-bitowy, oparte na jednym jest używana, musi być między najpierw 15 obrazów na listach obrazów. Aby uzyskać więcej informacji na temat stanów elementu formantu drzewa, zobacz [przegląd stanów elementu formantu drzewa](../mfc/tree-control-item-states-overview.md) wcześniej w tym temacie.  
  
 Jeśli określono listę obraz stanu, formantu drzewa rezerwuje miejsca z lewej strony każdego elementu ikonę obrazu stanu. Aplikacja może używać obrazy stanu, takie jak zaznaczony i wyczyszczenie pola wyboru, aby wskazać stanów elementu zdefiniowanym przez aplikację. Wartość różną od zera w bitach 12 – 15 określa indeks obrazu stanu jedynki (0 oznacza nie obrazu stanu).  
  
 Określając **I_IMAGECALLBACK** wartość zamiast indeks obrazu można opóźnić Określanie obraz wybrany lub nonselected, dopóki element ma być narysowany ponownie. **I_IMAGECALLBACK** kieruje do drzewa do badania aplikacji dla indeksu, wysyłając [TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) wiadomość z powiadomieniem.  
  
 [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) funkcji członkowskiej pobiera dojście listy obrazów formantu drzewa. Ta funkcja jest przydatna, jeśli potrzebujesz dodać więcej obrazów do listy. Aby uzyskać więcej informacji na temat list obrazów, zobacz [przy użyciu CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) w *odwołania MFC*, i [listy obrazów](http://msdn.microsoft.com/library/windows/desktop/bb761389) w Zestaw Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Formanty](../mfc/controls-mfc.md)

