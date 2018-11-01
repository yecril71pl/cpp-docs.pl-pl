---
title: 'Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu'
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
ms.openlocfilehash: 830ba27945ce8da2abd52c7f29d786d098113151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483489"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu

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

   [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

1. Dodaj następujący kod do `OnViewTest` do zaimplementowania funkcji:

   [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]

### <a name="to-display-a-modeless-dialog-box"></a>Aby wyświetlić niemodalnego okna dialogowego

1. Wykonaj pierwsze cztery kroki, aby wyświetlić okno modalne okno dialogowe, z wyjątkiem w kroku 4 Wybierz widok klasy (CDisplayDialogView).

1. Edytuj DisplayDialogView.h:

   - Zadeklaruj klasy pole okien dialogowych poprzedzających najwyższej klasy deklaracji:

         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]

   - Deklarowanie wskaźnika do okna dialogowego po sekcji publicznej w atrybuty:

         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]

1. Edytuj DisplayDialogView.cpp:

   - Dodaj następujące instrukcję #include po istniejącej instrukcji #include:

         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

   - Dodaj następujący kod do konstruktora:

         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]

   - Dodaj następujący kod do destruktor:

         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]

   - Dodaj następujący kod do `OnViewTest` do zaimplementowania funkcji:

         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Modalne i niemodalne okna dialogowe](../mfc/modal-and-modeless-dialog-boxes.md)
