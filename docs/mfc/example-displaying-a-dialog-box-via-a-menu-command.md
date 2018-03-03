---
title: "Przykład: Wyświetlanie okna dialogowego za pomocą polecenia Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2715e1b64c1565d122f6eec012a8a33c2525ac9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu
Ten temat zawiera procedury:  
  
-   Wyświetla modalne okno dialogowe za pomocą poleceń menu.  
  
-   Wyświetl okno niemodalnego okna dialogowego za pomocą poleceń menu.  
  
 Zarówno przykładowe procedury dotyczą aplikacji MFC i będzie działać w aplikacji można utworzyć z [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md).  
  
 Procedury należy użyć następujących nazwy i wartości:  
  
|Element|Nazwa lub wartość|  
|----------|-------------------|  
|Aplikacja|DisplayDialog|  
|Polecenia menu|Polecenie testu w menu Widok. Identyfikator polecenia = ID_VIEW_TEST|  
|Okno dialogowe|Okno dialogowe testu; Klasa = CTestDialog; Plik nagłówka = TestDialog.h; Zmienna = testdlg, ptestdlg|  
|Program obsługi poleceń|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>Aby wyświetlić modalne okno dialogowe  
  
1.  Utwórz polecenie; zobacz [tworzenie menu lub elementów Menu](../windows/creating-a-menu.md).  
  
2.  Utwórz okno dialogowe; zobacz [uruchamiania edytora okien dialogowych](../windows/creating-a-new-dialog-box.md).  
  
3.  Dodaj klasę z okna dialogowego. Zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md) Aby uzyskać więcej informacji.  
  
4.  W **widoku klasy**, wybierz klasę dokumentu (CDisplayDialogDoc). W **właściwości** okna, kliknij przycisk **zdarzenia** przycisku. Kliknij dwukrotnie identyfikator polecenia menu (ID_VIEW_TEST) w lewym okienku **właściwości** i zaznacz **polecenia**. W okienku po prawej stronie, kliknij strzałkę w dół i wybierz  **\<Dodaj > OnViewTest**.  
  
     Jeśli polecenie menu do mainframe aplikacji MDI, należy wybrać klasę aplikacji (CDisplayDialogApp).  
  
5.  Dodaj następujące dołączania instrukcji CDisplayDialogDoc.cpp (lub CDisplayDialogApp.cpp) po istniejącej instrukcji #include:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  Dodaj następujący kod do `OnViewTest` do implementowania funkcji:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>Aby wyświetlić niemodalne okno dialogowe  
  
1.  Czy pierwsze cztery kroki, aby wyświetlić modalne okno dialogowe, z wyjątkiem wybierz klasę widoku (CDisplayDialogView) w kroku 4.  
  
2.  Edytuj DisplayDialogView.h:  
  
    -   Zadeklarować klasy okno dialogowe, poprzedzających w pierwszej klasie deklaracji:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   Zadeklarować wskaźnika do okna dialogowego po sekcji publicznej atrybuty:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  Edytuj DisplayDialogView.cpp:  
  
    -   Dodaj następujące zawierać instrukcji po instrukcji #include istniejące:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   Dodaj następujący kod do konstruktora:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   Dodaj następujący kod do destruktor:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   Dodaj następujący kod do `OnViewTest` do implementowania funkcji:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 Ponadto zawiera następujący artykuł bazy wiedzy Knowledge Base:  
  
-   Q251059: Porada: Podaj własną nazwę klasy okna dla okna dialogowego MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Modalne i niemodalne okna dialogowe](../mfc/modal-and-modeless-dialog-boxes.md)

