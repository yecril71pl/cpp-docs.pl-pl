---
title: 'Wskazówki: Dodawanie animacji do projektu MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e8ae7496daf6827a6be7769d60af10bca45f7a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Wskazówki: dodawanie animacji do projektu MFC
Ten przewodnik zawiera wskazówki jak dodać obiekt animowany podstawowe dla języka Visual C++ projektu Microsoft Foundation Class biblioteki (MFC).  
  
 Instruktaż pokazano, jak wykonać te zadania:  
  
-   Tworzenie aplikacji MFC.  
  
-   Dodawanie menu, a następnie dodaj polecenia, aby uruchomić i zatrzymać animacji.  
  
-   Tworzenie programów obsługi dla poleceń rozpoczęcie i zakończenie.  
  
-   Dodać obiektu do projektu.  
  
-   Centrum animowany obiekt w oknie.  
  
-   Sprawdź wyniki.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku, musi mieć programu Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>Do tworzenia aplikacji MFC  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, w lewym okienku w obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C++** , a następnie wybierz **MFC**. W środkowym okienku wybierz **aplikacji MFC**. W **nazwa** wpisz `MFCAnimationWalkthrough`. Kliknij przycisk **OK**.  
  
3.  W **Kreator aplikacji MFC** okna dialogowego Sprawdź, czy **typu aplikacji** jest **wielu dokumentów**, **styl projektu** jest  **Visual Studio**i **wsparcie dla architektury dokument/widok** opcja jest zaznaczona. Kliknij przycisk **Zakończ**.  
  
### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Dodawanie menu, a następnie dodać polecenia, aby uruchomić i zatrzymać animacji  
  
1.  Na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **widok zasobów**.  
  
2.  W **widok zasobów**, przejdź do **Menu** folder, a następnie otwórz go. Kliknij dwukrotnie `IDR_MFCAnimationWalTYPE` zasobów, aby otworzyć go do modyfikacji.  
  
3.  Na pasku menu w **typu w tym miejscu** wpisz `A&nimation` można utworzyć menu animacji.  
  
4.  W obszarze **animacji**w **typu w tym miejscu** wpisz `Start &Forward` Aby utworzyć polecenie Start do przodu.  
  
5.  W obszarze **Start do przodu**w **typu w tym miejscu** wpisz `Start &Backward`.  
  
6.  W obszarze **Uruchom tyłu**w **typu w tym miejscu** wpisz `S&top` można utworzyć polecenia zatrzymania.  
  
7.  MFCAnimationWalkthrough.rc Zapisz i zamknij go.  
  
8.  W **Eksploratora rozwiązań**, kliknij dwukrotnie MainFrm.cpp, aby otworzyć go do modyfikacji. W `CMainFrame::OnCreate` metody, Znajdź sekcję, która ma kilka wywołań `lstBasicCommands.AddTail`. Zaraz po tej sekcji Dodaj następujący kod.  
  
 ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);

 lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);

    lstBasicCommands.AddTail(ID_ANIMATION_STOP);

 ```  
  
9. Zapisz plik i zamknij go.  
  
### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Aby utworzyć programy obsługi dla uruchomienia i zatrzymania poleceń  
  
1.  Na **projektu** menu, kliknij przycisk **Kreator klas**.  
  
2.  W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz pozycję `CMFCAnimationWalkthroughView`.  
  
3.  Na **polecenia** karcie **identyfikatory obiektów** wybierz opcję `ID_ANIMATION_STARTFORWARD`, a następnie w **wiadomości** wybierz opcję `COMMAND`. Kliknij przycisk **programu obsługi dodawania**.  
  
4.  W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.  
  
5.  W **identyfikatory obiektów** wybierz opcję `ID_ANIMATION_STARTBACKWARD`, a następnie w **wiadomości** wybierz opcję `COMMAND`. Kliknij przycisk **programu obsługi dodawania**.  
  
6.  W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.  
  
7.  W **identyfikatory obiektów** wybierz opcję `ID_ANIMATION_STOP`, a następnie w **wiadomości** wybierz opcję `COMMAND`. Kliknij przycisk **Dodaj obsługę** , a następnie kliknij przycisk **OK**.  
  
8.  W **dodawania funkcji członkowskiej** okno dialogowe, kliknij przycisk **OK**.  
  
9. W **Kreator klas MFC**, kliknij przycisk **OK**.  
  
10. Zapisz MFCAnimationWalkthroughView.cpp, który jest otwarty w edytorze, ale nie zamykaj.  
  
### <a name="to-add-an-animated-object-to-the-project"></a>Aby dodać obiektu do projektu  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie MFCAnimationWalkthroughView.h, aby otworzyć go do modyfikacji. Tuż przed definicją `CMFCAnimationWalkthroughView` klasy, Dodaj następujący kod, aby utworzyć kontroler animacji niestandardowej, która obsłuży planowania powoduje konflikt z obiektu animacji.  
  
 ```  
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
  
