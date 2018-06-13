---
title: 'Wskazówki: Dodawanie obiektu D2D do projektu MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7985b36c0eeaa7adf5441a7a6fbb3314bac8353f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384023"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Wskazówki: dodawanie obiektu D2D do projektu MFC
Ten przewodnik zawiera wskazówki jak dodać podstawowe Direct2D (D2D) obiekt do języka Visual C++, projektu Microsoft Foundation Class biblioteki (MFC), a następnie Skompiluj projekt do aplikacji, która wyświetla "tekst Hello, world" gradientu tła.  
  
 Instruktaż pokazano, jak wykonać te zadania:  
  
-   Tworzenie aplikacji MFC.  
  
-   Tworzenie pędzla pełny kolor i pędzla gradientu liniowego.  
  
-   Zmodyfikuj pędzla gradientu, tak, aby go zostanie odpowiednio zmienić podczas zmiany rozmiaru okna.  
  
-   Implementowanie obsługi rysowania D2D.  
  
-   Sprawdź wyniki.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku, musi mieć programu Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>Do tworzenia aplikacji MFC  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, w lewym okienku w obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C++** , a następnie wybierz **MFC**. W środkowym okienku wybierz **aplikacji MFC**. W **nazwa** wpisz `MFCD2DWalkthrough`. Kliknij przycisk **OK**.  
  
3.  W **Kreator aplikacji MFC**, kliknij przycisk **Zakończ** bez zmieniania żadnych ustawień.  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Aby utworzyć pełny kolor pędzla i pędzla gradientu liniowego  
  
1.  W **Eksploratora rozwiązań**w **MFCD2DWalkthrough** projektu w **pliki nagłówkowe** MFCD2DWalkthroughView.h Otwórz folder. Dodaj następujący kod do `CMFCD2DWalkthroughView` klasy w celu utworzenia trzech zmiennych danych.  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     Zapisz plik i zamknij go.  
  
2.  W **pliki źródłowe** MFCD2DWalkthroughView.cpp Otwórz folder. W Konstruktorze `CMFCD2DWalkthroughView` klasy, Dodaj następujący kod.  
  
 "" * / / Włącz obsługę D2D dla tego okna:  
    EnableD2DSupport();

 * / / Zainicjować zasoby D2D:  
    m_pBlackBrush = CD2DSolidColorBrush(GetRenderTarget() nowe, D2D1::ColorF(D2D1::ColorF::Black));

 
    m_pTextFormat = CD2DTextFormat(GetRenderTarget() nowe, _T("Verdana"), 50);

    m_pTextFormat -> Get() -> SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);

 m_pTextFormat -> Get() -> SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

 
    GradientStops D2D1_GRADIENT_STOP [2].  
 
    .color gradientStops [0] = D2D1::ColorF(D2D1::ColorF::White);

    .position gradientStops [0] = 0.f;  
    .color gradientStops [1] = D2D1::ColorF(D2D1::ColorF::Indigo);

    .position gradientStops [1] = 1.f;  
 
    m_pLinearGradientBrush = nowy CD2DLinearGradientBrush(GetRenderTarget()   
    gradientStops, ARRAYSIZE(gradientStops),  
    D2D1::LinearGradientBrushProperties (D2D1::Point2F (0, 0), D2D1::Point2F (0, 0)));

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush -> SetEndPoint (CPoint (cx, cy));

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam) elementu LRESULT  
    {  
 PRenderTarget CHwndRenderTarget * = (CHwndRenderTarget *) lParam;  
    ASSERT_VALID(pRenderTarget);

 
    CRect rect;  
    GetClientRect(rect);

 
    pRenderTarget -> FillRectangle (rect, m_pLinearGradientBrush);

    pRenderTarget -> DrawText (rect ("Hello, World!"), _t — m_pBlackBrush, m_pTextFormat);

 
    Zwraca wartość TRUE;  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

