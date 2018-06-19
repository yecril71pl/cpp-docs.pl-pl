---
title: Położenie elementu formantu drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7b7576786f456320a355920a7a9ef9e4935ab03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382154"
---
# <a name="tree-control-item-position"></a>Położenie elementu kontrolki drzewa
Położenie początkowe elementu jest ustawiona, gdy element zostanie dodany do formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) przy użyciu `InsertItem` funkcję elementu członkowskiego. Wywołanie funkcji Członkowskich określa uchwytu elementu nadrzędnego i obsługi po upływie którego nowy element ma zostać wstawiony element. Drugi dojścia musi zidentyfikować elementów podrzędnych danego elementu nadrzędnego lub jedną z tych wartości: `TVI_FIRST`, `TVI_LAST`, lub `TVI_SORT`.  
  
 Gdy `TVI_FIRST` lub `TVI_LAST` określono drzewie umieszcza nowy element na początku lub na końcu listy elementów podrzędnych elementu nadrzędnego danego. Gdy `TVI_SORT` określono drzewie Wstawia nowy element do listy elementów podrzędnych w kolejności alfabetycznej na podstawie tekstu etykiety elementów.  
  
 Listy elementów podrzędnych elementu nadrzędnego można umieścić w kolejności alfabetycznej wywołując [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) funkcję elementu członkowskiego. Ta funkcja zawiera parametr, który określa, czy wszystkie poziomy od nadrzędnego danego elementu elementy podrzędne są również sortowane w kolejności alfabetycznej.  
  
 [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) funkcji członkowskiej umożliwia sortowanie elementów podrzędnych na podstawie kryteriów, które zostały zdefiniowane. Podczas wywoływania tej funkcji, należy określić zdefiniowanym przez aplikację funkcja wywołania zwrotnego drzewie można wywołać, gdy względną kolejność dwa elementy podrzędne musi być określona. Funkcja wywołania zwrotnego otrzymuje dwa wartości 32-bitowe zdefiniowanym przez aplikację dla elementów są porównywane i trzecia wartość 32-bitowy, określonym przez użytkownika podczas wywoływania metody `SortChildrenCB`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

