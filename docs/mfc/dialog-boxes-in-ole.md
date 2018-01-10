---
title: Okna dialogowe w OLE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96dfe1828ae3451411adf3ab57c1ec67db24c34e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-boxes-in-ole"></a>Okna dialogowe w OLE
Gdy użytkownik uruchomi aplikację z obsługą OLE, istnieją razy, gdy aplikacja potrzebuje informacje od użytkownika w celu przeprowadzenia operacji. Klasy MFC OLE zapewniają wiele okien dialogowych w celu zebrania wymaganych informacji. W tym temacie wymieniono zadania obsługiwane przez okien dialogowych OLE i klasy niezbędne do wyświetlania tych okien dialogowych. Szczegółowe informacje o okien dialogowych OLE i struktury używane w celu dostosowania ich zachowania, zobacz [odwołania MFC](../mfc/mfc-desktop-applications.md).  
  
 *INSERT — obiekt*  
 To okno dialogowe umożliwia użytkownikowi wstawiania nowych lub istniejących obiektów do dokumentu złożonego. Również umożliwia użytkownikowi wybrać wyświetlanie elementu jako ikonę i umożliwia przycisku polecenia Zmień ikonę. Wyświetl to okno dialogowe, gdy użytkownik wybierze Wstaw obiekt z menu Edycja. Użyj [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) klasy do wyświetlenia tego okna dialogowego. Należy pamiętać, że nie można wstawić aplikacji MDI do siebie samego. Nie można wstawić aplikacji kontenera/serwera do tego samego, chyba że jest to aplikacja SDI.  
  
 *Wklej specjalne*  
 To okno dialogowe umożliwia użytkownikowi na kontrolowanie format używany podczas wklejania danych do złożonego dokumentu. Użytkownik może wybrać format danych, czy osadzić lub połączyć dane i czy chcesz wyświetlić w postaci ikony. Wyświetl to okno dialogowe, gdy użytkownik wybierze Wklej specjalne w menu Edycja. Użyj [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) klasy do wyświetlenia tego okna dialogowego.  
  
 *Zmienianie ikony*  
 To okno dialogowe umożliwia użytkownikowi wybranie ikony, która jest wyświetlana do reprezentowania elementu połączonego lub osadzonego. Wyświetl to okno dialogowe, gdy użytkownik wybierze ikonę zmiany z menu Edycja lub wybierze przycisk Zmień ikonę Wklej specjalne lub przekonwertować okien dialogowych. Również go wyświetlić, gdy użytkownik otwiera okno dialogowe Wstaw obiekt i wybiera pozycję Wyświetl jako ikonę. Użyj [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) klasy do wyświetlenia tego okna dialogowego.  
  
 *Konwertuj*  
 To okno dialogowe umożliwia użytkownikowi zmianę typu osadzonego lub połączonego elementu. Na przykład osadzania metaplik wewnątrz złożonego dokumentu, a później chcesz użyć innej aplikacji do zmodyfikowania osadzonych metaplik, można użyć okna dialogowego Convert. To okno dialogowe jest zwykle wyświetlany, klikając *typ elementu* obiekt menu Edycja, a następnie w menu kaskadowych, klikając polecenie Konwertuj. Użyj [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) klasy do wyświetlenia tego okna dialogowego. Na przykład uruchomić przykładowy MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 *Linków edycji lub aktualizacji*  
 Okno dialogowe Edytuj łącza umożliwia użytkownikom na zmianę informacji o źródle połączonego obiektu. Okno dialogowe łącza aktualizacji sprawdza źródeł połączone elementy w bieżącym oknie dialogowym i wyświetla okno dialogowe Edytuj łącza, jeśli to konieczne. Wyświetl okno dialogowe Edytuj łącza, gdy użytkownik wybierze łącza z menu Edycja. Zazwyczaj zostanie wyświetlone okno dialogowe Aktualizuj łącza, po pierwszym otwarciu złożonego dokumentu. Użyj jednej [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) lub [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) klasy, w zależności od okno dialogowe, które mają być wyświetlane.  
  
 *Serwer jest zajęty lub serwer nie odpowiada*  
 Serwer jest zajęty okno dialogowe jest wyświetlane, gdy użytkownik próbuje aktywować elementu i serwer nie może obecnie obsłużyć żądania, zwykle, ponieważ serwer jest używany przez innego użytkownika lub zadanie. Zostanie wyświetlone okno dialogowe serwer nie odpowiada, jeśli serwer nie odpowiada na żądanie aktywacji w ogóle. Okna te są wyświetlane za pośrednictwem `COleMessageFilter`, oparte na implementację interfejsu OLE **IMessageFilter**, i użytkownik może zdecydować, czy próby żądania aktywacji. Użyj [COleBusyDialog](../mfc/reference/colebusydialog-class.md) klasy do wyświetlenia tego okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