2.  Na koniec `CMFCAnimationWalkthroughView` klasy, Dodaj następujący kod.  
  
 ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
 ```  
  
3.  Po `DECLARE_MESSAGE_MAP()` wiersz, Dodaj następujący kod.  
  
 ```  
    void Animate(BOOL bDirection);

 ```  
  
4.  Zapisz plik i zamknij go.  
  
5.  W MFCAnimationWalkthroughView.cpp u góry pliku po `#include` instrukcje ale przed dowolnej metody, klasy Dodaj następujący kod.  
  
 ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
 ```  
  
6.  Na koniec Konstruktor `CMFCAnimationWalkthroughView`, Dodaj następujący kod.  
  
 ```  
    m_animationController.EnableAnimationTimerEventHandler();
m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);

 
    m_animationColor = RGB(255,
    255,
    255);

    m_animationRect = CRect(0,
    0,
    0,
    0);

 
    m_animationColor.SetID(-1,
    nAnimationGroup);

    m_animationRect.SetID(-1,
    nAnimationGroup);

 
    m_animationController.AddAnimationObject(&m_animationColor);

 m_animationController.AddAnimationObject(&m_animationRect);

 ```  
  
7.  Zlokalizuj `CAnimationWalthroughView::PreCreateWindow` metodę i zastąp go następującym kodem.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
 { *// TODO: Modify the Window class or styles here by modifying *//  the CREATESTRUCT cs  
 
    m_animationController.SetRelatedWnd(this);

 return CView::PreCreateWindow(cs);

 }  
 ```  
  
8.  Zlokalizuj `CAnimationWalkthroughView::OnDraw` metodę i zastąp go następującym kodem.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
 {  
    CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
ASSERT_VALID(pDoc);

 if (!pDoc)  
    return; 
 *// TODO: add draw code for native data here  
    CMemDC dcMem(*pDC,
    this);

    CDC& dc = dcMem.GetDC();

 
    CRect rect;  
    GetClientRect(rect);

 
    dc.FillSolidRect(rect,
    GetSysColor(COLOR_WINDOW));

 
    CString strRGB;  
    strRGB.Format(_T("Fill Color is: %d; %d; %d"),
    GetRValue(m_animationColor),
    GetGValue(m_animationColor),
    GetBValue(m_animationColor));

 
    dc.DrawText(strRGB,
    rect,
    DT_CENTER);

    rect.top += nInfoAreaHeight;  
 
    CBrush br;  
 
    br.CreateSolidBrush(m_animationColor);

 CBrush* pBrushOld = dc.SelectObject(&br);

 
    dc.Rectangle((CRect)m_animationRect);

 dc.SelectObject(pBrushOld);

 }  
 ```  
  
9. Na końcu pliku Dodaj poniższy kod.  
  
 ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
 {  
    static UI_ANIMATION_SECONDS duration = 3;  
    static DOUBLE dblSpeed = 35.;  
    static BYTE nStartColor = 50;  
    static BYTE nEndColor = 255;  
 
    BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;  
 
    CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

    CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

    CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

 
    m_animationColor.AddTransition(pRedTransition,
    pGreenTransition,
    pBlueTransition);

 
    CRect rectClient;  
    GetClientRect(rectClient);

 rectClient.top += nInfoAreaHeight;  
 
    int nLeftFinal = bDirection  rectClient.left : rectClient.CenterPoint().x;  
    int nTopFinal = bDirection  rectClient.top : rectClient.CenterPoint().y;  
    int nRightFinal = bDirection  rectClient.right : rectClient.CenterPoint().x;  
    int nBottomFinal = bDirection  rectClient.bottom : rectClient.CenterPoint().y;  
 
    CLinearTransition* pLeftTransition = new CLinearTransition(duration,
    nLeftFinal);

    CLinearTransition* pTopTransition = new CLinearTransition(duration,
    nTopFinal);

    CLinearTransition* pRightTransition = new CLinearTransition(duration,
    nRightFinal);

    CLinearTransition* pBottomTransition = new CLinearTransition(duration,
    nBottomFinal);

 
    m_animationRect.AddTransition(pLeftTransition,
    pTopTransition,
    pRightTransition,
    pBottomTransition);

 
    CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();
CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup,
    pBlueTransition);

 
    pLeftTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pTopTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pRightTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pBottomTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

 
    m_animationController.AnimateGroup(nAnimationGroup);

 }  
 ```  
  
