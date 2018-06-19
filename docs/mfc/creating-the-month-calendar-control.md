---
title: Tworzenie kalendarza miesięcznego kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e5cb58cfbecd03964963814081c2f0039c0752c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343246"
---
# <a name="creating-the-month-calendar-control"></a>Tworzenie formantu kalendarza miesięcznego
Sposób tworzenia formant kalendarza miesięcznego zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenia go w oknie nondialog.  
  
### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Do użycia bezpośrednio w oknie dialogowym CMonthCalCtrl  
  
1.  W edytorze okien dialogowych Dodaj formant kalendarza miesięcznego zasobu szablonu okna dialogowego. Określ jego identyfikator formantu.  
  
2.  Określ wszystkie style wymagane, za pomocą okna dialogowego właściwości w formancie kalendarza miesięcznego.  
  
3.  Użyj [Kreator dodawania zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej członka typu [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) razem z właściwością formantu. Ten element członkowski można użyć do wywołania `CMonthCalCtrl` funkcji elementów członkowskich.  
  
4.  Użyj okna właściwości do mapowania funkcje programu obsługi w klasy okien dialogowych dla wszystkich powiadomień formantu kalendarza miesięcznego wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CMonthCalCtrl` obiektu.  
  
### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Do użycia w oknie nondialog CMonthCalCtrl  
  
1.  Zdefiniuj formantu w klasie widoku lub okna.  
  
2.  Wywołanie formantu [Utwórz](../mfc/reference/cmonthcalctrl-class.md#create) prawdopodobnie w funkcji członkowskiej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie możliwie wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy formantu). Ustawianie stylów formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

