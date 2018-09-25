---
title: 'Wskazówki: Dodawanie animacji do projektu MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 326535395599a76f521100475cfc80b014ba6cd9
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169440"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Wskazówki: dodawanie animacji do projektu MFC

Ten przewodnik omawia sposób dodawania obiekt animowany basic do Visual C++, projektu Microsoft Foundation Class Library (MFC).

Instruktażu przedstawiono sposób wykonywania tych zadań:

- Tworzenie aplikacji MFC.

- Dodawanie menu, a następnie dodaj polecenia, aby uruchomić i zatrzymać animację.

- Tworzenie programów do obsługi dla poleceń rozpoczęcie i zakończenie.

- Dodawanie obiektu do projektu.

- Centrum obiekt animowany w oknie.

- Sprawdź wyniki.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Do przeprowadzenia tego instruktażu, konieczne jest posiadanie programu Visual Studio.

### <a name="to-create-an-mfc-application"></a>Aby utworzyć aplikację MFC

1. Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

1. W **nowy projekt** okno dialogowe, w okienku po lewej stronie w obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C++** , a następnie wybierz **MFC**. W środkowym okienku wybierz **aplikacji MFC**. W **nazwa** wpisz *MFCAnimationWalkthrough*. Kliknij przycisk **OK**.

1. W **Kreator aplikacji MFC** okna dialogowego Sprawdź, czy **typ aplikacji** jest **wiele dokumentów**, **stylu projektu** jest  **Program Visual Studio**i **Obsługa architektury dokument/widok** opcja jest zaznaczona. Kliknij przycisk **Zakończ**.

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Aby dodać menu, a następnie dodaj polecenia, aby uruchomić i zatrzymać animację

1. Na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **widok zasobów**.

1. W **widok zasobów**, przejdź do **Menu** folder i otwórz go. Kliknij dwukrotnie **IDR_MFCAnimationWalkthroughTYPE** zasobów, aby otworzyć ją do modyfikacji.

1. Na pasku menu w **typu w tym miejscu** wpisz *d & każ* Aby utworzyć menu animacji.

1. W obszarze **animacji**w **typu w tym miejscu** wpisz *Start do & przodu* Aby utworzyć polecenie Start do przodu.

1. W obszarze **Start do przodu**w **typu w tym miejscu** wpisz *początkowy adres & Wstecz*.

1. W obszarze **Start zapewniania**w **typu w tym miejscu** wpisz *za & trzymaj* utworzyć polecenie zatrzymania.

1. Zapisz MFCAnimationWalkthrough.rc i zamknij go.

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie MainFrm.cpp, aby otworzyć ją do modyfikacji. W `CMainFrame::OnCreate` metody, odszukaj sekcję, która ma kilka wywołań `lstBasicCommands.AddTail`. Zaraz po tej sekcji Dodaj następujący kod.

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. Zapisz plik i zamknij go.

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Tworzenie programów do obsługi uruchomienia i zatrzymania poleceń

1. Na **projektu** menu, kliknij przycisk **Kreator klas**.

1. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz opcję **CMFCAnimationWalkthroughView**.

1. Na **polecenia** na karcie **identyfikatory obiektów** wybierz opcję **ID_ANIMATION_STARTFORWARD**, a następnie w polu **wiadomości** wybierz  **POLECENIE**. Kliknij przycisk **Dodaj procedurę obsługi**.

1. W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.

1. W **identyfikatory obiektów** wybierz opcję **ID_ANIMATION_STARTBACKWARD**, a następnie w polu **wiadomości** wybierz opcję **polecenia**. Kliknij przycisk **Dodaj procedurę obsługi**.

1. W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.

1. W **identyfikatory obiektów** wybierz opcję **ID_ANIMATION_STOP**, a następnie w polu **wiadomości** wybierz opcję **polecenia**. Kliknij przycisk **Dodaj obsługę** a następnie kliknij przycisk **OK**.

1. W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.

1. W **Kreator klas MFC**, kliknij przycisk **OK**.

1. Zapisz MFCAnimationWalkthroughView.cpp, który jest otwarty w edytorze, ale nie zamykaj.

### <a name="to-add-an-animated-object-to-the-project"></a>Aby dodać obiektu do projektu

