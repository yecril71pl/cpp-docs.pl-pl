---
title: "Element nadrzędny kontrolki i elementy podrzędne drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: feaf59932da66be2bf269316c7ee9587d4037b3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-parent-and-child-items"></a>Elementy nadrzędne i podrzędne kontrolki drzewa
Dowolny element formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) może mieć listy elementów podrzędnych, które są nazywane związane z nim elementy podrzędne. Element, który ma co najmniej jeden element podrzędny nosi nazwę elementu nadrzędnego. Element podrzędny jest wyświetlony poniżej jego element nadrzędny i tworzone jest wcięcie wskazująca, że jest podrzędny w stosunku do obiektu nadrzędnego. Element, który nie ma nadrzędnego znajduje się na szczycie hierarchii i nosi nazwę elementu głównego.  
  
 W dowolnym momencie stan listy elementów podrzędnych elementu nadrzędnego może zostać rozwinięte lub zwinięte. Po rozwinięciu stan elementy podrzędne są wyświetlane poniżej elementu nadrzędnego. Po zwinięciu, elementy podrzędne nie są wyświetlane. Listy automatycznie przełącza między Stanami rozwinięte i zwinięte, gdy użytkownik kliknie dwukrotnie elementu nadrzędnego lub, jeśli element nadrzędny ma **TVS_HASBUTTONS** stylu, gdy użytkownik kliknie przycisk skojarzone z elementem nadrzędnym. Aplikację można rozwinąć lub zwinąć elementy podrzędne za pomocą [rozwiń](../mfc/reference/ctreectrl-class.md#expand) funkcję elementu członkowskiego.  
  
 Dodaj element do formantu drzewa, wywołując [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcję elementu członkowskiego. Ta funkcja zwraca uchwyt **HTREEITEM** typu, który unikatowo identyfikuje element. Podczas dodawania elementu, należy określić dojście nowego elementu nadrzędnego elementu. Jeśli określisz **NULL** lub **TVI_ROOT** zamiast uchwytu elementu nadrzędnego w wartości [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) struktury lub `hParent` parametru element zostanie dodany jako katalog główny element.  
  
 Formant drzewa wysyła [TVN_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) powiadomienie, gdy ma być rozwijane czy zwijane listy elementów podrzędnych elementu nadrzędnego. Powiadomienia daje możliwość uniemożliwiają zmianę lub ustawić atrybuty elementu nadrzędnego, które są zależne od stanu na liście elementów podrzędnych. Po zmianie stanu z listy, wysyła do drzewa [TVN_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) wiadomość z powiadomieniem.  
  
 Po rozwinięciu listy elementów podrzędnych jest wcięty względem elementu nadrzędnego. Należy określić wielkość wcięcia przy użyciu [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) funkcji członkowskiej lub pobrać bieżącą ilość przy użyciu [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

