---
title: 'Przykład: Wyświetlanie okna dialogowego za pomocą polecenia menu'
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 9b76d481bff6e98b915d71634dbf04a83a432736
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907744"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Przykład: Wyświetlanie okna dialogowego za pomocą polecenia menu

Ten temat zawiera następujące procedury:

- Wyświetl modalne okno dialogowe za pomocą polecenia menu.

- Wyświetl niemodalne okno dialogowe za pomocą polecenia menu.

Obie przykładowe procedury są przeznaczone dla aplikacji MFC i będą działały w aplikacji utworzonej za pomocą [Kreatora aplikacji MFC](../mfc/reference/mfc-application-wizard.md).

W procedurach użyto następujących nazw i wartości:

|Element|Nazwa lub wartość|
|----------|-------------------|
|Aplikacja|DisplayDialog|
|Polecenie menu|Polecenie testowe w menu Widok; Identyfikator polecenia = ID_VIEW_TEST|
|Okno dialogowe|Test — okno dialogowe; Class = CTestDialog; Plik nagłówka = TestDialog. h; Zmienna = testdlg, ptestdlg|
|Procedura obsługi polecenia|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Aby wyświetlić modalne okno dialogowe

1. Utwórz polecenie menu; Zobacz [Tworzenie menu lub elementów menu](../windows/creating-a-menu.md).

1. Utwórz okno dialogowe; Zobacz [Uruchamianie edytora okien dialogowych](../windows/creating-a-new-dialog-box.md).

1. Dodaj klasę do okna dialogowego. Aby uzyskać więcej informacji [, zobacz Dodawanie klasy](../ide/adding-a-class-visual-cpp.md) .

1. W **Widok klasy**wybierz klasę dokumentu (CDisplayDialogDoc). W oknie **Właściwości** kliknij przycisk **zdarzenia** . Kliknij dwukrotnie identyfikator polecenia menu (ID_VIEW_TEST). Następnie kliknij strzałkę w dół i wybierz pozycję  **\<Dodaj > OnViewTest**.

   Jeśli dodano polecenie menu do komputera mainframe aplikacji MDI, zamiast tego wybierz klasę aplikacji (CDisplayDialogApp).

1. Dodaj następującą instrukcję include do CDisplayDialogDoc. cpp (lub CDisplayDialogApp. cpp) po istniejącej instrukcji include:

   ```cpp
   #include "TestDialog.h"
   ```

1. Dodaj następujący kod w `OnViewTest` celu zaimplementowania funkcji:

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();  
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Aby wyświetlić niemodalne okno dialogowe

1. Wykonaj pierwsze cztery kroki, aby wyświetlić modalne okno dialogowe, z wyjątkiem zaznaczania klasy View (CDisplayDialogView) w kroku 4.

1. Edytuj DisplayDialogView. h:

   - Zadeklaruj klasę okna dialogowego poprzedzającą pierwszą deklarację klasy:

   ```cpp
   class CTestDialog;
   ```

   - Zadeklaruj wskaźnik do okna dialogowego po sekcji Public Attributes:

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Edytuj DisplayDialogView. cpp:

   - Dodaj następującą instrukcję include po istniejących instrukcjach include:

   ```cpp
   #include "TestDialog.h"
   ```

   - Dodaj następujący kod do konstruktora:

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Dodaj następujący kod do destruktora:

   ```cpp
   delete m_pTestDlg;
   ```

   - Dodaj następujący kod w `OnViewTest` celu zaimplementowania funkcji:

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