10. Na **projektu** menu, kliknij przycisk **Kreator klas**.  
  
11. W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz pozycję `CMFCAnimationWalkthroughView`.  
  
12. Na **wiadomości** karcie **wiadomości** wybierz opcję `WM_ERASEBKGND`, kliknij przycisk **Dodaj obsługę**, a następnie kliknij przycisk **OK**.  
  
13. W MFCAnimationWalkthroughView.cpp, Zastąp implementację `OnEraseBkgnd` z następującym kodem w celu zmniejszenia migotania w obiekcie animowany, gdy jest narysowany ponownie.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
 {  
    return TRUE;  
 }  
 ```  
  
14. Zastąp implementacje `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, i `CMFCAnimationWalkthroughView::OnAnimationStop` następującym kodem.  
  
 ```  
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
  
15. Zapisz plik i zamknij go.  
  
### <a name="to-center-the-animated-object-in-the-window"></a>Aby wyśrodkować animowany obiekt w oknie  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie MFCAnimationWalkthroughView.h, aby otworzyć go do modyfikacji. Na koniec `CMFCAnimationWalkthroughView` klasy zaraz po definicji `m_animationRect`, Dodaj następujący kod.  
  
 ```  
    BOOL m_bCurrentDirection;  
 ```  
  
2.  Zapisz plik i zamknij go.  
  
3.  Na **projektu** menu, kliknij przycisk **Kreator klas**.  
  
4.  W **Kreator klas MFC**w obszarze **Nazwa klasy**, wybierz pozycję `CMFCAnimationWalkthroughView`.  
  
5.  Na **wiadomości** karcie **wiadomości** wybierz opcję `WM_SIZE`, kliknij przycisk **Dodaj obsługę**, a następnie kliknij przycisk **OK**.  
  
6.  W MFCAnimationWalkthroughView.cpp, Zastąp kod `CMFCAnimationWalkthroughView::OnSize` następującym kodem.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

 
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
  
7.  Na początku Konstruktor `CMFCAnimationWalkthroughView`, Dodaj następujący kod.  
  
 ```  
    m_bCurrentDirection = TRUE;  
 ```  
  
8.  Na początku `CMFCAnimationWalkthroughView::Animate` metody, Dodaj następujący kod.  
  
 ```  
    m_bCurrentDirection = bDirection;  
 ```  
  
9. Zapisz plik i zamknij go.  
  
### <a name="to-verify-the-results"></a>Aby zweryfikować wyniki  
  
1.  Skompiluj i uruchom aplikację. Na **animacji** menu, kliknij przycisk **Start do przodu**. Prostokąt powinna występować, a następnie wprowadź obszaru roboczego. Po kliknięciu **Uruchom tyłu**, powinny odwracać animacji i po kliknięciu **zatrzymać**, należy ją zatrzymać. Kolor wypełnienia prostokąta należy zmieniać w trakcie animacji, a bieżący kolor powinien być wyświetlany w górnej części okna animacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodniki](../mfc/walkthroughs-mfc.md)

