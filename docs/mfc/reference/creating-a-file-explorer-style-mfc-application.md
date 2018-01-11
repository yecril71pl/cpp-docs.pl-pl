---
title: "Tworzenie aplikacji MFC w stylu Eksploratora plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfcexplorer.project
dev_langs: C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6098e451b4ebc4caf2bb7fad99ea2e407e4872c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Tworzenie aplikacji MFC w stylu eksploratora plików
Wiele aplikacji systemu Windows używa interfejsu użytkownika (UI) w Eksploratorze plików. Po ponownym uruchomieniu Eksploratora plików, na przykład pojawić aplikacji przy użyciu rozdzielacza pionowy pasek dzielenia obszaru klienckiego. Lewej obszaru klienckiego zapewnia nawigacji i funkcji przeglądania, i prawego obszaru klienckiego przedstawia szczegółowe informacje dotyczące zaznaczenie w okienku po lewej stronie. Po kliknięciu elementu w okienku po lewej stronie aplikacji repopulates okienku po prawej stronie. W aplikacji MDI, możesz użyć polecenia w **widoku** menu, aby zmienić poziom szczegółów wyświetlany w okienku po prawej stronie. (W SDI lub wiele dokumentów najwyższego poziomu aplikacji, można zmienić szczegóły, korzystając z przycisków paska narzędzi.)  
  
 Zawartość okienka zależą od aplikacji. W przeglądarce systemu plików okienka po lewej stronie zawiera hierarchiczny widok katalogów lub komputery lub grupy na komputerze, gdy folderów, pojedyncze pliki, lub maszyny i szczegółowe informacje o ich wyświetlone w okienku po prawej stronie. Zawartość nie muszą być jako plików. Może być wiadomości e-mail, raporty o błędach lub innych elementów w bazie danych.  
  
 Kreator tworzy następujące klasy dla Ciebie:  
  
-   **CLeftView** klasa definiuje w okienku po lewej stronie obszaru klienckiego. Zawsze jest pochodną [CTreeView —](../../mfc/reference/ctreeview-class.md).  
  
-   C*nazwa_projektu.nazwa_modułu.nazwa_procedury*widoku klasy definiuje okienku po prawej stronie obszaru klienckiego. Domyślnie, pochodzi z [clistview —](../../mfc/reference/clistview-class.md) , ale może być inny rodzaj widoku w zależności od klasy z **klasa podstawowa** na liście [wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony Kreator.  
  
 Wygenerowany aplikacji może mieć interfejs pojedynczego dokumentu (SDI), interfejsu wielu dokumentów (MDI) lub wielu architektura dokumentów najwyższego poziomu. Każde okno ramowe aplikacja tworzy pionowo dzieli się przy użyciu [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Kodowanie tego typu aplikacji jest podobny do kodowania normalne aplikacji MFC, która używa podziału, z wyjątkiem tego, że ten typ aplikacji ma sterującym widokach w ramach poszczególnych okienkach podziału.  
  
 Jeśli używasz domyślny widok listy w okienku po prawej stronie, Kreator tworzy dodatkowe menu opcji (w tylko aplikacje MDI) i przycisków paska narzędzi, aby przełączyć stylu widoku między duże ikony, małe ikony, listy i szczegółów trybów.  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Aby rozpocząć tworzenie wykonywalny MFC w stylu Eksploratora plików  
  
1.  Postępuj zgodnie z instrukcjami w [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  W Kreatorze aplikacji MFC [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) wybierz pozycję **Eksploratora plików** styl projektu.  
  
3.  Ustaw inne opcje, które chcesz na innych stronach kreatora.  
  
4.  Kliknij przycisk **Zakończ** do generowania szkielet aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Pochodne klasy widoków](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Opcje do wyboru przy projektowaniu aplikacji](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Tworzenie aplikacji MFC w stylu przeglądarki sieci Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [Tworzenie aplikacji MFC opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md)

