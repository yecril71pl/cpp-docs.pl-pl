---
title: "Położenie elementu formantu drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db47e27ad0b556e08f51685bf84b6bd998722239
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-position"></a>Położenie elementu kontrolki drzewa
Położenie początkowe elementu jest ustawiona, gdy element zostanie dodany do formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) przy użyciu `InsertItem` funkcję elementu członkowskiego. Wywołanie funkcji Członkowskich określa uchwytu elementu nadrzędnego i obsługi po upływie którego nowy element ma zostać wstawiony element. Drugi dojścia musi zidentyfikować elementów podrzędnych danego elementu nadrzędnego lub jedną z tych wartości: `TVI_FIRST`, `TVI_LAST`, lub `TVI_SORT`.  
  
 Gdy `TVI_FIRST` lub `TVI_LAST` określono drzewie umieszcza nowy element na początku lub na końcu listy elementów podrzędnych elementu nadrzędnego danego. Gdy `TVI_SORT` określono drzewie Wstawia nowy element do listy elementów podrzędnych w kolejności alfabetycznej na podstawie tekstu etykiety elementów.  
  
 Listy elementów podrzędnych elementu nadrzędnego można umieścić w kolejności alfabetycznej wywołując [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) funkcję elementu członkowskiego. Ta funkcja zawiera parametr, który określa, czy wszystkie poziomy od nadrzędnego danego elementu elementy podrzędne są również sortowane w kolejności alfabetycznej.  
  
 [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) funkcji członkowskiej umożliwia sortowanie elementów podrzędnych na podstawie kryteriów, które zostały zdefiniowane. Podczas wywoływania tej funkcji, należy określić zdefiniowanym przez aplikację funkcja wywołania zwrotnego drzewie można wywołać, gdy względną kolejność dwa elementy podrzędne musi być określona. Funkcja wywołania zwrotnego otrzymuje dwa wartości 32-bitowe zdefiniowanym przez aplikację dla elementów są porównywane i trzecia wartość 32-bitowy, określonym przez użytkownika podczas wywoływania metody `SortChildrenCB`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

