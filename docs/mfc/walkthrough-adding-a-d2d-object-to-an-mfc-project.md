---
title: 'Wskazówki: dodawanie obiektu D2D do projektu MFC'
ms.date: 09/20/2018
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 0793511f09be9dcb37732c4c16bfd2b3038a6cf4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567261"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Wskazówki: dodawanie obiektu D2D do projektu MFC

Ten przewodnik omawia sposób dodawania podstawowe Direct2D (D2D) obiektu do programu Visual C++ projektu Microsoft Foundation Class Library (MFC), a następnie skompilowanie projektu do aplikacji, która drukuje "Hello, world" na gradientu tła.

Instruktażu przedstawiono sposób wykonywania tych zadań:

- Tworzenie aplikacji MFC.

- Utwórz pełny kolor pędzla i pędzla gradientu liniowego.

- Zmodyfikuj pędzla gradientów, tak, aby członkowie zmieniają się odpowiednio po zmianie rozmiaru okna.

- Implementowanie obsługi rysowania D2D.

- Sprawdź wyniki.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Do przeprowadzenia tego instruktażu, konieczne jest posiadanie zainstalowanego za pomocą programu Visual Studio **programowanie aplikacji klasycznych w języku C++** obciążenia i opcjonalną **Visual C++ MFC dla x86 i x64** składnika.

## <a name="to-create-an-mfc-application"></a>Aby utworzyć aplikację MFC

1. Na **pliku** menu wskaż **New** , a następnie wybierz **projektu**.

1. W **nowy projekt** okno dialogowe, w okienku po lewej stronie w obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C++** , a następnie wybierz **MFC**. W środkowym okienku wybierz **aplikacji MFC**. W **nazwa** wpisz *MFCD2DWalkthrough*. Wybierz **OK**.

1. W **Kreator aplikacji MFC**, wybierz **Zakończ** bez zmieniania żadnych ustawień.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Aby utworzyć pełny kolor pędzla i pędzla gradientu liniowego

1. W **Eksploratora rozwiązań**w **MFCD2DWalkthrough** projektu w **pliki nagłówkowe** folder, otwórz MFCD2DWalkthroughView.h. Dodaj następujący kod do `CMFCD2DWalkthroughView` klasy w celu utworzenia trzech zmiennych danych:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Zapisz plik i zamknij go.

1. W **pliki źródłowe** folder, otwórz MFCD2DWalkthroughView.cpp. W Konstruktorze `CMFCD2DWalkthroughView` klasy, Dodaj następujący kod:

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Zapisz plik i zamknij go.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Aby zmodyfikować pędzla gradientów, tak, aby członkowie zmieniają się odpowiednio po zmianie rozmiaru okna

1. Na **projektu** menu, wybierz **Kreator klas**.

1. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz opcję `CMFCD2DWalkthroughView`.

1. Na **wiadomości** na karcie **wiadomości** wybierz opcję `WM_SIZE` , a następnie wybierz **Dodaj obsługę**. Ta akcja spowoduje dodanie `OnSize` program obsługi komunikatów do `CMFCD2DWalkthroughView` klasy.

1. W **istniejące programy obsługi** wybierz opcję `OnSize`. Wybierz **Edytuj kod** do wyświetlenia `CMFCD2DWalkthroughView::OnSize` metody. Na końcu metody Dodaj następujący kod.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Zapisz plik i zamknij go.

## <a name="to-implement-a-d2d-drawing-handler"></a>Aby zaimplementować mechanizm obsługi rysowania D2D

1. Na **projektu** menu, wybierz **Kreator klas**.

1. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz opcję `CMFCD2DWalkthroughView`.

1. Na **wiadomości** kartę, wybrać **dodać niestandardowy komunikat**.

1. W **dodać niestandardowy komunikat** dialogowym **komunikat Windows niestandardowego** wpisz *AFX_WM_DRAW2D*. W **Nazwa procedury obsługi wiadomości** wpisz *OnDraw2D*. Wybierz **zarejestrowany komunikat** opcji, a następnie wybierz **OK**. Ta akcja spowoduje dodanie obsługi komunikatów do wiadomości AFX_WM_DRAW2D `CMFCD2DWalkthroughView` klasy.

1. W **istniejące programy obsługi** wybierz opcję `OnDraw2D`. Wybierz **Edytuj kod** do wyświetlenia `CMFCD2DWalkthroughView::OnDraw2D` metody. Użyj tego kodu na potrzeby `CMFCD2DWalkthroughView::OnDrawD2D` metody:

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Zapisz plik i zamknij go.

## <a name="to-verify-the-results"></a>Aby sprawdzić oddziaływanie

Skompiluj i uruchom aplikację. Powinien on gradientu prostokąt, który zmienia się podczas zmiany rozmiaru okna. "Hello World!" powinna być wyświetlana w Centrum prostokąta.

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
