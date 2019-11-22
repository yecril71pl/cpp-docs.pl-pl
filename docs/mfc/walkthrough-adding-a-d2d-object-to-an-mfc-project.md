---
title: 'Wskazówki: dodawanie obiektu D2D do projektu MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304298"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Wskazówki: dodawanie obiektu D2D do projektu MFC

W tym instruktażu przedstawiono sposób dodawania podstawowego obiektu Direct2D (D2D) do projektu wizualizacji C++, biblioteka MFC (MFC), a następnie tworzenia projektu w aplikacji, która drukuje "Hello, World!" na tle gradientu.

W tym przewodniku przedstawiono sposób wykonywania następujących zadań:

- Utwórz aplikację MFC.

- Utwórz pędzel z pełnymi kolorami i gradient liniowy.

- Zmodyfikuj pędzel gradientu w taki sposób, aby zmienił się odpowiednio po zmianie rozmiaru okna.

- Zaimplementuj procedurę obsługi rysowania D2D.

- Sprawdź wyniki.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć zainstalowany program Visual Studio z **programowaniem dla komputerów C++ stacjonarnych z** obciążeniem i opcjonalną **wizualizacją C++ MFC dla składnika x86 i x64** .

## <a name="to-create-an-mfc-application"></a>Aby utworzyć aplikację MFC

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć aplikację MFC. Zobacz [Przewodnik: używanie nowych formantów powłoki MFC](walkthrough-using-the-new-mfc-shell-controls.md) w celu uzyskania instrukcji dotyczących sposobu otwierania Kreatora dla używanej wersji programu Visual Studio.

1. W polu **Nazwa** wpisz *MFCD2DWalkthrough*. Wybierz **OK**.

1. W **Kreatorze aplikacji MFC**wybierz pozycję **Zakończ** bez zmiany jakichkolwiek ustawień.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Tworzenie pędzla pełnego koloru i gradientu liniowego

1. W **Eksplorator rozwiązań**w projekcie **MFCD2DWalkthrough** , w folderze **pliki nagłówkowe** Otwórz MFCD2DWalkthroughView. h. Dodaj ten kod do klasy `CMFCD2DWalkthroughView`, aby utworzyć trzy zmienne danych:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Zapisz plik i zamknij go.

1. W folderze **pliki źródłowe** Otwórz MFCD2DWalkthroughView. cpp. W konstruktorze klasy `CMFCD2DWalkthroughView` Dodaj następujący kod:

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

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Aby zmodyfikować pędzel gradientu w taki sposób, że zmieni się odpowiednio po zmianie rozmiaru okna

1. W menu **projekt** wybierz **kreatora klas**.

1. W **Kreatorze klasy MFC**w obszarze **Nazwa klasy**wybierz pozycję `CMFCD2DWalkthroughView`.

1. Na karcie **komunikaty** w polu **komunikaty** wybierz pozycję `WM_SIZE` a następnie wybierz pozycję **Dodaj procedurę obsługi**. Ta akcja dodaje procedurę obsługi komunikatów `OnSize` do klasy `CMFCD2DWalkthroughView`.

1. W polu **istniejące programy obsługi** wybierz pozycję `OnSize`. Wybierz polecenie **Edytuj kod** , aby wyświetlić metodę `CMFCD2DWalkthroughView::OnSize`. Na końcu metody Dodaj następujący kod.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Zapisz plik i zamknij go.

## <a name="to-implement-a-d2d-drawing-handler"></a>Aby zaimplementować procedurę obsługi rysowania D2D

1. W menu **projekt** wybierz **kreatora klas**.

1. W **Kreatorze klasy MFC**w obszarze **Nazwa klasy**wybierz pozycję `CMFCD2DWalkthroughView`.

1. Na karcie **wiadomości** wybierz pozycję **Dodaj komunikat niestandardowy**.

1. W oknie dialogowym **Dodawanie komunikatu niestandardowego** w polu **niestandardowy komunikat systemu Windows** wpisz *AFX_WM_DRAW2D*. W polu **Nazwa programu obsługi wiadomości** wpisz *OnDraw2D*. Wybierz opcję **zarejestrowany komunikat** , a następnie wybierz **przycisk OK**. Ta akcja dodaje procedurę obsługi komunikatów AFX_WM_DRAW2D do klasy `CMFCD2DWalkthroughView`.

1. W polu **istniejące programy obsługi** wybierz pozycję `OnDraw2D`. Wybierz polecenie **Edytuj kod** , aby wyświetlić metodę `CMFCD2DWalkthroughView::OnDraw2D`. Użyj tego kodu dla metody `CMFCD2DWalkthroughView::OnDrawD2D`:

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

## <a name="to-verify-the-results"></a>Aby sprawdzić wyniki

Skompiluj i uruchom aplikację. Powinien on mieć prostokąt gradientu, który zmienia się po zmianie rozmiaru okna. "Hello world!" powinna być wyświetlana na środku prostokąta.

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
