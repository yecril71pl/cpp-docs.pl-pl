---
title: 'Wskazówki: aktualizowanie aplikacji bazgrołów MFC (część 2)'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360226"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Wskazówki: aktualizowanie aplikacji bazgrołów MFC (część 2)

[Część 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) tego przewodnika pokazała, jak dodać Wstążkę Office Fluent do klasycznej aplikacji Bazgroły. W tej części pokazano, jak dodać panele wstążki i formanty, których użytkownicy mogą używać zamiast menu i poleceń.

## <a name="prerequisites"></a>Wymagania wstępne

[Przykłady Visual C++](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Dodawanie nowych paneli do Wstążki](#addnewpanel)

- [Dodawanie Panelu pomocy do Wstążki](#addhelppanel)

- [Dodawanie panelu pióra do Wstążki](#addpenpanel)

- [Dodawanie przycisku koloru do Wstążki](#addcolorbutton)

- [Dodawanie elementu członkowskiego koloru do klasy dokumentu](#addcolormember)

- [Inicjowanie piór i preferencje zapisywania](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>Dodawanie nowych paneli do Wstążki

W tych krokach pokazano, jak dodać panel **Widok** zawierający dwa pola wyboru, które sterują widocznością paska narzędzi i paska stanu, a także panel **Window** zawierający pionowo zorientowany przycisk podziału, który steruje tworzeniem i rozmieszczeniem okien interfejsu wielu dokumentów (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Aby dodać panel Widok i panel Okno do paska wstążki

1. Utwórz panel `View`o nazwie , który ma dwa pola wyboru, które przełączają pasek stanu i pasek narzędzi.

   1. Z **przybornika**przeciągnij **panel** do kategorii **Strona** główna. Następnie przeciągnij dwa **pola wyboru** do panelu.

   1. Kliknij panel, aby zmodyfikować jego właściwości. Zmień **Caption** podpis `View`na .

   1. Kliknij pierwsze pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** `ID_VIEW_TOOLBAR` i **podpis** na `Toolbar`.

   1. Kliknij drugie pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** `ID_VIEW_STATUS_BAR` i **podpis** na `Status Bar`.

1. Utwórz panel `Window` o nazwie, który ma przycisk podziału. Gdy użytkownik kliknie przycisk podziału, w menu skrótów zostaną wyświetlone trzy polecenia, które są już zdefiniowane w aplikacji Bazgroły.

   1. Z **przybornika**przeciągnij **panel** do kategorii **Strona** główna. Następnie przeciągnij **przycisk** na panel.

   1. Kliknij panel, aby zmodyfikować jego właściwości. Zmień **Caption** podpis `Window`na .

   1. Kliknij przycisk. Zmień **Caption** podpis `Windows`na `w`, **Klawisze** `1`do , Duży **indeks obrazu** do , i **Tryb podziału** do `False`. Następnie kliknij wielokropek (**...**) obok **pozycji Elementy menu,** aby otworzyć okno dialogowe Edytor **elementów.**

   1. Kliknij **przycisk Dodaj** trzy razy, aby dodać trzy przyciski.

   1. Kliknij pierwszy przycisk, **Caption** a `New Window`następnie zmień caption `ID_WINDOW_NEW`na , i **ID** na .

   1. Kliknij drugi przycisk, **Caption** a `Cascade`następnie zmień caption `ID_WINDOW_CASCADE`na , i **ID** na .

   1. Kliknij trzeci przycisk, **Caption** a `Tile`następnie zmień caption `ID_WINDOW_TILE_HORZ`na , i **ID** na .

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Powinny być wyświetlane panele **Widok** i **Okno.** Kliknij przyciski, aby potwierdzić, że działają poprawnie.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>Dodawanie Panelu pomocy do Wstążki

Teraz można przypisać dwa elementy menu, które są zdefiniowane w aplikacji Bazgroły do przycisków wstążki, które są nazywane **Tematy pomocy** i **O bazgroły**. Przyciski zostaną dodane do nowego panelu o nazwie **Pomoc**.

### <a name="to-add-a-help-panel"></a>Aby dodać panel Pomocy

1. Z **przybornika**przeciągnij **panel** do kategorii **Strona** główna. Następnie przeciągnij dwa **przyciski** na panel.

1. Kliknij panel, aby zmodyfikować jego właściwości. Zmień **Caption** podpis `Help`na .

1. Kliknij pierwszy przycisk. Zmień **Caption** podpis `Help Topics`na **id** na `ID_HELP_FINDER`.

1. Kliknij drugi przycisk. Zmień **Caption** podpis `About Scribble...`na **id** na `ID_APP_ABOUT`.

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Powinien zostać wyświetlony panel **Pomocy** zawierający dwa przyciski wstążki.

   > [!IMPORTANT]
   > Po kliknięciu przycisku **Tematy pomocy** aplikacja Bazgroły otwiera skompresowany plik pomocy HTML (chm) o nazwie *your_project_name*.chm. W związku z tym jeśli projekt nie ma nazwy Bazgroły, należy zmienić nazwę pliku pomocy do nazwy projektu.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>Dodawanie panelu pióra do Wstążki

Teraz dodaj panel, aby wyświetlić przyciski, które kontrolują grubość i kolor pióra. Ten panel zawiera pole wyboru przełączane między grubymi i cienkimi długopisami. Jego funkcjonalność przypomina funkcję elementu menu **Gruba linia** w aplikacji Bazgroły.

Oryginalna aplikacja Bazgroły umożliwia użytkownikowi wybranie szerokości pióra z okna dialogowego wyświetlanego po kliknięciu w menu **opcji Szerokość pióra.** Ponieważ pasek wstążki ma dużo miejsca na nowe kontrolki, można zastąpić okno dialogowe za pomocą dwóch pól kombi na wstążce. Jedno pole kombi dostosowuje szerokość cienkiego pióra, a drugie pole kombi dostosowuje szerokość grubego pióra.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Aby dodać panel Pióro i pola kombi do wstążki

1. Z **przybornika**przeciągnij **panel** do kategorii **Strona** główna. Następnie przeciągnij **pole wyboru** i dwa **pola kombi** do panelu.

1. Kliknij panel, aby zmodyfikować jego właściwości. Zmień **Caption** podpis `Pen`na .

1. Kliknij to pole wyboru. Zmień **Caption** podpis `Use Thick`na **id** na `ID_PEN_THICK_OR_THIN`.

1. Kliknij pierwsze pole kombi. Zmień **Caption** podpis `Thin Pen`na , `ID_PEN_THIN_WIDTH` **ID** , `1;2;3;4;5;6;7;8;9;` **Wpisz** na `Drop List` `2`, **Dane** do , i **Tekst** do .

1. Kliknij drugie pole kombi. Zmień **Caption** podpis `Thick Pen`na , `ID_PEN_THICK_WIDTH` **ID** , `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;` **Wpisz** na `Drop List` `5`, **Dane** do , i **Tekst** do .

1. Nowe pola kombi nie odpowiadają żadnym istniejącym elementom menu, dlatego należy utworzyć element menu dla każdej opcji pióra.

   1. W oknie **Widok zasobów** otwórz zasób menu **IDR_SCRIBBTYPE.**

   1. Kliknij **pozycję Pióro,** aby otworzyć menu pióra. Następnie kliknij przycisk `Thi&n Pen`Wpisz **tutaj** i wpisz .

   1. Kliknij prawym przyciskiem myszy wpisany tekst, aby otworzyć okno **Właściwości,** `ID_PEN_THIN_WIDTH`a następnie zmień właściwość ID na .

   1. Utwórz program obsługi zdarzeń dla każdego elementu menu pióra. Kliknij prawym przyciskiem myszy utworzony element menu **Thi&n Pióro,** a następnie kliknij polecenie **Dodaj program obsługi zdarzeń**. Zostanie wyświetlony **Kreator obsługi zdarzeń.**

   1. W polu **listy Klasa** w kreatorze wybierz pozycję **CScribbleDoc,** a następnie kliknij pozycję **Dodaj i edytuj**. Polecenie tworzy program obsługi `CScribbleDoc::OnPenThinWidth`zdarzeń o nazwie .

   1. Dodaj następujący kod `CScribbleDoc::OnPenThinWidth`do pliku .

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Następnie utwórz element menu i programy obsługi zdarzeń dla grubego pióra.

   1. W oknie **Widok zasobów** otwórz zasób menu **IDR_SCRIBBTYPE.**

   1. Kliknij **pozycję Pióro,** aby otworzyć menu pióra. Następnie kliknij przycisk `Thic&k Pen`Wpisz **tutaj** i wpisz .

   1. Kliknij prawym przyciskiem myszy wpisany tekst, aby wyświetlić okno **Właściwości.** Zmień właściwość ID na `ID_PEN_THICK_WIDTH`.

   1. Kliknij prawym przyciskiem myszy utworzony element menu **Grube pióro,** a następnie kliknij polecenie **Dodaj program obsługi zdarzeń**. Zostanie wyświetlony **Kreator obsługi zdarzeń.**

   1. W polu **listy Klasa** kreatora wybierz pozycję **CScribbleDoc,** a następnie kliknij pozycję **Dodaj i edytuj**. Polecenie tworzy program obsługi `CScribbleDoc::OnPenThickWidth`zdarzeń o nazwie .

   1. Dodaj następujący kod `CScribbleDoc::OnPenThickWidth`do pliku .

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Powinny być wyświetlane nowe przyciski i pola kombi. Spróbuj użyć różnych szerokości pióra do bazgrołów.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>Dodawanie przycisku koloru do panelu pióra

Następnie dodaj [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) obiektu, który pozwala użytkownikowi bazgroły w kolorze.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Aby dodać kolorowy przycisk do panelu Pióro

1. Przed dodaniem przycisku koloru utwórz dla niego element menu. W oknie **Widok zasobów** otwórz zasób menu **IDR_SCRIBBTYPE.** Kliknij pozycję menu **Pióro,** aby otworzyć menu pióra. Następnie kliknij przycisk `&Color`Wpisz **tutaj** i wpisz . Kliknij prawym przyciskiem myszy wpisany tekst, aby wyświetlić okno **Właściwości.** Zmień identyfikator na `ID_PEN_COLOR`.

1. Teraz dodaj przycisk koloru. W **przyborniku**przeciągnij **przycisk kolor** na panel **Pióro.**

1. Kliknij przycisk koloru. Zmień **Caption** podpis `Color`na , `ID_PEN_COLOR` **ID** `True`, **Prosty wygląd,** Duży indeks `False` **obrazu** do `1`, i tryb **podziału** na .

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Nowy przycisk koloru powinien być wyświetlany na panelu **Pióro.** Jednak nie można go używać, ponieważ nie ma jeszcze programu obsługi zdarzeń. Następne kroki pokazują, jak dodać program obsługi zdarzeń dla przycisku kolor.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>Dodawanie elementu członkowskiego koloru do klasy dokumentu

Ponieważ oryginalna aplikacja Bazgroły nie ma kolorowych piór, należy napisać dla nich implementację. Aby zapisać kolor pióra dokumentu, dodaj nowy element `CscribbleDoc`członkowski do klasy dokumentu, .

### <a name="to-add-a-color-member-to-the-document-class"></a>Aby dodać element członkowski koloru do klasy dokumentu

1. W scribdoc.h, `CScribbleDoc` w klasie, `// Attributes` znajdź sekcję. Dodaj następujące wiersze kodu po `m_nThickWidth` definicji elementu członkowskiego danych.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Każdy dokument zawiera listę stokes, że użytkownik już narysował. Każdy obrys `CStroke` jest definiowany przez obiekt. Klasa `CStroke` nie zawiera informacji o kolorze pióra, więc należy zmodyfikować klasę. W pliku scribdoc.h `CStroke` w klasie dodaj następujące wiersze kodu `m_nPenWidth` po definicji elementu członkowskiego danych.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. W pliku scribdoc.h `CStroke` dodaj nowego konstruktora, którego parametry określają szerokość i kolor. Dodaj następujący wiersz kodu `CStroke(UINT nPenWidth);` po instrukcji.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. W pliku scribdoc.cpp dodaj implementację nowego `CStroke` konstruktora. Dodaj następujący kod po implementacji konstruktora. `CStroke::CStroke(UINT nPenWidth)`

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Zmień drugi wiersz `CStroke::DrawStroke` metody w następujący sposób.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Ustawianie domyślnego koloru pióra dla klasy dokumentu. W pliku scribdoc.cpp dodaj `CScribbleDoc::InitDocument`następujące wiersze do , po `m_nThickWidth = 5;` instrukcji.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. W pliku scribdoc.cpp zmień pierwszy `CScribbleDoc::NewStroke` wiersz metody na następujący.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Zmień ostatni wiersz `CScribbleDoc::ReplacePen` metody na następujący.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Element członkowski `m_penColor` został dodany w poprzednim kroku. Teraz utwórz program obsługi zdarzeń dla przycisku kolor, który ustawia element członkowski.

   1. W oknie **Widok zasobów** otwórz zasób menu IDR_SCRIBBTYPE.

   1. Kliknij prawym przyciskiem myszy element menu **Kolor** i kliknij polecenie **Dodaj program obsługi zdarzeń**. Zostanie **wyświetlony Kreator obsługi zdarzeń.**

   1. W polu **listy Klasa** w kreatorze wybierz pozycję **CScribbleDoc,** a następnie kliknij przycisk **Dodaj i edytuj.** Polecenie tworzy `CScribbleDoc::OnPenColor` skrót programu obsługi zdarzeń.

1. Zastąp `CScribbleDoc::OnPenColor` skrót dla programu obsługi zdarzeń następującym kodem.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Teraz możesz nacisnąć przycisk koloru i zmienić kolor pióra.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>Inicjowanie piór i preferencje zapisywania

Następnie należy zainicjować kolor i szerokość pisaków. Na koniec zapisz i załaduj rysunek kolorowy z pliku.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Aby zainicjować formanty na pasku wstążki

1. Zainicjować pióra na pasku wstążki.

   Dodaj następujący kod do scribdoc.cpp, w `CScribbleDoc::InitDocument` `m_sizeDoc = CSize(200,200)` metodzie, po instrukcji.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. Zapisywanie rysunku kolorowego w pliku. Dodaj następującą instrukcję do scribdoc.cpp, w metodzie, `CStroke::Serialize` po `ar << (WORD)m_nPenWidth;` instrukcji.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Na koniec załaduj rysunek kolorowy z pliku. Dodaj następujący wiersz kodu, `CStroke::Serialize` w metodzie, po `m_nPenWidth = w;` instrukcji.

   ```cpp
   ar >> m_penColor;
   ```

1. Teraz bazgroł w kolorze i zapisz rysunek w pliku.

## <a name="conclusion"></a>Podsumowanie

Zaktualizowano aplikację MFC Scribble. Użyj tego przewodnika jako przewodnika podczas modyfikowania istniejących aplikacji.

## <a name="see-also"></a>Zobacz też

[Wskazówki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
