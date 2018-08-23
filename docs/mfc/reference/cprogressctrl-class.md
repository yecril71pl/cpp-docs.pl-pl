---
title: Klasa CProgressCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93a637c1374e77127a5bf71c6fa736d2857928f1
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465625"
---
# <a name="cprogressctrl-class"></a>Klasa CProgressCtrl
Oferuje funkcje formantu Windows typowego paska postępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Konstruuje `CProgressCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CProgressCtrl::Create](#create)|Tworzy kontrolkę paska postępu i dołącza je do `CProgressCtrl` obiektu.|  
|[CProgressCtrl::CreateEx](#createex)|Tworzy formant postępu przy użyciu określonego stylów rozszerzonej Windows i dołącza je do `CProgressCtrl` obiektu.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego pasek postępu.|  
|[CProgressCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję pasek postępu.|  
|[CProgressCtrl::GetRange](#getrange)|Pobiera dolny i górny limit zakresu kontrolkę paska postępu.|  
|[CProgressCtrl::GetState](#getstate)|Pobiera stan bieżącego formantu paska postępu.|  
|[CProgressCtrl::GetStep](#getstep)|Pobiera przyrost krok aż pasek postępu bieżącego formantu paska postępu.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Bieżące położenie formantu paska postępu jest przesuwany o określoną wartość i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Ustawia kolor paska wskaźnika postępu w bieżącym formantu paska postępu.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła paska postępu.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Włącza tryb zaznaczenia lub wyłącz bieżące formantu paska postępu.|  
|[CProgressCtrl::SetPos](#setpos)|Ustawia bieżącej pozycji formantu paska postępu i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.|  
|[CProgressCtrl::SetRange](#setrange)|Ustawia minimalną i maksymalną zakresy dla formantu paska postępu i ponownie rysuje paska, aby odzwierciedlić nowe zakresy.|  
|[CProgressCtrl::SetState](#setstate)|Ustawia stan bieżący formant paska postępu.|  
|[CProgressCtrl::SetStep](#setstep)|Określa przyrost krok dla formantu paska postępu.|  
|[CProgressCtrl::StepIt](#stepit)|Bieżące położenie formantu paska postępu jest przesuwany o przyrost kroku (zobacz [SetStep](#setstep)) i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.|  
  
## <a name="remarks"></a>Uwagi  
 Formant paska postępu jest oknem które aplikacja może użyć do informowania o postępie długotrwałej operacji. Składa się z prostokąt, który stopniowo jest wypełniony, od lewej do prawej, w systemie kolor wyróżnienia w miarę postępów operacji.  
  
 Formant paska postępu ma zakres i bieżącej pozycji. Zakres reprezentuje łączny czas trwania operacji, a bieżąca pozycja reprezentuje postęp, wprowadzone przez aplikację do wykonywania operacji. Procedurę okna używa zakres i bieżącej pozycji, aby ustalić procent pasek postępu, aby wypełnić kolor wyróżnienia. Ponieważ zakres i bieżącej wartości pozycji są wyrażane jako liczby całkowite ze znakiem, zakres możliwych wartości bieżącej pozycji obejmuje adresy od -2,147,483,648 do 2 147 483 647 (włącznie).  
  
 Aby uzyskać więcej informacji na temat korzystania z `CProgressCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl  
 Konstruuje `CProgressCtrl` obiektu.  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowanie `CProgressCtrl` obiektu, wywołaj `CProgressCtrl::Create` Aby utworzyć formant paska postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Tworzy kontrolkę paska postępu i dołącza je do `CProgressCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl formantu paska postępu. Zastosuj dowolną kombinację stylesdescribed okna w [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie SDK Windows, oprócz pasek style kontrolki do kontrolki postępu następujące:  
  
- Pbs_vertical — Wyświetla postęp informacji w pionie, od góry do dołu. Bez tej flagi kontrolkę paska postępu Wyświetla poziomie, w lewo po prawej stronie.  
  
- Wyświetla pbs_smooth — stopniowe, smooth, wypełniając kontrolkę paska postępu. Bez tej flagi kontrolki spowoduje wypełnienie przy użyciu bloków.  
  
 *Rect*  
 Określa rozmiar i położenie formantu paska postępu. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury. Ponieważ kontrolki musi być okna podrzędnego, określonych współrzędnych są względne wobec obszaru klienckiego *pParentWnd*.  
  
 *pParentWnd*  
 Określa pasek okno nadrzędne kontrolki, postępu, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki paska postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli `CProgressCtrl` obiekt jest pomyślnie utworzony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CProgressCtrl` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, który tworzy `CProgressCtrl` obiektu, a następnie wywołaj `Create`, która tworzy kontrolkę paska postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CProgressCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl formantu paska postępu. Zastosuj dowolną kombinację Style okna ramowego opisanego w [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor bieżącego pasek postępu, reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość lub CLR_DEFAULT Jeśli kolor paska wskaźnika postępu jest domyślny kolor.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Pobiera kolor tła bieżącego pasek postępu.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor tła bieżącego pasek postępu, reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Pobiera bieżącą pozycję pasek postępu.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Położenie formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Położenie formantu paska postępu nie lokalizację fizyczną na ekranie, ale raczej między górny i dolny zakres określonej w [SetRange](#setrange).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Pobiera bieżący dolny i górny limit lub zakresu formantu paska postępu.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 *nLower*  
 Odwołanie do wartości całkowitej odbieranie dolną granicę kontrolkę paska postępu.  
  
 *nUpper*  
 Odwołanie do wartości całkowitej odbieranie górny limit kontrolkę paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja kopiuje wartości dolny i górny limit liczby całkowite, odwołuje się *nLower* i *nUpper*, odpowiednio.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl::GetState  
 Pobiera stan bieżącego formantu paska postępu.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan bieżący formantu paska postępu, który będzie miał jedną z następujących wartości:  
  
|Wartość|Stan|  
|-----------|-----------|  
|PBST_NORMAL|W toku|  
|PBST_ERROR|Błąd|  
|PBST_PAUSED|Wstrzymano|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera stan bieżącego formantu paska postępu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Pobiera przyrost krok aż pasek postępu bieżącego formantu paska postępu.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość przyrostu kroku pasek postępu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość, o którą jest zwiększenie kroku wywołanie [CProgressCtrl::StepIt](#stepit) zwiększa bieżącego położenia obiektu pasek postępu.  
  
 Ta metoda wysyła [PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera przyrost kroku bieżącego formantu paska postępu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Pasek bieżące położenie kontrolki postępu jest przesuwany o określony przez wartość przyrostu *npos —* i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Kwota Przejdź położenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Ustawia kolor paska wskaźnika postępu w bieżącym formantu paska postępu.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *clrBar*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która określa nowy kolor paska wskaźnika postępu. Określ CLR_DEFAULT do powodują pasek postępu używać jej domyślny kolor.|  
  
### <a name="return-value"></a>Wartość zwracana  

Poprzedni kolor paska wskaźnika postępu, reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość lub CLR_DEFAULT Jeśli kolor paska wskaźnika postępu jest domyślny kolor.  
  
### <a name="remarks"></a>Uwagi  

`SetBarColor` Metoda ustawia pasek koloru tylko wtedy, gdy postępu Windows Vista [motyw](/windows/desktop/Controls/visual-styles-overview) nie jest włączone.  
  
 Ta metoda wysyła [PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu zmienia kolor paska postępu czerwony, zielony, niebieski lub wartość domyślną.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Ustawia kolor tła paska postępu.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parametry  
 *clrNew*  
 Wartość COLORREF, która określa nowy kolor tła. Określ wartość CLR_DEFAULT na potrzeby domyślny kolor tła paska postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość wskazującą poprzedni kolor tła lub CLR_DEFAULT, jeśli kolor domyślny kolor tła.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Włącza tryb zaznaczenia lub wyłącz bieżące formantu paska postępu.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *fMarqueeMode*|Wartość true, Włącz tryb zaznaczenia na, lub FAŁSZ, aby wyłączyć tryb zaznaczenia.|  
|[in] *Ninterwał*|Czas w milisekundach między aktualizacjami ramki animacji.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zawsze zwraca wartość TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Gdy jest włączony tryb zaznaczenia, jest animowany pasek postępu i przewija, takich jak logowania theater ruchome obramowanie.  
  
 Ta metoda wysyła [PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod uruchamia i zatrzymuje ramki animacji przewijania.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Ustawia postęp paska bieżące położenie kontrolki określony przez *npos —* i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Nowa pozycja formantu paska postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Położenie formantu paska postępu nie lokalizację fizyczną na ekranie, ale raczej między górny i dolny zakres określonej w [SetRange](#setrange).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Ustawia górny i dolny limit pasek zakresu kontrolki postępu i ponownie rysuje paska, aby odzwierciedlić nowe zakresy.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 *nLower*  
 Określa dolną granicę zakres (wartość domyślna to zero).  
  
 *nUpper*  
 Określa górną granicę zakres (wartość domyślna to 100).  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego `SetRange32` Ustawia zakres 32-bitowych formantu postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 Ustawia stan bieżący formant paska postępu.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *iState*|Stan, aby ustawić pasek postępu. Użyj jednej z następujących wartości:<br /><br /> -PBST_NORMAL — w toku<br />-PBST_ERROR — błąd<br />-PBST_PAUSED - wstrzymana|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni stan bieżący formant paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia stan bieżący formant paska postępu Wstrzymano "lub" w toku.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 Określa przyrost krok dla formantu paska postępu.  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>Parametry  
 *nStep*  
 Nowy krok przyrostu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyrost poprzedniego kroku.  
  
### <a name="remarks"></a>Uwagi  
 Wartość, o którą jest zwiększenie kroku wywołanie `CProgressCtrl::StepIt` zwiększa postęp paska w bieżącym położeniu.  
  
 Wartość kroku domyślna wynosi 10.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Bieżące położenie formantu paska postępu jest przesuwany o przyrost kroku i ponownie rysuje na pasku, aby odzwierciedlić nowe położenie.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Przyrost kroku jest ustawiana przez `CProgressCtrl::SetStep` funkcja elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)


