---
title: Elementy podrzędne i element nadrzędny kontrolki drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c56885300b05cfb038dd1a8484ae57648bf9357
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208435"
---
# <a name="tree-control-parent-and-child-items"></a>Elementy nadrzędne i podrzędne kontrolki drzewa
Dowolnego elementu kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) może się znajdować lista elementów podrzędnych, które nazywane są skojarzone z nim elementów podrzędnych. Element, który ma co najmniej jeden element podrzędny nosi nazwę elementu nadrzędnego. Element podrzędny jest wyświetlana poniżej jego elementu nadrzędnego i tworzone jest wcięcie w celu wskazania, że jest podrzędny w stosunku do obiektu nadrzędnego. Element, który nie ma elementu nadrzędnego znajduje się na szczycie hierarchii i nosi nazwę elementu głównego.  
  
 W dowolnym momencie stan nadrzędnego elementu listy elementów podrzędnych może być rozwinięte lub zwinięte. Po rozwinięciu stan elementy podrzędne są wyświetlane poniżej elementu nadrzędnego. Gdy jest zwinięte, elementy podrzędne nie są wyświetlane. Listy automatycznie przełącza między Stanami rozwiniętymi i zwiniętymi po użytkownik kliknie dwukrotnie nadrzędnego elementu, lub, jeśli element nadrzędny ma **TVS_HASBUTTONS** stylu, gdy użytkownik kliknie przycisk skojarzone z elementem nadrzędnym. Aplikację można rozwinąć lub zwinąć elementy podrzędne przy użyciu [rozwiń](../mfc/reference/ctreectrl-class.md#expand) funkcja elementu członkowskiego.  
  
 Dodawanie elementu kontrolki drzewa, wywołując [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcja elementu członkowskiego. Ta funkcja zwraca uchwyt **HTREEITEM** typ, który unikatowo identyfikuje element. Podczas dodawania elementu, należy określić dojście nowy element nadrzędny element. Jeśli określisz **NULL** lub **TVI_ROOT** wartości zamiast na dojście do elementu nadrzędnego w [TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa) struktury lub *hParent* Parametr element jest dodawany jako element główny.  
  
 Kontrolka drzewa wysyła [TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding) komunikat powiadomienia, gdy element nadrzędny listę elementów podrzędnych ma można rozwijać i zwijać. Powiadomienie daje możliwość zapobiegania zmiany lub ustaw atrybuty elementu nadrzędnego, które są zależne od stanu na liście elementów podrzędnych. Po zmianie stanu listy, formant drzewa wysyła [TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded) wiadomość z powiadomieniem.  
  
 Po rozwinięciu listy elementów podrzędnych go tworzone jest wcięcie względem elementu nadrzędnego. Należy określić wielkość wcięcia przy użyciu [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) funkcji członkowskiej lub pobrać bieżącą ilość przy użyciu [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) funkcja elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

