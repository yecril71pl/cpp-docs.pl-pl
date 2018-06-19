---
title: Tworzenie formantu listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42457e223bb7e12da64be54d757e05d0bac3a028
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342049"
---
# <a name="creating-the-list-control"></a>Tworzenie kontrolki listy
Metody kontrolowania listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) jest tworzony zależy od tego, czy jest bezpośrednio za pomocą formantu lub za pomocą klasy [clistview —](../mfc/reference/clistview-class.md) zamiast tego. Jeśli używasz `CListView`, platformę tworzy widok jako część jej Sekwencja tworzenia dokumentu/widoku. Tworzenie widoku listy tworzy kontrolki listy również (są to samo). Formant nie zostanie utworzony w widoku [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi. W takim przypadku formant jest gotowy do dodawania elementów za pomocą wywołania [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).  
  
### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Do użycia bezpośrednio w oknie dialogowym CListCtrl  
  
1.  W edytorze okien dialogowych Dodaj formant listy zasobu szablonu okna dialogowego. Określ jego identyfikator formantu.  
  
2.  Użyj [Kreator dodawania zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej członka typu `CListCtrl` razem z właściwością formantu. Ten element członkowski można użyć do wywołania `CListCtrl` funkcji elementów członkowskich.  
  
3.  Użyj okna właściwości do mapowania funkcje programu obsługi w klasy okien dialogowych dla wszystkich powiadomień formantu listy wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
4.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustawianie stylów dla `CListCtrl`. Zobacz [Zmienianie stylów formantu listy](../mfc/changing-list-control-styles.md). Określa rodzaj "Widok" pobieranie w formancie, mimo że można później zmienić widok.  
  
### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Do użycia w oknie nondialog CListCtrl  
  
1.  Zdefiniuj formantu w klasie widoku lub okna.  
  
2.  Wywołanie formantu [Utwórz](../mfc/reference/clistctrl-class.md#create) prawdopodobnie w funkcji członkowskiej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie możliwie wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy formantu). Ustawianie stylów formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

