---
title: 'Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 2) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 83caf353ca4a45e3ae834a41062de955a91dbb8a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952440"
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
  
#### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Aby dodać panel widoku i okno panel do pasek wstążki  
  
1.  Utwórz panelu o nazwie *widoku*, która ma dwa pola wyboru, które Przełącz pasek stanu i narzędzi.  
  
    1.  Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij dwa **pola wyboru** do panelu.  
  
    2.  Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do *widoku*.  
  
    3.  Kliknij pierwszy pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** do *id_view_toolbar —* i **podpis** do *narzędzi*.  
  
    4.  Kliknij przycisk drugie pole wyboru, aby zmodyfikować jego właściwości. Zmień **identyfikator** do *id_view_status_bar —* i **podpis** do *pasek stanu*.  
  
2.  Utwórz panelu o nazwie *okna* mający przycisku podziału. Po kliknięciu przycisku podziału menu skrótów wyświetlane trzy polecenia, które zostały już zdefiniowane w aplikacji bazgrołów.  
  
    1.  Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij **przycisk** do panelu.  
  
    2.  Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do *okna*.  
  
    3.  Kliknij przycisk. Zmień **podpis** do *Windows*, **klucze** do *w*, **indeks dużego obrazu** do *1* , i **Tryb podziału** do *False*. Następnie kliknij przycisk wielokropka (**...** ) obok pozycji **elementów Menu** otworzyć **Edytor elementów** okno dialogowe.  
  
    4.  Kliknij przycisk **Dodaj** trzy razy, aby dodać trzy przyciski.  
  
    5.  Kliknij pierwszy przycisk, a następnie zmień **podpis** do *nowe okno*, i **identyfikator** do *id_window_new —*.  
  
    6.  Kliknij przycisk drugiej, a następnie zmień **podpis** do *Cascade*, i **identyfikator** do *id_window_cascade —*.  
  
    7.  Kliknij przycisk trzeci, a następnie zmień **podpis** do *Kafelek*, i **identyfikator** do *id_window_tile_horz —*.  
  
