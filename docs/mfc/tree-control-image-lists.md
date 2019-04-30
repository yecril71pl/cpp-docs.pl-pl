---
title: Listy obrazów kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: f4dc4f0d7b2cfb78b07b23802054f119da9cbbc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389401"
---
# <a name="tree-control-image-lists"></a>Listy obrazów kontrolki drzewa

Każdego elementu kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) może mieć parę bitowymi obrazów skojarzonych z nim. Obrazy są wyświetlane po lewej stronie etykiety elementu. Jeden obraz jest wyświetlany, gdy element jest zaznaczony, a drugi jest wyświetlana, jeśli element nie zostanie wybrane. Na przykład element może wyświetlić Otwórz folder, gdy zostanie wybrane i folder zamknięty, gdy nie jest zaznaczona.

Aby używać obrazów elementów, należy utworzyć listy obrazów, tworząc [CImageList](../mfc/reference/cimagelist-class.md) obiektu i przy użyciu [CImageList::Create](../mfc/reference/cimagelist-class.md#create) funkcję, aby utworzyć listę powiązanego obrazu. Następnie dodaj żądaną bitmap do listy i skojarzenia listy z formantem drzewa za pomocą [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) funkcja elementu członkowskiego. Domyślnie wszystkie elementy wyświetlane pierwsze obraz z listy obrazów dla wybranego i nonselected stanów. Domyślne zachowanie dla określonego elementu można zmienić, określając indeksy wybranego i nonselected obrazów, podczas dodawania elementu za pomocą formantu drzewa [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcja elementu członkowskiego. Indeksy można zmienić po dodaniu elementu za pomocą [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) funkcja elementu członkowskiego.

Listy obrazów kontrolki drzewa może również zawierać nakładki obrazów, które mają być nałożoną na obrazach elementu. Określa indeksu liczonego od jednego obrazu nakładki, wartość różną od zera w bitach 8 – 11 stan elementu kontrolki drzewa (0 oznacza brak obrazu nakładki). Ponieważ indeksu 4-bitowego, liczonego od jednego są używane, nakładki obrazów musi być między pierwszych 15 obrazów na listach obrazów. Aby uzyskać więcej informacji na temat stanów elementu kontrolki drzewa, zobacz [przegląd stanów elementu kontrolki drzewa](../mfc/tree-control-item-states-overview.md) we wcześniejszej części tego tematu.

Jeśli listy obrazów stan zostanie określony, formant drzewa rezerwuje miejsce na lewo od każdego elementu ikona obrazu stanu. Aplikacja może użyć obrazy stanu, takie jak pola wyboru zaznaczone i wyczyszczone, aby wskazać stany elementów zdefiniowanych przez aplikację. Wartość różną od zera w bitach 12 – 15 określa indeksu liczonego od jednego obrazu stanu systemu (0 oznacza brak obrazu stanu).

Określając **I_IMAGECALLBACK** wartości zamiast indeksu obrazu, można opóźnić określania obrazu wybranego lub nonselected, dopóki element ma być narysowany ponownie. **I_IMAGECALLBACK** kieruje formant drzewa, aby zbadać wniosek o indeks, wysyłając [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) wiadomość z powiadomieniem.

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) element członkowski funkcja pobiera uchwyt listy obrazów kontrolki drzewa. Funkcja ta jest przydatna, jeśli potrzebujesz dodać więcej obrazów do listy. Aby uzyskać więcej informacji na temat list obrazów, zobacz [korzystanie z CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) w *odwołanie MFC*, i [listy obrazów](/windows/desktop/controls/image-lists) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