1. W Eksploratorze rozwiązań kliknij dwukrotnie MFCAnimationWalkthroughView.h, aby otworzyć ją do modyfikacji. Tuż przed definicją `CMFCAnimationWalkthroughView` klasy, Dodaj następujący kod, aby utworzyć kontroler animacji niestandardowej, która będzie obsługiwać planowania powoduje konflikt z obiektem animacji.

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. Na koniec `CMFCAnimationWalkthroughView` klasy, Dodaj następujący kod.

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. Po `DECLARE_MESSAGE_MAP()` wiersz, Dodaj następujący kod.

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. Zapisz plik i zamknij go.

1. W MFCAnimationWalkthroughView.cpp w górnej części pliku po `#include` instrukcji ale przed każdej klasy, metody, Dodaj następujący kod.

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. Na koniec Konstruktor `CMFCAnimationWalkthroughView`, Dodaj następujący kod.

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. Znajdź `CAnimationWalthroughView::PreCreateWindow` metodę i zastąp go następującym kodem.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. Znajdź `CAnimationWalkthroughView::OnDraw` metodę i zastąp go następującym kodem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)
    {
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
        ASSERT_VALID(pDoc);
        if (!pDoc)
            return;

        // TODO: add draw code for native data here
        CMemDC dcMem(*pDC, this);
        CDC& dc = dcMem.GetDC();
        CRect rect;
        GetClientRect(rect);

        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));

        CString strRGB;
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. Na końcu pliku Dodaj następujący kod.

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. Na **projektu** menu, kliknij przycisk **Kreator klas**.

1. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz opcję **CMFCAnimationWalkthroughView**.

1. Na **wiadomości** na karcie **wiadomości** wybierz opcję **WM_ERASEBKGND**, kliknij przycisk **Dodaj obsługę**, a następnie kliknij przycisk **OK** .

1. W MFCAnimationWalkthroughView.cpp, należy zastąpić implementację `OnEraseBkgnd` następujący kod w celu zmniejszenia migotania w obiekt animowany, gdy jest narysowany ponownie.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. Zastąp implementacje `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, i `CMFCAnimationWalkthroughView::OnAnimationStop` następującym kodem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()
    {
        Animate(TRUE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()
    {
        Animate(FALSE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStop()
    {
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
        if (pManager != NULL)
        {
            pManager->AbandonAllStoryboards();

        }
    }
    ```

1. Zapisz plik i zamknij go.

### <a name="to-center-the-animated-object-in-the-window"></a>Aby wyśrodkować obiekt animowany w oknie

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie MFCAnimationWalkthroughView.h, aby otworzyć ją do modyfikacji. Na koniec `CMFCAnimationWalkthroughView` klasy zaraz po definicji `m_animationRect`, Dodaj następujący kod.

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. Zapisz plik i zamknij go.

1. Na **projektu** menu, kliknij przycisk **Kreator klas**.

1. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz opcję **CMFCAnimationWalkthroughView**.

1. Na **wiadomości** na karcie **wiadomości** wybierz opcję **WM_SIZE**, kliknij przycisk **Dodaj obsługę**, a następnie kliknij przycisk **OK**.

1. W MFCAnimationWalkthroughView.cpp, Zastąp kod `CMFCAnimationWalkthroughView::OnSize` następującym kodem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);
        CRect rect;
        GetClientRect(rect);

        rect.top += nInfoAreaHeight;

        CRect rectAnim = m_animationRect;
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,
        rect.CenterPoint().y - rectAnim.Height() / 2),
        rectAnim.Size());

        if (m_animationController.IsAnimationInProgress())
        {
            Animate(m_bCurrentDirection);
        }
    }
    ```

1. Na początku Konstruktor `CMFCAnimationWalkthroughView`, Dodaj następujący kod.

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. Na początku `CMFCAnimationWalkthroughView::Animate` metody, Dodaj następujący kod.

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. Zapisz plik i zamknij go.

### <a name="to-verify-the-results"></a>Aby sprawdzić oddziaływanie

1. Skompiluj i uruchom aplikację. Na **animacji** menu, kliknij przycisk **Start do przodu**. Prostokąt powinien są wyświetlane, a następnie wprowadź obszaru roboczego. Po kliknięciu **Start zapewniania**, powinny odwracać animacji i po kliknięciu **zatrzymać**, należy go zatrzymać. Kolor wypełnienia prostokąta należy zmieniać w miarę postępów animacji, a bieżący kolor powinien być wyświetlany w górnej części okna animacji.

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
