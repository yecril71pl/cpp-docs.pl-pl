---
title: "Klasy wspólnych okien dialogowych OLE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0617354337e75e2c2431df894c054722349e2306
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-common-dialog-classes"></a>Klasy wspólnych okien dialogowych OLE
Te klasy obsługi typowych zadań OLE implementując kilka standardowych oknach dialogowych OLE. Zapewniają także spójny interfejs użytkownika funkcji OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Używane przez platformę do przechowywania najczęściej występujące implementacje dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejsu użytkownika są uzyskiwane z tej klasy podstawowej. `COleDialog`Nie można używać bezpośrednio.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Wyświetla okno dialogowe Wstaw obiekt standardowy interfejs użytkownika dla wstawiania nowych OLE połączone lub osadzone elementy.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Wyświetla okno dialogowe Wklej specjalne standardowy interfejs użytkownika dla wykonania polecenia Edytuj Wklej specjalne.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Wyświetla okno dialogowe Edytuj łącza standardowy interfejs użytkownika do modyfikowania informacji na temat połączone elementy.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Wyświetla okno dialogowe Zmienianie ikony, standardowy interfejs użytkownika dla zmiana, którą osadzonych ikon skojarzonych z OLE lub połączony element.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Wyświetla okno dialogowe Konwertowanie standardowy interfejs użytkownika do konwertowania elementy OLE z jednego typu.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Hermetyzuje okno dialogowe właściwości OLE wspólne systemu Windows. Wspólne okna dialogowe OLE właściwości umożliwiają łatwe do wyświetlanie i modyfikowanie właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Wyświetla okno dialogowe aktualizacji standardowy interfejs użytkownika aktualizacji wszystkich łączy w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, jak blisko procedura aktualizacji zostanie do zakończenia.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Wyświetla okno dialogowe Zmienianie źródła standardowy interfejs użytkownika do zmiany docelowy lub źródłowy łącza.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Wyświetla oknach dialogowych serwer jest zajęty i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań zajęty aplikacji. Zwykle wyświetlane automatycznie przez `COleMessageFilter` implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

