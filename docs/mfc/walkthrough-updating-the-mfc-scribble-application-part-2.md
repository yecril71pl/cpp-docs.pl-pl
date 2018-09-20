---
title: 'Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 2) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 351aea09376d6cba7f091828225fd337fa3f68e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423182"
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

   2. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `View`.

   3. Kliknij pierwsze pole wyboru, aby zmodyfikować jego właściwości. Zmiana **identyfikator** do `ID_VIEW_TOOLBAR` i **podpis** do `Toolbar`.

   4. Kliknij przycisk drugie pole wyboru, aby zmodyfikować jego właściwości. Zmiana **identyfikator** do `ID_VIEW_STATUS_BAR` i **podpis** do `Status Bar`.

2. Utwórz zespół o nazwie `Window` zawierający przycisk podziału. Gdy użytkownik kliknie przycisk podziału, w menu skrótów przedstawia trzy polecenia, które są już zdefiniowane w aplikacji bazgrołów.

   1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij **przycisk** do panelu.

   2. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Window`.

   3. Kliknij przycisk. Zmiana **podpis** do `Windows`, **klucze** do `w`, **indeksu duży obraz** do `1`, i **Tryb podziału** Aby `False`. Następnie kliknij przycisk wielokropka (**...** ) obok pozycji **elementów Menu** otworzyć **Edytor elementów** okno dialogowe.

   4. Kliknij przycisk **Dodaj** trzy razy, aby dodać trzy przyciski.

   5. Kliknij pierwszy przycisk, a następnie zmień **podpis** do `New Window`, i **identyfikator** do `ID_WINDOW_NEW`.

   6. Drugi przycisk, a następnie zmień **podpis** do `Cascade`, i **identyfikator** do `ID_WINDOW_CASCADE`.

   7. Kliknij trzeci przycisk, a następnie zmień **podpis** do `Tile`, i **identyfikator** do `ID_WINDOW_TILE_HORZ`.

3. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. **Widoku** i **okna** panele powinny być wyświetlane. Kliknij przyciski, aby upewnić się, że działają poprawnie.

[[Sekcje](#top)]

##  <a name="addhelppanel"></a> Dodawanie pomocy panelu do wstążki

Teraz można przypisać dwa elementy menu, które są zdefiniowane w aplikacji bazgrołów przyciski wstążki, które są nazywane **tematy Pomocy** i **o Bazgroły**. Przyciski są dodawane do nowego panelu o nazwie **pomocy**.

### <a name="to-add-a-help-panel"></a>Aby dodać panel pomocy

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij dwa **przyciski** do panelu.

2. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Help`.

3. Kliknij pierwszy przycisk. Zmiana **podpis** do `Help Topics`, i **identyfikator** do `ID_HELP_FINDER`.

4. Drugi przycisk. Zmiana **podpis** do `About Scribble...`, i **identyfikator** do `ID_APP_ABOUT`.

5. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. A **pomocy** powinien zostać wyświetlony panel, który zawiera dwa przyciski wstążki.

   > [!IMPORTANT]
   > Po kliknięciu **tematy Pomocy** przycisku spowoduje otwarcie aplikacji bazgrołów skompresowanego pliku Pomocy HTML (chm) o nazwie *your_project_name*. chm. W związku z tym jeśli projekt nie ma nazwy Bazgroły, należy zmienić plik pomocy do nazwy projektu.

