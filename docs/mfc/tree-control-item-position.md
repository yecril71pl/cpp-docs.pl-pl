---
title: Położenie elementu kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: d39e48cf940f3e5e903fc8a1c82952d5c2550c05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501208"
---
# <a name="tree-control-item-position"></a>Położenie elementu kontrolki drzewa

Położenie początkowe elementu jest ustawiona, gdy element zostanie dodany do kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) przy użyciu `InsertItem` funkcja elementu członkowskiego. Wywołanie funkcji elementu członkowskiego określa uchwyt elementu nadrzędnego i uchwytu elementu, po upływie którego ma zostać wstawiony nowy element. Drugi dojścia musi zidentyfikować elementów podrzędnych danego elementu nadrzędnego lub jedną z tych wartości: `TVI_FIRST`, `TVI_LAST`, lub `TVI_SORT`.

Gdy `TVI_FIRST` lub `TVI_LAST` jest określony, formant drzewa umieszcza nowy element na początku lub na końcu listy elementów podrzędnych elementu nadrzędnego danego. Gdy `TVI_SORT` jest określony, formant drzewa Wstawia nowy element do listy elementów podrzędnych w kolejności alfabetycznej na podstawie tekstu etykiety elementów.

Listy elementów podrzędnych elementu nadrzędnego można umieścić w kolejności alfabetycznej, wywołując [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) funkcja elementu członkowskiego. Ta funkcja zawiera parametr, który określa, czy wszystkie poziomy elementów podrzędnych, od nadrzędnego danego elementu, również są sortowane w kolejności alfabetycznej.

[SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) funkcja elementu członkowskiego umożliwia sortowanie elementów podrzędnych na podstawie kryteriów, które definiujesz. Jeśli chcesz wywołać tę funkcję, należy określić zdefiniowanych przez aplikację funkcji wywołania zwrotnego, formant drzewa może wywołać zawsze wtedy, gdy trzeba zdecydować względną kolejność dwóch elementów podrzędnych. Funkcja wywołania zwrotnego otrzymuje dwa wartości 32-bitowe zdefiniowanych przez aplikację dla elementów, którą jest porównywany i trzeci 32-bitową wartość, która została określona podczas wywoływania `SortChildrenCB`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