3.  Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. **Widoku** i **okna** panele powinny być wyświetlane. Kliknij przyciski, aby potwierdzić, że działają poprawnie.  
  
 [[Sekcje](#top)]  
  
##  <a name="addhelppanel"></a> Dodawanie panelu pomocy do wstążki  
 Teraz można przypisać dwa elementy menu, które są zdefiniowane w aplikacji bazgrołów do przycisków wstążki, które są nazywane **tematy Pomocy** i **o Bazgroły**. Przyciski są dodawane do panelu nowe o nazwie **pomocy**.  
  
#### <a name="to-add-a-help-panel"></a>Aby dodać panel pomocy  
  
1.  Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij dwa **przyciski** do panelu.  
  
2.  Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do *pomocy*.  
  
3.  Kliknij pierwszy przycisk. Zmień **podpis** do *tematy Pomocy*, i **identyfikator** do *ID_HELP_FINDER*.  
  
4.  Kliknij przycisk drugiego. Zmień **podpis** do *o bazgrołów...* , i **identyfikator** do *id_app_about —*.  
  
5.  Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. A **pomocy** powinien być wyświetlany panel, która zawiera dwa przyciski wstążki.  
  
    > [!IMPORTANT]
    >  Po kliknięciu **tematy Pomocy** przycisku, otwarcie aplikacji bazgrołów skompresowany plik Pomocy HTML (.chm) o nazwie *your_project_name*. chm. W związku z tym jeśli projekt nie ma nazwy bazgrołów, należy zmienić plik pomocy do nazwy projektu.  
  
 [[Sekcje](#top)]  
  
##  <a name="addpenpanel"></a> Dodawanie panelu pióra do wstążki  
 Teraz Dodaj panelu, aby wyświetlić przyciski, które sterują grubość i kolor pióra. Panel ten zawiera pole wyboru, które Przełącza pomiędzy grubych i alokowania pióra. Jego działanie przypomina z **grubości linii** elementu menu w aplikacji bazgrołów.  
  
 Oryginalnej aplikacji bazgrołów umożliwia użytkownikowi wybieranie szerokości pióra z okna dialogowego, który jest wyświetlany, gdy użytkownik kliknie **szerokości pióra** w menu. Ponieważ pasek wstążki ma wystarczającą ilość miejsca na nowe formanty, można zastąpić okna dialogowego za pomocą dwóch pól kombi na Wstążce. Grubość pióra alokowania dopasowuje jedno pole kombi i pole kombi dostosowuje szerokość grubość pióra.  
  
#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Aby dodać panel pióra i kombi pola do wstążki  
  
1.  Z **przybornika**, przeciągnij **panelu** do **Home** kategorii. Przeciągnij **pole wyboru** i dwa **pola kombi** do panelu.  
  
2.  Kliknij panel można zmodyfikować jego właściwości. Zmień **podpis** do *pióra*.  
  
3.  Kliknij pole wyboru. Zmień **podpis** do *Użyj gruby*, i **identyfikator** do *ID_PEN_THICK_OR_THIN*.  
  
4.  Kliknij pierwszy pola kombi. Zmień **podpis** do *elastycznej pióra*, **identyfikator** do *ID_PEN_THIN_WIDTH*, **tekst** do *2* , **Typu** do *porzucić listy*, i **danych** do *1 2 3; 4; 5; 6; 7; 8; 9;*.  
  
5.  Kliknij pole kombi drugiego. Zmień **podpis** do *grubość pióra*, **identyfikator** do *ID_PEN_THICK_WIDTH*, **tekst** do  *5*, **typu** do *porzucić listy*, i **danych** do *5, 6, 7; 8; 9; 10; 11; 12; 13; 14; 15; 16; 17; 18; 19, 20;*.  
  
6.  Wszystkie istniejące elementy menu nie odpowiadają nowego pola kombi. Dlatego należy utworzyć element menu dla każdej opcji pióra.  
  
    1.  W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu.  
  
    2.  Kliknij przycisk **pióra** otworzyć p**en** menu. Następnie kliknij przycisk **typu w tym miejscu** i typ *gr & n pióra*.  
  
    3.  Kliknij prawym przyciskiem myszy tekst, który właśnie wpisane w celu otwarcia **właściwości** okna, a następnie zmień identyfikator właściwości *ID_PEN_THIN_WIDTH*.  
  
    4.  Należy także utworzyć program obsługi zdarzeń dla każdego elementu menu pióra. Kliknij prawym przyciskiem myszy **gr & n pióra** element menu, który właśnie utworzony, a następnie kliknij przycisk **Dodaj program obsługi zdarzeń**. **Kreator obsługi zdarzeń** jest wyświetlany.  
  
    5.  W **listy klas** pola w kreatorze Wybierz **CScribbleDoc** , a następnie kliknij przycisk **dodawać i edytować**. Spowoduje to utworzenie program obsługi zdarzeń o nazwie `CScribbleDoc::OnPenThinWidth`.  
  
    6.  Dodaj następujący kod do `CScribbleDoc::OnPenThinWidth`.  
  
 ``` *Pobierz wskaźnik do wstążki pasek CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar(); ASSERT_VALID(pRibbon); */ / Pobierz wskaźnik do alokowania szerokość pola kombi CMFCRibbonComboBox* pThinComboBox = dynamic_downcast — (CMFCRibbonComboBox, pRibbon FindByID(ID_PEN_THIN_WIDTH)); -> * //Get wybranej wartości  
    int nCurSel = pThinComboBox -> GetCurSel(); Jeśli (nCurSel > = 0)  
{  
m_nThinWidth = atoi — (pThinComboBox -> GetItem(nCurSel));

 } * / / Tworzenie nowych przy użyciu wybranej grubości pióra  
    ReplacePen();

 ```  
  
7.  Next, create a menu item and event handlers for the thick pen.  
  
    1.  In the **Resource View** window, open the IDR_SCRIBBTYPE menu resource.  
  
    2.  Click **Pen** to open the pen menu. Then click **Type Here** and type *Thic&k Pen*.  
  
    3.  Right-click the text that you just typed to display the **Properties** window. Change the ID property to *ID_PEN_THICK_WIDTH*.  
  
    4.  Right-click the **Thick Pen** menu item that you just created and then click **Add Event Handler**. The **Event Handler Wizard** is displayed.  
  
    5.  In the **Class list** box of the wizard, select **CScribbleDoc** and then click **Add and Edit**. This creates an event handler named `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Add the following code to `CScribbleDoc::OnPenThickWidth`.  
  
 ``` *// Get a pointer to the ribbon bar  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
*// Get the selected value  
    int nCurSel = pThickComboBox->GetCurSel();
if (nCurSel>= 0)  
 {  
    m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));

 } *// Create a new pen using the selected width  
    ReplacePen();

 ```  
  
8.  Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. Powinny być wyświetlane nowe przycisków i pola kombi. Spróbuj użyć innego pióra szerokości do Bazgroły.  
  
 [[Sekcje](#top)]  
  
##  <a name="addcolorbutton"></a> Dodawanie przycisk koloru do panelu pióra  
 Następnie dodaj [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) obiekt, który umożliwia użytkownikowi bazgrołów w kolorze.  
  
#### <a name="to-add-a-color-button-to-the-pen-panel"></a>Aby dodać przycisk koloru do panelu pióra  
  
1.  Przed dodaniem przycisk koloru, należy utworzyć element menu dla niego. W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu. Kliknij przycisk **pióra** element menu, aby otworzyć menu pióra. Następnie kliknij przycisk **typu w tym miejscu** i typ *& kolorów*. Kliknij prawym przyciskiem myszy tekst, który właśnie został wpisany do wyświetlenia **właściwości** okna. Zmień identyfikator do *ID_PEN_COLOR*.  
  
2.  Teraz Dodaj przycisk koloru. Z **przybornika**, przeciągnij **przycisk koloru** do **pióra** panelu.  
  
3.  Kliknij przycisk koloru. Zmień **podpis** do *kolor*, **identyfikator** do *ID_PEN_COLOR*, **SimpleLook** do  *Wartość true,*, **indeks dużego obrazu** do *1*, i **Tryb podziału** do *False*.  
  
4.  Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. Powinien być wyświetlany przycisk Nowy kolor na **pióra** panelu. Jednak nie można użyć, ponieważ nie ma jeszcze obsługi zdarzeń. W następnych krokach przedstawiono sposób dodawania obsługi zdarzeń dla przycisk koloru.  
  
 [[Sekcje](#top)]  
  
##  <a name="addcolormember"></a> Dodawanie członka kolorów do klasy dokumentów  
 Ponieważ oryginalne aplikacji bazgrołów nie ma kolor pióra, należy napisać implementacji dla nich. Aby przechowywać na kolor pióra dokumentu, Dodaj nowy element członkowski do klasy dokumentu `CscribbleDoc.`  
  
#### <a name="to-add-a-color-member-to-the-document-class"></a>Aby dodać element członkowski kolorów do klasy dokumentów  
  
1.  W scribdoc.h w `CScribbleDoc` klasy, Znajdź `// Attributes` sekcji. Dodaj następujące wiersze kodu po definicji `m_nThickWidth` element członkowski danych.  
  
 "" * / / Kolor pióra bieżącego  
    COLORREF m_penColor;  
 ```  
  
2.  Every document contains a list of stokes that the user has already drawn. Every stroke is defined by a `CStroke` object. The `CStroke` class does not include information about pen color. Therefore, you must modify the class. In scribdoc.h, in the `CStroke` class, add the following lines of code after the definition of the `m_nPenWidth` data member.  
  
 ``` *// Pen color for the stroke  
    COLORREF m_penColor;  
 ```  
  
3.  W scribdoc.h, Dodaj nową `CStroke` konstruktora, którego parametry określają szerokość i kolor. Dodaj następujący wiersz kodu po `CStroke(UINT nPenWidth);` instrukcji.  
  
 ```  
    CStroke(UINT nPenWidth, COLORREF penColor);

 ```  
  
4.  W scribdoc.cpp, Dodaj implementację nowej `CStroke` konstruktora. Dodaj następujący kod po realizacji `CStroke::CStroke(UINT nPenWidth)` konstruktora.  
  
 "" * / / Konstruktor, który korzysta z dokumentu do bieżącego szerokości i koloru  
    CStroke::CStroke (UINT nPenWidth, COLORREF penColor)  
 {  
    m_nPenWidth = nPenWidth;  
    m_penColor = penColor;  
    m_rectBounding.SetRectEmpty();

 }  
 ```  
  
5.  Change the second line of the `CStroke::DrawStroke` method as follows.  
  
 ```  
    Jeśli (! penStroke.CreatePen (PS_SOLID, m_nPenWidth, m_penColor))  
 ```  
  
6.  Set the default pen color for the document class. In scribdoc.cpp, add the following lines to `CScribbleDoc::InitDocument`, after the `m_nThickWidth = 5;` statement.  
  
 ``` *// default pen color is black  
    m_penColor = RGB(0,
    0,
    0);

 ```  
  
7.  W scribdoc.cpp, Zmień pierwszy wiersz `CScribbleDoc::NewStroke` metody do następującego.  
  
 ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);

 ```  
  
8.  Zmień ostatni wiersz `CScribbleDoc::ReplacePen` metody do następującego.  
  
 ```  
    m_penCur.CreatePen(PS_SOLID,
    m_nPenWidth,
    m_penColor);

 ```  
  
9. Możesz dodać `m_penColor` element członkowski w poprzednim kroku. Teraz można utworzyć programu obsługi zdarzeń dla przycisku kolor, który ustawia element członkowski.  
  
    1.  W **widok zasobów** okna, otwórz IDR_SCRIBBTYPE zasobów menu.  
  
    2.  Kliknij prawym przyciskiem myszy **kolor** element menu i kliknij przycisk **Dodaj program obsługi zdarzeń**. **Kreator obsługi zdarzeń** pojawi się.  
  
    3.  W **listy klas** pola w kreatorze Wybierz **CScribbleDoc** , a następnie kliknij przycisk **dodawać i edytować** przycisku. Spowoduje to utworzenie `CScribbleDoc::OnPenColor` szkieletu obsługi zdarzenia.  
  
10. Zastąp klasy zastępczej dla `CScribbleDoc::OnPenColor` obsługi zdarzeń z następującym kodem.  
  
 ```  
    void CScribbleDoc::OnPenColor()  
 { *// Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
    CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

    m_penColor = pColorBtn->GetColor();
*// Create new pen using the selected color  
    ReplacePen();

 }  
 ```  
  
11. Zapisać zmiany, a następnie utworzyć i uruchomić aplikację. Można nacisnąć przycisk koloru i zmienić kolor pióra.  
  
 [[Sekcje](#top)]  
  
##  <a name="initpensave"></a> Inicjowanie pióra i preferencji zapisywania  
 Następnie można zainicjować, kolor i szerokość pióra. Na koniec Zapisz i załadować koloru rysowania z pliku.  
  
#### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Aby zainicjować kontrolki w pasku wstążki  
  
1.  Inicjowanie pióra w pasku wstążki.  
  
     Dodaj następujący kod do scribdoc.cpp, w `CScribbleDoc::InitDocument` metody, po `m_sizeDoc = CSize(200,200)` instrukcji.  
  
 ``` *Resetuj interfejs użytkownika wstążki do swojej wartości początkowej CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar(); ASSERT_VALID(pRibbon);

 PColorBtn CMFCRibbonColorButton * = dynamic_downcast — (CMFCRibbonColorButton, pRibbon -> FindByID(ID_PEN_COLOR)); * / / Set ColorButton na kolor czarny  
    pColorBtn -> SetColor (RGB (0, 0, 0));

 PThinComboBox CMFCRibbonComboBox * = dynamic_downcast — (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THIN_WIDTH)); * / / Set combobox alokowania Pióro 2  
    pThinComboBox -> SelectItem(1);

 PThickComboBox CMFCRibbonComboBox * = dynamic_downcast — (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THICK_WIDTH)); * / / Set combobox grubość pióra na wartość 5.  
    pThickComboBox -> SelectItem(0);

 ```  
  
2.  Save a color drawing to a file. Add the following statement to scribdoc.cpp, in the `CStroke::Serialize` method, after the `ar << (WORD)m_nPenWidth;` statement.  
  
 ```  
    ar << m_penColor (COLORREF);  
 ```  
  
3.  Finally, load a color drawing from a file. Add the following line of code, in the `CStroke::Serialize` method, after the `m_nPenWidth = w;` statement.  
  
 ```  
    ar >> m_penColor;  
 ```  
  
4.  Now scribble in color and save your drawing to a file.  
  
 [[Sections](#top)]  
  
## Conclusion  
 You have updated the MFC Scribble application. Use this walkthrough as a guide when you modify your existing applications.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