[[Sekcje](#top)]

##  <a name="addpenpanel"></a> Dodawanie panelu piórem do wstążki

Teraz Dodaj panelu w celu wyświetlenia przycisków, które sterują grubość i kolor pióra. Ten panel zawiera pole wyboru, które jest przełączana między pióra grubości i alokowania elastycznego. Jego działanie przypomina z **Gruba linia** element menu w aplikacji bazgrołów.

Oryginalnej aplikacji bazgrołów umożliwia użytkownikowi wybranie szerokości pióra z okna dialogowego wyświetlanego, gdy użytkownik kliknie **szerokości pióra** w menu. Na Wstążce ma wystarczającą ilość miejsca dla nowych formantów, okno dialogowe można zastąpić przy użyciu dwóch pól kombi na Wstążce. Jedno pole kombi dostosowuje grubość pióra alokowania elastycznego, a pole kombi dostosowuje szerokość grubość pióra.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Aby dodać panel pióra i pole kombi pola do wstążki

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Następnie przeciągnij **pole wyboru** oraz dwóch **pola kombi** do panelu.

2. Kliknij panel, aby zmodyfikować jego właściwości. Zmiana **podpis** do `Pen`.

3. Kliknij pole wyboru. Zmiana **podpis** do `Use Thick`, i **identyfikator** do `ID_PEN_THICK_OR_THIN`.

4. Kliknij pierwsze pole kombi. Zmiana **podpis** do `Thin Pen`, **identyfikator** do `ID_PEN_THIN_WIDTH`, **tekstu** do `2`, **typu** do `Drop List`, i **danych** do `1;2;3;4;5;6;7;8;9;`.

5. Kliknij przycisk drugiego pola kombi. Zmiana **podpis** do `Thick Pen`, **identyfikator** do `ID_PEN_THICK_WIDTH`, **tekstu** do `5`, **typu** do `Drop List`, i **danych** do `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`.

6. Nowe pola kombi nie odpowiadają wszystkie istniejące elementy menu. W związku z tym należy utworzyć element menu dla każdej opcji pióra.

   1. W **widok zasobów** okna, otwórz zasób menu IDR_SCRIBBTYPE.

   2. Kliknij przycisk **pióra** otworzyć p**en** menu. Następnie kliknij przycisk **typu w tym miejscu** i typ `Thi&n Pen`.

   3. Kliknij prawym przyciskiem myszy tekst, który po prostu wpisane w celu otwarcia **właściwości** okna, a następnie zmień identyfikator właściwości `ID_PEN_THIN_WIDTH`.

   4. Należy także utworzyć program obsługi zdarzeń dla każdego elementu menu pióra. Kliknij prawym przyciskiem myszy **gr & n pióra** element menu, który właśnie utworzony, a następnie kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlana.

   5. W **listy klas** polu w kreatorze Wybierz **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować**. Spowoduje to utworzenie obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThinWidth`.

   6. Dodaj następujący kod do `CScribbleDoc::OnPenThinWidth`.

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
        m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));
    }

    // Create a new pen using the selected width
    ReplacePen();
    ```

7. Następnie należy utworzyć menu elementu i programów obsługi grubość pióra.

   1. W **widok zasobów** okna, otwórz zasób menu IDR_SCRIBBTYPE.

   2. Kliknij przycisk **pióra** aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ `Thic&k Pen`.

   3. Kliknij prawym przyciskiem myszy tekst wpisany tylko do wyświetlania **właściwości** okna. Zmień właściwości Identyfikatora `ID_PEN_THICK_WIDTH`.

   4. Kliknij prawym przyciskiem myszy **grubość pióra** element menu, który właśnie utworzony, a następnie kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlana.

   5. W **listy klas** pola kreatora wybierz pozycję **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować**. Spowoduje to utworzenie obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThickWidth`.

   6. Dodaj następujący kod do `CScribbleDoc::OnPenThickWidth`.

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
          m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));
      }

      // Create a new pen using the selected width
      ReplacePen();
      ```

8. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Powinny być wyświetlane nowe przyciski i pola kombi. Spróbuj Bazgroły za pomocą pióra szerokości.

[[Sekcje](#top)]

##  <a name="addcolorbutton"></a> Dodawanie przycisku koloru do panelu pióra

Następnie dodaj [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) obiekt, który umożliwia użytkownikowi bazgrołów są oznaczone kolorem.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Aby dodać przycisk koloru do panelu pióra

1. Zanim dodasz przycisk koloru, Utwórz element menu dla niego. W **widok zasobów** okna, otwórz zasób menu IDR_SCRIBBTYPE. Kliknij przycisk **pióra** element menu, aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ `&Color`. Kliknij prawym przyciskiem myszy tekst wpisany tylko do wyświetlania **właściwości** okna. Zmień identyfikator, który ma `ID_PEN_COLOR`.

2. Teraz Dodaj przycisk koloru. Z **przybornika**, przeciągnij **przycisk koloru** do **pióra** panelu.

3. Kliknij przycisk koloru. Zmiana **podpis** do `Color`, **identyfikator** do `ID_PEN_COLOR`, **SimpleLook** do `True`, **indeksu duży obraz** do `1`, i **Tryb podziału** do `False`.

4. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Nowy przycisk koloru powinien być wyświetlany na **pióra** panelu. Jednak nie można użyć, ponieważ nie ma jeszcze obsługi zdarzeń. Następne kroki pokazują, jak dodać program obsługi zdarzeń dla przycisku koloru.

[[Sekcje](#top)]

##  <a name="addcolormember"></a> Dodawanie członka kolorów do klasy dokumentów

Ponieważ oryginalnej aplikacji bazgrołów nie ma kolor pióra, musisz napisać implementację dla nich. Aby przechowywać na kolor pióra dokumentu, Dodaj nowego członka do klasy dokumentów `CscribbleDoc.`

### <a name="to-add-a-color-member-to-the-document-class"></a>Aby dodać element członkowski kolorów do klasy dokumentów

1. W scribdoc.h w `CScribbleDoc` klasy, Znajdź `// Attributes` sekcji. Dodaj następujące wiersze kodu po definicji `m_nThickWidth` element członkowski danych.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

2. Każdy dokument zawiera listę pociągnięć, że użytkownik ma już rysowania. Każdy obrys jest definiowany przez `CStroke` obiektu. `CStroke` Klasy nie zawiera informacji na temat kolor pióra. W związku z tym należy zmodyfikować klasy. W scribdoc.h w `CStroke` klasy, Dodaj następujące wiersze kodu po definicji `m_nPenWidth` element członkowski danych.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

3. W scribdoc.h, Dodaj nowy `CStroke` konstruktora, w której parametry Określ szerokość i kolor. Dodaj następujący wiersz kodu po `CStroke(UINT nPenWidth);` instrukcji.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

4. W scribdoc.cpp, Dodaj implementację nowej `CStroke` konstruktora. Dodaj następujący kod po wprowadzeniu w życie `CStroke::CStroke(UINT nPenWidth)` konstruktora.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

5. Zmień drugi wiersz `CStroke::DrawStroke` metody w następujący sposób.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

6. Ustaw domyślny kolor pióra klasy dokumentu. W scribdoc.cpp, Dodaj następujące wiersze do `CScribbleDoc::InitDocument`po `m_nThickWidth = 5;` instrukcji.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

7. W scribdoc.cpp, Zmień w pierwszym wierszu `CScribbleDoc::NewStroke` metody do następującego.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

8. Zmień ostatni wiersz `CScribbleDoc::ReplacePen` metody do następującego.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

9. Możesz dodać `m_penColor` elementu członkowskiego w poprzednim kroku. Teraz Utwórz program obsługi zdarzeń dla przycisku koloru, który ustawia element członkowski.

   1. W **widok zasobów** okna, otwórz zasób menu IDR_SCRIBBTYPE.

   2. Kliknij prawym przyciskiem myszy **kolor** element menu i kliknij przycisk **dodać program obsługi zdarzeń**. **Kreator obsługi zdarzeń** pojawia się.

   3. W **listy klas** polu w kreatorze Wybierz **CScribbleDoc** a następnie kliknij przycisk **dodawać i edytować** przycisku. Spowoduje to utworzenie `CScribbleDoc::OnPenColor` szkieletu program obsługi zdarzenia.

10. Zastąp klasy zastępczej dla `CScribbleDoc::OnPenColor` programu obsługi zdarzeń z następującym kodem.

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

11. Zapisz zmiany, a następnie tworzenie i uruchamianie aplikacji. Można nacisnąć przycisk koloru i zmienić kolor pióra.

[[Sekcje](#top)]

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

2. Zapisz kolor Rysowanie w pliku. Dodaj następującą instrukcję, aby scribdoc.cpp, w `CStroke::Serialize` metoda po `ar << (WORD)m_nPenWidth;` instrukcji.

   ```cpp
   ar << (COLORREF)m_penColor;
    ```

3. Na koniec Załaduj kolor rysowania z pliku. Dodaj następujący wiersz kodu, w `CStroke::Serialize` metoda po `m_nPenWidth = w;` instrukcji.

   ```cpp
   ar >> m_penColor;
   ```

4. Teraz Bazgroły w kolorze i zapisać w pliku rysunku.

[[Sekcje](#top)]

## <a name="conclusion"></a>Wniosek

Klasa Scribble MFC aplikacji zostały zaktualizowane. Należy użyć w tym przewodniku jako przewodnika podczas modyfikowania istniejących aplikacji.

## <a name="see-also"></a>Zobacz też

[Przewodniki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
