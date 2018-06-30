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
ms.openlocfilehash: bccc10e1aa2d984486c3cadfd45a14a6625ec959
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122408"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Wskazówki: aktualizowanie aplikacji bazgrołów MFC (część 2)

[Część 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) tego instruktażu pokazano, jak dodać Fluent wstążki pakietu Office do klasycznego Bazgroły aplikacji. Tej części przedstawiono sposób dodawania paneli Wstążki i kontrolek, które użytkownicy mogą używać zamiast menu i poleceń.

## <a name="prerequisites"></a>Wymagania wstępne

[Przykłady Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Dodawanie nowych paneli do wstążki](#addnewpanel)

- [Dodawanie panelu pomocy do wstążki](#addhelppanel)

- [Dodawanie panelu pióra do wstążki](#addpenpanel)

- [Dodawanie przycisk koloru do wstążki](#addcolorbutton)

- [Dodawanie członka kolorów do klasy dokumentów](#addcolormember)

- [Inicjowanie pióra i preferencji zapisywania](#initpensave)

##  <a name="addnewpanel"></a> Dodawanie nowych paneli do wstążki

Te kroki pokazują, jak dodać **widoku** panel, która zawiera dwa pola wyboru kontrolujących widoczność paska narzędzi i paska stanu, a także **okna** panelu, który zawiera podział orientacji pionowej przycisk, który kontroluje tworzenie i układ interfejsu wielu dokumentów (MDI) systemu Windows.

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Aby dodać panel widoku i okno panel do pasek wstążki

1. Utwórz panelu o nazwie `View`, która ma dwa pola wyboru, które Przełącz pasek stanu i narzędzi.

   1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij dwa **pola wyboru** do panelu.

   2. Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do `View`.

   3. Kliknij pierwszy pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** do `ID_VIEW_TOOLBAR` i **podpis** do `Toolbar`.

   4. Kliknij przycisk drugie pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** do `ID_VIEW_STATUS_BAR` i **podpis** do `Status Bar`.

2. Utwórz panelu o nazwie `Window` mający przycisku podziału. Po kliknięciu przycisku podziału menu skrótów wyświetlane trzy polecenia, które zostały już zdefiniowane w aplikacji bazgrołów.

   1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij **przycisk** do panelu.

   2. Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do `Window`.

   3. Kliknij przycisk. Zmień **podpis** do `Windows`, **klucze** do `w`, **indeks dużego obrazu** do `1`, i **Tryb podziału** Aby `False`. Następnie kliknij przycisk wielokropka (**...** ) obok pozycji **elementów Menu** otworzyć **Edytor elementów** okno dialogowe.

   4. Kliknij przycisk **Dodaj** trzy razy, aby dodać trzy przyciski.

   5. Kliknij pierwszy przycisk, a następnie zmień **podpis** do `New Window`, i **identyfikator** do `ID_WINDOW_NEW`.

   6. Kliknij przycisk drugiej, a następnie zmień **podpis** do `Cascade`, i **identyfikator** do `ID_WINDOW_CASCADE`.

   7. Kliknij przycisk trzeci, a następnie zmień **podpis** do `Tile`, i **identyfikator** do `ID_WINDOW_TILE_HORZ`.

3. Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. **Widoku** i **okna** panele powinny być wyświetlane. Kliknij przyciski, aby potwierdzić, że działają poprawnie.

[[Sekcje](#top)]

##  <a name="addhelppanel"></a> Dodawanie panelu pomocy do wstążki

Teraz można przypisać dwa elementy menu, które są zdefiniowane w aplikacji bazgrołów do przycisków wstążki, które są nazywane **tematy Pomocy** i **o Bazgroły**. Przyciski są dodawane do panelu nowe o nazwie **pomocy**.

### <a name="to-add-a-help-panel"></a>Aby dodać panel pomocy

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij dwa **przyciski** do panelu.

2. Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do `Help`.

3. Kliknij pierwszy przycisk. Zmień **podpis** do `Help Topics`, i **identyfikator** do `ID_HELP_FINDER`.

4. Kliknij przycisk drugiego. Zmień **podpis** do `About Scribble...`, i **identyfikator** do `ID_APP_ABOUT`.

5. Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. A **pomocy** powinien być wyświetlany panel, która zawiera dwa przyciski wstążki.

   > [!IMPORTANT]
   > Po kliknięciu **tematy Pomocy** przycisku, otwarcie aplikacji bazgrołów skompresowany plik Pomocy HTML (.chm) o nazwie *your_project_name*. chm. W związku z tym jeśli projekt nie ma nazwy bazgrołów, należy zmienić plik pomocy do nazwy projektu.

[[Sekcje](#top)]

##  <a name="addpenpanel"></a> Dodawanie panelu pióra do wstążki

Teraz Dodaj panelu, aby wyświetlić przyciski, które sterują grubość i kolor pióra. Panel ten zawiera pole wyboru, które Przełącza pomiędzy grubych i alokowania pióra. Jego działanie przypomina z **grubości linii** elementu menu w aplikacji bazgrołów.

Oryginalnej aplikacji bazgrołów umożliwia użytkownikowi wybieranie szerokości pióra z okna dialogowego, który jest wyświetlany, gdy użytkownik kliknie **szerokości pióra** w menu. Ponieważ pasek wstążki ma wystarczającą ilość miejsca na nowe formanty, można zastąpić okna dialogowego za pomocą dwóch pól kombi na Wstążce. Grubość pióra alokowania dopasowuje jedno pole kombi i pole kombi dostosowuje szerokość grubość pióra.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Aby dodać panel pióra i kombi pola do wstążki

1. Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij **pole wyboru** i dwa **pola kombi** do panelu.

2. Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do `Pen`.

3. Kliknij pole wyboru. Zmień **podpis** do `Use Thick`, i **identyfikator** do `ID_PEN_THICK_OR_THIN`.

4. Kliknij pierwszy pola kombi. Zmień **podpis** do `Thin Pen`, **identyfikator** do `ID_PEN_THIN_WIDTH`, **tekst** do `2`, **typu** do `Drop List`, i **danych** do `1;2;3;4;5;6;7;8;9;`.

5. Kliknij pole kombi drugiego. Zmień **podpis** do `Thick Pen`, **identyfikator** do `ID_PEN_THICK_WIDTH`, **tekst** do `5`, **typu** do `Drop List`, i **danych** do `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`.

6. Wszystkie istniejące elementy menu nie odpowiadają nowego pola kombi. Dlatego należy utworzyć element menu dla każdej opcji pióra.

   1. W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu.

   2. Kliknij przycisk **pióra** otworzyć p**en** menu. Następnie kliknij przycisk **typu w tym miejscu** i typu `Thi&n Pen`.

   3. Kliknij prawym przyciskiem myszy tekst, który właśnie wpisane w celu otwarcia **właściwości** okna, a następnie zmień identyfikator właściwości `ID_PEN_THIN_WIDTH`.

   4. Należy także utworzyć program obsługi zdarzeń dla każdego elementu menu pióra. Kliknij prawym przyciskiem myszy **gr & n pióra** element menu, który właśnie utworzony, a następnie kliknij przycisk **Dodaj program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlany.

   5. W **listy klas** pola w kreatorze Wybierz **CScribbleDoc** , a następnie kliknij przycisk **dodawać i edytować**. Spowoduje to utworzenie program obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThinWidth`.

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

   1. W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu.

   2. Kliknij przycisk **pióra** aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typu `Thic&k Pen`.

   3. Kliknij prawym przyciskiem myszy tekst, który właśnie został wpisany do wyświetlenia **właściwości** okna. Zmień właściwości ID do `ID_PEN_THICK_WIDTH`.

   4. Kliknij prawym przyciskiem myszy **grubość pióra** element menu, który właśnie utworzony, a następnie kliknij przycisk **Dodaj program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlany.

   5. W **listy klas** pola kreatora wybierz pozycję **CScribbleDoc** , a następnie kliknij przycisk **dodawać i edytować**. Spowoduje to utworzenie program obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThickWidth`.

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

8. Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. Powinny być wyświetlane nowe przycisków i pola kombi. Spróbuj użyć innego pióra szerokości do Bazgroły.

[[Sekcje](#top)]

##  <a name="addcolorbutton"></a> Dodawanie przycisk koloru do panelu pióra

Następnie dodaj [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) obiekt, który umożliwia użytkownikowi bazgrołów w kolorze.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Aby dodać przycisk koloru do panelu pióra

1. Przed dodaniem przycisk koloru, należy utworzyć element menu dla niego. W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu. Kliknij przycisk **pióra** element menu, aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typu `&Color`. Kliknij prawym przyciskiem myszy tekst, który właśnie został wpisany do wyświetlenia **właściwości** okna. Zmień identyfikator do `ID_PEN_COLOR`.

2. Teraz Dodaj przycisk koloru. Z **przybornika**, przeciągnij **przycisk koloru** do **pióra** panelu.

3. Kliknij przycisk koloru. Zmień **podpis** do `Color`, **identyfikator** do `ID_PEN_COLOR`, **SimpleLook** do `True`, **indeks dużego obrazu** do `1`, i **Tryb podziału** do `False`.

4. Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. Powinien być wyświetlany przycisk Nowy kolor na **pióra** panelu. Jednak nie można użyć, ponieważ nie ma jeszcze obsługi zdarzeń. W następnych krokach przedstawiono sposób dodawania obsługi zdarzeń dla przycisk koloru.

[[Sekcje](#top)]

##  <a name="addcolormember"></a> Dodawanie członka kolorów do klasy dokumentów

Ponieważ oryginalne aplikacji bazgrołów nie ma kolor pióra, należy napisać implementacji dla nich. Aby przechowywać na kolor pióra dokumentu, Dodaj nowy element członkowski do klasy dokumentu `CscribbleDoc.`

### <a name="to-add-a-color-member-to-the-document-class"></a>Aby dodać element członkowski kolorów do klasy dokumentów

1. W scribdoc.h w `CScribbleDoc` klasy, Znajdź `// Attributes` sekcji. Dodaj następujące wiersze kodu po definicji `m_nThickWidth` element członkowski danych.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

2. Każdy dokument zawiera listę pociągnięć, że użytkownik ma już wstawiany. Każdy obiekt stroke jest definiowana za pomocą `CStroke` obiektu. `CStroke` Klasa nie ma informacji na temat kolor pióra. W związku z tym należy zmodyfikować klasy. W scribdoc.h w `CStroke` klasy, Dodaj następujące wiersze kodu po definicji `m_nPenWidth` element członkowski danych.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

3. W scribdoc.h, Dodaj nową `CStroke` konstruktora, którego parametry określają szerokość i kolor. Dodaj następujący wiersz kodu po `CStroke(UINT nPenWidth);` instrukcji.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

4. W scribdoc.cpp, Dodaj implementację nowej `CStroke` konstruktora. Dodaj następujący kod po realizacji `CStroke::CStroke(UINT nPenWidth)` konstruktora.

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

6. Ustawianie koloru pióra domyślnej klasy dokumentu. W scribdoc.cpp, Dodaj następujące wiersze do `CScribbleDoc::InitDocument`, po `m_nThickWidth = 5;` instrukcji.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

7. W scribdoc.cpp, Zmień pierwszy wiersz `CScribbleDoc::NewStroke` metody do następującego.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

8. Zmień ostatni wiersz `CScribbleDoc::ReplacePen` metody do następującego.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

9. Możesz dodać `m_penColor` element członkowski w poprzednim kroku. Teraz można utworzyć programu obsługi zdarzeń dla przycisku kolor, który ustawia element członkowski.

   1. W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu.

   2. Kliknij prawym przyciskiem myszy **kolor** element menu i kliknij przycisk **Dodaj program obsługi zdarzeń**. **Kreator obsługi zdarzeń** pojawi się.

   3. W **listy klas** pola w kreatorze Wybierz **CScribbleDoc** , a następnie kliknij przycisk **dodawać i edytować** przycisku. Spowoduje to utworzenie `CScribbleDoc::OnPenColor` szkieletu obsługi zdarzenia.

10. Zastąp klasy zastępczej dla `CScribbleDoc::OnPenColor` obsługi zdarzeń z następującym kodem.

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

11. Zapisać zmiany, a następnie utworzyć i uruchomić aplikację. Można nacisnąć przycisk koloru i zmienić kolor pióra.

[[Sekcje](#top)]

##  <a name="initpensave"></a> Inicjowanie pióra i preferencji zapisywania

Następnie można zainicjować, kolor i szerokość pióra. Na koniec Zapisz i załadować koloru rysowania z pliku.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Aby zainicjować kontrolki w pasku wstążki

1. Inicjowanie pióra w pasku wstążki.

   Dodaj następujący kod do scribdoc.cpp, w `CScribbleDoc::InitDocument` metody, po `m_sizeDoc = CSize(200,200)` instrukcji.

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

2. Zapisz kolor rysowania do pliku. Dodaj następującą instrukcję do scribdoc.cpp, w `CStroke::Serialize` metody, po `ar << (WORD)m_nPenWidth;` instrukcji.

   ```cpp
   ar << (COLORREF)m_penColor;
    ```

3. Na koniec załadować koloru rysowania z pliku. Dodaj następujący wiersz kodu, w `CStroke::Serialize` metody, po `m_nPenWidth = w;` instrukcji.

   ```cpp
   ar >> m_penColor;
   ```

4. Teraz Bazgroły w kolorze i zapisać w pliku rysunku.

[[Sekcje](#top)]

## <a name="conclusion"></a>Wniosek

Zaktualizowano aplikację Bazgroły MFC. Użyj tego przewodnika jako przewodnik po zmodyfikowaniu istniejących aplikacji.

## <a name="see-also"></a>Zobacz też

[Przewodniki](../mfc/walkthroughs-mfc.md)  
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)  
