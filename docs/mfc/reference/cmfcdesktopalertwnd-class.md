---
title: Klasa CMFCDesktopAlertWnd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfebb488921d81c36f842885ad49eae3f40a37fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdesktopalertwnd-class"></a>Klasa CMFCDesktopAlertWnd
`CMFCDesktopAlertWnd` Klasa implementuje funkcje niemodalne okno dialogowe, który jest wyświetlany na ekranie, aby poinformować użytkownika o zdarzeniu.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|Tworzy i inicjuje okno alertu pulpitu.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Zwraca prędkość animacji.|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Zwraca typ animacji.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Zwraca limit czasu automatycznego zamykania.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość podpis.|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Zwraca ostatni prawidłową pozycję oknie alertu pulpitu na ekranie.|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Zwraca poziom przezroczystości.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Określa, czy okna alertu pulpitu jest wyświetlana z podpisem mała.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk łącze znajduje się w menu alertu pulpitu.|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Struktura wywołuje funkcji członkowskiej, gdy użytkownik wybierze element menu, gdy formant podrzędny wysyła powiadomienie, lub gdy jest translacja klawiszy skrótów. (Przesłania [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Ustawia nowe prędkość animacji.|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Ustawia typ animacji.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Ustawia limit czasu automatycznego zamykania.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Przełącza między małych i normalnym podpisów.|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Ustawia poziom przezroczystości.|  
  
## <a name="remarks"></a>Uwagi  
 Pulpitu oknie alert może być przezroczysty, może wystąpić z efektami animacji i może zniknąć, (po określonym czasie lub gdy użytkownik odrzuci go, klikając przycisk Zamknij).  
  
 Pulpitu oknie alert może również zawierać domyślne okno dialogowe, które z kolei zawiera ikonę, tekst komunikatu (etykieta) oraz łącza. Alternatywnie pulpitu oknie alert może zawierać niestandardowe okno dialogowe z zasobów aplikacji.  
  
 Można utworzyć pulpitu alertu okna w dwóch krokach. Najpierw należy wywołać konstruktora, aby utworzyć `CMFCDesktopAlertWnd` obiektu. Po drugie, wywołaj [CMFCDesktopAlertWnd::Create](#create) funkcji członkowskiej utworzyć okna i dołączenie go do `CMFCDesktopAlertWnd` obiektu.  
  
 `CMFCDesktopAlertWnd` Obiektu tworzy specjalne podrzędne okno dialogowe, które wypełnia obszaru klienckiego okna alertu pulpitu. Okno dialogowe jest właścicielem wszystkich kontrolek, które znajdują się na nim.  
  
 Aby wyświetlić okno dialogowe niestandardowe w oknie podręcznym, wykonaj następujące kroki:  
  
1.  Klasa wyprowadzona z `CMFCDesktopAlertDialog`.  
  
2.  Tworzenie szablonu okno podrzędne okna dialogowego w zasobach.  
  
3.  Wywołanie [CMFCDesktopAlertWnd::Create](#create) przy użyciu Identyfikatora zasobu szablon okno dialogowe i wskaźnika do informacji o klasie czasu wykonywania klasy pochodnej.  
  
4.  Okno dialogowe niestandardowe, aby obsłużyć wszystkie powiadomienia pochodzące z formantów hostowanej program lub program hostowanej służy do obsługi te powiadomienia bezpośrednio.  
  
 Do sterowania zachowaniem pulpitu oknie alert, należy użyć następujących funkcji:  
  
-   Ustaw typ animacji przez wywołanie metody [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Prawidłowe opcje to ujawniać, Przesuń i stopniowe.  
  
-   Ustaw szybkość ramki animacji przez wywołanie metody [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).  
  
-   Ustaw poziom przezroczystości wywołując [CMFCDesktopAlertWnd::SetTransparency](#settransparency).  
  
-   Zmień rozmiar podpisu dla małych wywołując [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Mała podpis jest 7 pikseli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia różnych metod w `CMFCDesktopAlertWnd` klasa do konfigurowania `CMFCDesktopAlertWnd` obiektu. W przykładzie przedstawiono sposób ustawić typ animacji, ustaw przezroczystość okno podręczne, określ, czy w oknie alert zawiera nagłówek małych i ustaw czas, jaki upływa przed oknie alert zostanie automatycznie zamknięte. W przykładzie pokazano również sposób tworzenia i inicjowania okna alertu pulpitu. Następujący fragment kodu jest częścią [próbka Demo alertu pulpitu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>CMFCDesktopAlertWnd::Create  
 Tworzy i inicjuje okno alertu pulpitu.  
  
```  
virtual BOOL Create(
    CWnd* pWndOwner,  
    UINT uiDlgResID,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1),  
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

 
virtual BOOL Create(
    CWnd* pWndOwner,  
    CMFCDesktopAlertWndInfo& params,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1));
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pWndOwner`  
 Określa właściciela oknie alert. Tego właściciela Zadzwonimy wszystkie powiadomienia dla alertów oknie pulpitu. Ta wartość nie może być `NULL`.  
  
 [in]`uiDlgResID`  
 Określa identyfikator zasobu okna alertu.  
  
 [in]`hMenu`  
 Określa menu wyświetlanym po kliknięciu przycisku menu. Jeśli `NULL`, nie jest wyświetlany przycisk menu.  
  
 [in]`ptPos`  
 Określa położenie początkowe, w którym jest wyświetlana w oknie alert, za pomocą współrzędnych ekranu. Jeśli ten parametr ma (-1, -1), w oknie alert jest wyświetlany w prawym dolnym rogu ekranu.  
  
 [in]`pRTIDlgBar`  
 Informacje o klasie czasu wykonywania dla klasy pole niestandardowe okno dialogowe, które obejmuje obszaru klienckiego okna alertu.  
  
 [in]`params`  
 Określa parametry, które są używane w celu utworzenia okna alertu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w oknie alert został utworzony pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę w celu utworzenia okna alertu. Obszar klienta okna alertu zawiera podrzędne okno dialogowe, które obsługuje wszystkie formanty, które są wyświetlane dla użytkownika.  
  
 Pierwszy przeciążenie metody tworzy okno alertu, zawierającą podrzędne okno dialogowe, które są ładowane z zasobów aplikacji. Pierwszy przeciążenie metody można również określić informacje o klasie czasu wykonywania dla klasy okno dialogowe niestandardowych.  
  
 Drugi przeciążenie metody tworzy okno alertu, zawierający domyślne formanty. Można określić, która kontroluje, aby wyświetlić modyfikując [CMFCDesktopAlertWndInfo klasy](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).  
  
##  <a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 Zwraca prędkość animacji.  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szybkość animacji okna alertu, w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Szybkość animacji opisuje tempa otwiera i zamyka w oknie alert.  
  
##  <a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 Zwraca typ animacji.  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden z następujących typów animacji:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime  
 Zwraca limit czasu automatycznego zamykania.  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Czas w milisekundach, po jakim oknie alert zostanie automatycznie zamknięte.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby określić, ile czasu powinno, po jakim oknie alert zostanie automatycznie zamknięte.  
  
##  <a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 Zwraca wysokość podpis.  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach podpisu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może zostać zastąpiona w klasie pochodnej. Domyślna implementacja albo: zwraca podpis mała wartość wysokości (w pikselach 7), jeśli powinien być wyświetlany w oknie podręcznym małych podpis lub wartość uzyskane z funkcji Windows API `GetSystemMetrics(SM_CYSMCAPTION)`.  
  
##  <a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 Zwraca ostatnie położenie okna alertu pulpitu na ekranie.  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Punkt, we współrzędnych ekranu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca ostatniej pozycji prawidłowe w oknie alert na ekranie.  
  
##  <a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 Zwraca poziom przezroczystości.  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Poziom przezroczystości zakresu od 0 do 255 włącznie. Im większa wartość, więcej nieprzezroczyste okna.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody można pobrać bieżący poziom przezroczystości oknie alert.  
  
##  <a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 Określa, czy pulpitu oknie alert ma małych podpisu lub podpis zwykły rozmiar.  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w oknie podręcznym jest wyświetlany z tekstem małych; `FALSE` Jeśli oknie podręcznym jest wyświetlane z tekstem o rozmiarze regularne.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby określić, czy w oknie podręcznym małych podpisu lub podpis zwykły rozmiar. Domyślnie małych podpis jest 7 pikseli. Wysokość podpis zwykły rozmiar można uzyskać przez wywołanie funkcji Windows API `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`CPoint&`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk łącze znajduje się w menu alertu pulpitu.  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdID`  
 Ten parametr nie jest używany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w klasie pochodnej, aby otrzymać powiadomienie, gdy użytkownik kliknie łącze w oknie alert.  
  
##  <a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`wParam`  
 [in]`lParam`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hwnd`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed  
 Ustawia nowe prędkość animacji.  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nSpeed`  
 Określa nowe prędkość animacji, w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby ustawić szybkość animacji oknie alert. Szybkość animacji domyślny to 30 milisekund.  
  
##  <a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 Ustawia typ animacji.  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`type`  
 Określa typ animacji.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby ustawić typ animacji. Można określić jedną z następujących wartości:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime  
 Ustawia limit czasu automatycznego zamykania.  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTime`  
 Czas w milisekundach, który musi upłynąć przed oknie alert zostanie automatycznie zamknięte.  
  
### <a name="remarks"></a>Uwagi  
 W oknie alert zostaje automatycznie zamknięty po określonym czasie, jeśli użytkownik nie wchodzi w interakcję z okna.  
  
##  <a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 Przełącza między małych i rozmiar regular podpisów.  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bSmallCaption`  
 `TRUE`Aby określić, czy w oknie alert zawiera nagłówek małych; w przeciwnym razie `FALSE` do określenia, czy w oknie alert zawiera nagłówek zwykły rozmiar.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wyświetlić małe lub zwykły rozmiar podpisu. Domyślnie małych podpis jest 7 pikseli. Rozmiar podpisu regularnych można uzyskać przez wywołanie funkcji Windows API `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 Ustawia poziom przezroczystości okna podręcznego.  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTransparency`  
 Określa poziom przezroczystości. Ta wartość musi być z zakresu od 0 do 255 włącznie. Im większa wartość, więcej nieprzezroczyste okna.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić poziom przezroczystości okna podręcznego.  
  
##  <a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)
