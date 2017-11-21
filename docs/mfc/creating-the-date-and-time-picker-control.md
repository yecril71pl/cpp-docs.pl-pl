---
title: Tworzenie formantu selektora godzina i Data | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc83daa0c009f997992e32165c1000d89a17aa98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-date-and-time-picker-control"></a>Tworzenie formantu selektora dat i godzin
Sposób tworzenia formant wyboru daty i godziny zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenia go w oknie nondialog.  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Do użycia bezpośrednio w oknie dialogowym CDateTimeCtrl  
  
1.  W edytorze okien dialogowych dodając datę i formant wyboru godziny zasobu szablonu okna dialogowego. Określ jego identyfikator formantu.  
  
2.  Określ wszystkie wymagane, style za pomocą okna dialogowego właściwości formantu selektora daty i godziny.  
  
3.  Użyj [Kreator dodawania zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej członka typu [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) razem z właściwością formantu. Ten element członkowski można użyć do wywołania `CDateTimeCtrl` funkcji elementów członkowskich.  
  
4.  Użyj okna właściwości do mapowania funkcje programu obsługi w klasy okien dialogowych dla dowolnego formant wyboru godziny data [powiadomień](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) potrzebne do obsługi komunikatów (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CDateTimeCtrl` obiektu.  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Do użycia w oknie nondialog CDateTimeCtrl  
  
1.  Zadeklarować formantu w klasie widoku lub okna.  
  
2.  Wywołanie formantu [Utwórz](../mfc/reference/ctabctrl-class.md#create) prawdopodobnie w funkcji członkowskiej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie możliwie wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy formantu). Ustawianie stylów formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Formanty](../mfc/controls-mfc.md)

