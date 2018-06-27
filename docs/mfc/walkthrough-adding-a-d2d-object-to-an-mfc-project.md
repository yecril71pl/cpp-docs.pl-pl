---
title: 'Wskazówki: Dodawanie obiektu D2D do projektu MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/19/2018
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
ms.openlocfilehash: 87e1c696f3da374d7b71e1b24e3a8bd3ebfe41b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954874"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Wskazówki: dodawanie obiektu D2D do projektu MFC

Ten przewodnik zawiera wskazówki jak dodać podstawowe Direct2D (D2D) obiekt do języka Visual C++, projektu Microsoft Foundation Class biblioteki (MFC), a następnie Skompiluj projekt do aplikacji, która wyświetla "tekst Hello, world" gradientu tła.

Instruktaż pokazano, jak wykonać te zadania:

- Tworzenie aplikacji MFC.

- Tworzenie pędzla pełny kolor i pędzla gradientu liniowego.

- Zmodyfikuj pędzla gradientu, tak, aby go zostanie odpowiednio zmienić podczas zmiany rozmiaru okna.

- Implementowanie obsługi rysowania D2D.

- Sprawdź wyniki.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku muszą mieć zainstalowanego z programu Visual Studio **tworzenia klasycznych aplikacji w języku C++** obciążenia i opcjonalne **Visual C++ MFC dla x86 i x64** składnika.

## <a name="to-create-an-mfc-application"></a>Do tworzenia aplikacji MFC

1. Na **pliku** menu wskaż **nowy** , a następnie wybierz **projektu**.

2. W **nowy projekt** okno dialogowe, w lewym okienku w obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C++** , a następnie wybierz **MFC**. W środkowym okienku wybierz **aplikacji MFC**. W **nazwa** wpisz *MFCD2DWalkthrough*. Wybierz **OK**.

3. W **Kreator aplikacji MFC**, wybierz **Zakończ** bez zmieniania żadnych ustawień.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Aby utworzyć pełny kolor pędzla i pędzla gradientu liniowego

1. W **Eksploratora rozwiązań**w **MFCD2DWalkthrough** projektu w **pliki nagłówkowe** MFCD2DWalkthroughView.h Otwórz folder. Dodaj ten kod do `CMFCD2DWalkthroughView` klasy w celu utworzenia trzech zmiennych danych:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Zapisz plik i zamknij go.

2. W **pliki źródłowe** MFCD2DWalkthroughView.cpp Otwórz folder. W Konstruktorze `CMFCD2DWalkthroughView` klasy, Dodaj ten kod:

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

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Aby zmodyfikować pędzla gradientu, tak aby ulega zmianie odpowiednio podczas zmiany rozmiaru okna

1. Na **projektu** menu, wybierz **Kreator klas**.

2. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz pozycję `CMFCD2DWalkthroughView`.

3. Na **wiadomości** karcie **wiadomości** wybierz opcję `WM_SIZE` , a następnie wybierz **Dodaj obsługę**. Ta akcja dodaje `OnSize` obsługi komunikatów do `CMFCD2DWalkthroughView` klasy.

4. W **istniejące programy obsługi** wybierz opcję `OnSize`. Wybierz **Edytuj kod** do wyświetlenia `CMFCD2DWalkthroughView::OnSize` metody. Na końcu metody Dodaj następujący kod.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Zapisz plik i zamknij go.

## <a name="to-implement-a-d2d-drawing-handler"></a>Aby zaimplementować D2D obsługi rysowania

1. Na **projektu** menu, wybierz **Kreator klas**.

2. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz pozycję `CMFCD2DWalkthroughView`.

3. Na **wiadomości** , wybierz pozycję **Dodaj niestandardowy komunikat**.

4. W **Dodaj niestandardowy komunikat** okna dialogowego, **komunikatów systemu Windows niestandardowego** wpisz *AFX_WM_DRAW2D*. W **nazwa obsługi wiadomości** wpisz *OnDraw2D*. Wybierz **zarejestrowany komunikat** opcji, a następnie wybierz pozycję **OK**. Ta akcja powoduje dodanie obsługi wiadomości do wiadomości AFX_WM_DRAW2D `CMFCD2DWalkthroughView` klasy.

5. W **istniejące programy obsługi** wybierz opcję `OnDraw2D`. Wybierz **Edytuj kod** do wyświetlenia `CMFCD2DWalkthroughView::OnDraw2D` metody. Użyj tego kodu dla `CMFCD2DWalkthroughView::OnDrawD2D` metody:

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

## <a name="to-verify-the-results"></a>Aby zweryfikować wyniki

- Skompiluj i uruchom aplikację. Powinien on gradientu prostokąta, który zmienia podczas zmiany rozmiaru okna. "Witaj świecie!" powinna być wyświetlana w Centrum prostokąta.

## <a name="see-also"></a>Zobacz także

- [Przewodniki](../mfc/walkthroughs-mfc.md)
