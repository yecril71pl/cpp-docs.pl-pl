---
title: 'Przykład: Wyświetlanie okna dialogowego za pomocą polecenia Menu'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 1e730125e47609f0bf87814b32962336cb752b04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173310"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Przykład: Wyświetlanie okna dialogowego za pomocą polecenia Menu

Ten temat zawiera procedury, aby:

- Wyświetla modalne okno dialogowe za pomocą polecenia menu.

- Wyświetl niemodalnego okna dialogowego za pomocą polecenia menu.

Zarówno przykładowe procedury dotyczą aplikacjach MFC i będzie działać w aplikacji możesz utworzyć przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md).

Procedury należy użyć następujących nazw i wartości:

|Element|Nazwa lub wartość|
|----------|-------------------|
|Aplikacja|DisplayDialog|
|Polecenia menu|Polecenie Test w menu Widok. Identyfikator polecenia = ID_VIEW_TEST|
|Okno dialogowe|Okno dialogowe testu; Klasa = CTestDialog; Plik nagłówkowy = TestDialog.h; Zmienna = testdlg, ptestdlg|
|Program obsługi poleceń|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Aby wyświetlić okno modalne okno dialogowe

1. Utwórz polecenie menu; zobacz [tworzenie menu lub elementy Menu](../windows/creating-a-menu.md).

1. Tworzenie okna dialogowego; zobacz [uruchomienie edytora okien dialogowych](../windows/creating-a-new-dialog-box.md).

1. Dodaj klasę dla usługi, okno dialogowe. Zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md) Aby uzyskać więcej informacji.

1. W **Widok klas**, wybierz klasę dokumentu (CDisplayDialogDoc). W **właściwości** okna, kliknij przycisk **zdarzenia** przycisku. Kliknij dwukrotnie identyfikator polecenia menu (ID_VIEW_TEST) w lewym okienku **właściwości** okna, a następnie wybierz pozycję **polecenia**. W okienku po prawej stronie, kliknij strzałkę w dół i wybierz pozycję  **\<Dodaj > OnViewTest**.

   Jeśli polecenie menu jest dodawany do komputera mainframe aplikacji MDI, należy wybrać klasę aplikacji (CDisplayDialogApp).

1. Dodaj następujące dołączania instrukcji CDisplayDialogDoc.cpp (lub CDisplayDialogApp.cpp) po istniejącej instrukcji #include:

   ```cpp
   #include "TestDialog.h"
   ```

1. Dodaj następujący kod do `OnViewTest` do zaimplementowania funkcji:

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();  
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Aby wyświetlić niemodalnego okna dialogowego

1. Wykonaj pierwsze cztery kroki, aby wyświetlić okno modalne okno dialogowe, z wyjątkiem w kroku 4 Wybierz widok klasy (CDisplayDialogView).

1. Edytuj DisplayDialogView.h:

   - Zadeklaruj klasy pole okien dialogowych poprzedzających najwyższej klasy deklaracji:

   ```cpp
   class CTestDialog;
   ```

   - Deklarowanie wskaźnika do okna dialogowego po sekcji publicznej w atrybuty:

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Edit DisplayDialogView.cpp:

   - Dodaj następujące instrukcję #include po istniejącej instrukcji #include:

   ```cpp
   #include "TestDialog.h"
   ```

   - Dodaj następujący kod do konstruktora:

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Dodaj następujący kod do destruktor:

   ```cpp
   delete m_pTestDlg;
   ```

   - Dodaj następujący kod do `OnViewTest` do zaimplementowania funkcji:

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW); 
   ```

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Modalne i niemodalne okna dialogowe](../mfc/modal-and-modeless-dialog-boxes.md)
