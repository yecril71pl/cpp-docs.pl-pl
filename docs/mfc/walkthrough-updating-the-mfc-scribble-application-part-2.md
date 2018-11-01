---
title: 'Wskazówki: aktualizowanie aplikacji bazgrołów MFC (część 2)'
ms.date: 09/20/2018
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: d618d79c50892523b3e4a71be163b8778402e48e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570342"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Wskazówki: aktualizowanie aplikacji bazgrołów MFC (część 2)

[Część 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) tego instruktażu pokazano, jak dodać wstążki Fluent pakietu Office do klasycznego Bazgroły aplikacji. Tej części przedstawiono sposób dodawania paneli Wstążki i formanty, które użytkownicy mogą używać zamiast menu i poleceń.

## <a name="prerequisites"></a>Wymagania wstępne

[Przykłady Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Dodawanie nowych paneli do wstążki](#addnewpanel)

- [Dodawanie pomocy panelu do wstążki](#addhelppanel)

- [Dodawanie panelu piórem do wstążki](#addpenpanel)

- [Dodawanie przycisku koloru do wstążki](#addcolorbutton)

- [Dodawanie członka kolorów do klasy dokumentów](#addcolormember)

- [Inicjowanie pióra i preferencji zapisywania](#initpensave)

##  <a name="addnewpanel"></a> Dodawanie nowych paneli do wstążki

Te kroki pokazują, jak dodać **widoku** panel, który zawiera dwa pola wyboru, które kontrolują widoczność paska narzędzi i pasek stanu, a także **okna** panel, który zawiera podział orientacji pionowej przycisk, który steruje tworzeniem i rozmieszczenie interfejsu wielu dokumentów (MDI) systemu Windows.

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Aby dodać do paska wstążki — panel widoku i oknie panelu

1. Utwórz zespół o nazwie `View`, który ma dwa pola wyboru, które Przełącz pasek stanu i narzędzi.

   1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij dwa **pola wyboru** do panelu.

   1. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `View`.

   1. Kliknij pierwsze pole wyboru, aby zmodyfikować jego właściwości. Zmiana **identyfikator** do `ID_VIEW_TOOLBAR` i **podpis** do `Toolbar`.

   1. Kliknij przycisk drugie pole wyboru, aby zmodyfikować jego właściwości. Zmiana **identyfikator** do `ID_VIEW_STATUS_BAR` i **podpis** do `Status Bar`.

1. Utwórz zespół o nazwie `Window` zawierający przycisk podziału. Gdy użytkownik kliknie przycisk podziału, w menu skrótów przedstawia trzy polecenia, które są już zdefiniowane w aplikacji bazgrołów.

   1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij **przycisk** do panelu.

   1. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Window`.

   1. Kliknij przycisk. Zmiana **podpis** do `Windows`, **klucze** do `w`, **indeksu duży obraz** do `1`, i **Tryb podziału** Aby `False`. Następnie kliknij przycisk wielokropka (**...** ) obok pozycji **elementów Menu** otworzyć **Edytor elementów** okno dialogowe.

   1. Kliknij przycisk **Dodaj** trzy razy, aby dodać trzy przyciski.

   1. Kliknij pierwszy przycisk, a następnie zmień **podpis** do `New Window`, i **identyfikator** do `ID_WINDOW_NEW`.

   1. Drugi przycisk, a następnie zmień **podpis** do `Cascade`, i **identyfikator** do `ID_WINDOW_CASCADE`.

   1. Kliknij trzeci przycisk, a następnie zmień **podpis** do `Tile`, i **identyfikator** do `ID_WINDOW_TILE_HORZ`.

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. **Widoku** i **okna** panele powinny być wyświetlane. Kliknij przyciski, aby upewnić się, że działają poprawnie.

##  <a name="addhelppanel"></a> Dodawanie pomocy panelu do wstążki

Teraz można przypisać dwa elementy menu, które są zdefiniowane w aplikacji bazgrołów przyciski wstążki, które są nazywane **tematy Pomocy** i **o Bazgroły**. Przyciski są dodawane do nowego panelu o nazwie **pomocy**.

### <a name="to-add-a-help-panel"></a>Aby dodać panel pomocy

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij dwa **przyciski** do panelu.

1. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Help`.

1. Kliknij pierwszy przycisk. Zmiana **podpis** do `Help Topics`, i **identyfikator** do `ID_HELP_FINDER`.

1. Drugi przycisk. Zmiana **podpis** do `About Scribble...`, i **identyfikator** do `ID_APP_ABOUT`.

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. A **pomocy** powinien zostać wyświetlony panel, który zawiera dwa przyciski wstążki.

   > [!IMPORTANT]
   > Po kliknięciu **tematy Pomocy** przycisku spowoduje otwarcie aplikacji bazgrołów skompresowanego pliku Pomocy HTML (chm) o nazwie *your_project_name*. chm. W związku z tym jeśli projekt nie ma nazwy Bazgroły, należy zmienić plik pomocy do nazwy projektu.

##  <a name="addpenpanel"></a> Dodawanie panelu piórem do wstążki

Teraz Dodaj panelu w celu wyświetlenia przycisków, które sterują grubość i kolor pióra. Ten panel zawiera pole wyboru, które jest przełączana między pióra grubości i alokowania elastycznego. Jego działanie przypomina z **Gruba linia** element menu w aplikacji bazgrołów.

Oryginalnej aplikacji bazgrołów umożliwia użytkownikowi wybranie szerokości pióra z okna dialogowego wyświetlanego, gdy użytkownik kliknie **szerokości pióra** w menu. Na Wstążce ma wystarczającą ilość miejsca dla nowych formantów, okno dialogowe można zastąpić przy użyciu dwóch pól kombi na Wstążce. Jedno pole kombi dostosowuje grubość pióra alokowania elastycznego, a pole kombi dostosowuje szerokość grubość pióra.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Aby dodać panel pióra i pole kombi pola do wstążki

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij **pole wyboru** oraz dwóch **pola kombi** do panelu.

1. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Pen`.

1. Kliknij pole wyboru. Zmiana **podpis** do `Use Thick`, i **identyfikator** do `ID_PEN_THICK_OR_THIN`.

1. Kliknij pierwsze pole kombi. Zmiana **podpis** do `Thin Pen`, **identyfikator** do `ID_PEN_THIN_WIDTH`, **typu** do `Drop List`, **danych** do `1;2;3;4;5;6;7;8;9;`, i **tekstu** do `2`.

1. Kliknij przycisk drugiego pola kombi. Zmiana **podpis** do `Thick Pen`, **identyfikator** do `ID_PEN_THICK_WIDTH`, **typu** do `Drop List`, **danych** do `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`, i **tekstu** do `5`.

1. Nowe pola kombi nie odnoszą się do wszystkie istniejące elementy menu, dlatego należy utworzyć element menu dla każdej opcji pióra.

   1. W **widok zasobów** otwarte okno **IDR_SCRIBBTYPE** zasobu menu.

   1. Kliknij przycisk **pióra** aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ `Thi&n Pen`.

   1. Kliknij prawym przyciskiem myszy tekst, który został wpisany, aby otworzyć **właściwości** okna, a następnie zmień identyfikator właściwości `ID_PEN_THIN_WIDTH`.

   1. Utwórz procedurę obsługi zdarzeń dla każdego elementu menu pióra. Kliknij prawym przyciskiem myszy **gr & n pióra** element menu, który zostanie utworzony, a następnie kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlana.

   1. W **listy klas** polu w kreatorze Wybierz **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować**. Polecenie tworzy program obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThinWidth`.

   1. Dodaj następujący kod do `CScribbleDoc::OnPenThinWidth`.

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

1. Następnie należy utworzyć menu elementu i programów obsługi grubość pióra.

   1. W **widok zasobów** otwarte okno **IDR_SCRIBBTYPE** zasobu menu.

   1. Kliknij przycisk **pióra** aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ `Thic&k Pen`.

   1. Kliknij prawym przyciskiem myszy tekst wpisany do wyświetlenia **właściwości** okna. Zmień właściwości Identyfikatora `ID_PEN_THICK_WIDTH`.

   1. Kliknij prawym przyciskiem myszy **grubość pióra** element menu, który zostanie utworzony, a następnie kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlana.

   1. W **listy klas** pola kreatora wybierz pozycję **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować**. Polecenie tworzy program obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThickWidth`.

   1. Dodaj następujący kod do `CScribbleDoc::OnPenThickWidth`.

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

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Powinny być wyświetlane nowe przyciski i pola kombi. Spróbuj Bazgroły za pomocą pióra szerokości.

##  <a name="addcolorbutton"></a> Dodawanie przycisku koloru do panelu pióra

Następnie dodaj [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) obiekt, który umożliwia użytkownikowi bazgrołów są oznaczone kolorem.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Aby dodać przycisk koloru do panelu pióra

1. Zanim dodasz przycisk koloru, Utwórz element menu dla niego. W **widok zasobów** otwarte okno **IDR_SCRIBBTYPE** zasobu menu. Kliknij przycisk **pióra** element menu, aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ `&Color`. Kliknij prawym przyciskiem myszy tekst wpisany do wyświetlenia **właściwości** okna. Zmień identyfikator, który ma `ID_PEN_COLOR`.

1. Teraz Dodaj przycisk koloru. Z **przybornika**, przeciągnij **przycisk koloru** do **pióra** panelu.

1. Kliknij przycisk koloru. Zmiana **podpis** do `Color`, **identyfikator** do `ID_PEN_COLOR`, **prosty wygląd** do `True`, **indeksu duży obraz** do `1`, i **Tryb podziału** do `False`.

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Nowy przycisk koloru powinien być wyświetlany na **pióra** panelu. Jednak nie można użyć, ponieważ nie ma jeszcze obsługi zdarzeń. Następne kroki pokazują, jak dodać program obsługi zdarzeń dla przycisku koloru.

##  <a name="addcolormember"></a> Dodawanie członka kolorów do klasy dokumentów

Ponieważ oryginalnej aplikacji bazgrołów nie ma kolor pióra, musisz napisać implementację dla nich. Do przechowywania na kolor pióra dokumentu, Dodaj nowy element członkowski do klasy dokumentu `CscribbleDoc`.

### <a name="to-add-a-color-member-to-the-document-class"></a>Aby dodać element członkowski kolorów do klasy dokumentów

1. W scribdoc.h w `CScribbleDoc` klasy, Znajdź `// Attributes` sekcji. Dodaj następujące wiersze kodu po definicji `m_nThickWidth` element członkowski danych.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Każdy dokument zawiera listę pociągnięć, że użytkownik ma już rysowania. Każdy obrys jest definiowany przez `CStroke` obiektu. `CStroke` Klasy nie zawiera informacji na temat koloru pióra, więc należy zmodyfikować klasy. W scribdoc.h w `CStroke` klasy, Dodaj następujące wiersze kodu po definicji `m_nPenWidth` element członkowski danych.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. W scribdoc.h, Dodaj nowy `CStroke` konstruktora, w której parametry Określ szerokość i kolor. Dodaj następujący wiersz kodu po `CStroke(UINT nPenWidth);` instrukcji.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. W scribdoc.cpp, Dodaj implementację nowej `CStroke` konstruktora. Dodaj następujący kod po wprowadzeniu w życie `CStroke::CStroke(UINT nPenWidth)` konstruktora.

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

1. Ustaw domyślny kolor pióra klasy dokumentu. W scribdoc.cpp, Dodaj następujące wiersze do `CScribbleDoc::InitDocument`po `m_nThickWidth = 5;` instrukcji.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. W scribdoc.cpp, Zmień w pierwszym wierszu `CScribbleDoc::NewStroke` metody do następującego.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Zmień ostatni wiersz `CScribbleDoc::ReplacePen` metody do następującego.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Możesz dodać `m_penColor` elementu członkowskiego w poprzednim kroku. Teraz Utwórz program obsługi zdarzeń dla przycisku koloru, który ustawia element członkowski.

   1. W **widok zasobów** okna, otwórz zasób menu IDR_SCRIBBTYPE.

   1. Kliknij prawym przyciskiem myszy **kolor** element menu i kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** pojawia się.

   1. W **listy klas** polu w kreatorze Wybierz **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować** przycisku. Polecenie tworzy `CScribbleDoc::OnPenColor` szkieletu program obsługi zdarzenia.

1. Zastąp klasy zastępczej dla `CScribbleDoc::OnPenColor` programu obsługi zdarzeń z następującym kodem.

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

1. Zapisz zmiany, a następnie tworzenie i uruchamianie aplikacji. Teraz możesz nacisnąć przycisk koloru i zmiana koloru pióra.

##  <a name="initpensave"></a> Inicjowanie pióra i preferencji zapisywania

Następnie można zainicjować, kolor i grubość pióra. Na koniec Zapisz i załadować koloru rysowania z pliku.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Aby zainicjować kontrolki na pasku wstążki

1. Zainicjuj pióra w pasku wstążki.

   Dodaj następujący kod do scribdoc.cpp, w `CScribbleDoc::InitDocument` metoda po `m_sizeDoc = CSize(200,200)` instrukcji.

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

1. Zapisz kolor Rysowanie w pliku. Dodaj następującą instrukcję, aby scribdoc.cpp, w `CStroke::Serialize` metoda po `ar << (WORD)m_nPenWidth;` instrukcji.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Na koniec Załaduj kolor rysowania z pliku. Dodaj następujący wiersz kodu, w `CStroke::Serialize` metoda po `m_nPenWidth = w;` instrukcji.

   ```cpp
   ar >> m_penColor;
   ```

1. Teraz Bazgroły w kolorze i zapisać w pliku rysunku.

## <a name="conclusion"></a>Wniosek

Klasa Scribble MFC aplikacji został zaktualizowany. Należy użyć w tym przewodniku jako przewodnika podczas modyfikowania istniejących aplikacji.

## <a name="see-also"></a>Zobacz też

[Przewodniki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
