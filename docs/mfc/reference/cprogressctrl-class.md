---
title: Cprogressctrl — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6317ce9484cc471611762d10e6f1482f24c2742a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378324"
---
# <a name="cprogressctrl-class"></a>Cprogressctrl — klasa
Udostępnia funkcje formantu paska postępu wspólnej systemu Windows.  
  
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
|[CProgressCtrl::Create](#create)|Tworzy kontrolkę paska postępu i dołącza go do `CProgressCtrl` obiektu.|  
|[CProgressCtrl::CreateEx](#createex)|Tworzy formantu postępu w określonym stylu rozszerzonej systemu Windows i dołącza go do `CProgressCtrl` obiektu.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego pasek postępu.|  
|[CProgressCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję pasek postępu.|  
|[CProgressCtrl::GetRange](#getrange)|Pobiera dolny i górny limit zakresu formantu paska postępu.|  
|[CProgressCtrl::GetState](#getstate)|Pobiera stan bieżącego formantu paska postępu.|  
|[CProgressCtrl::GetStep](#getstep)|Pobiera przyrost kroku paska postępu bieżącego formantu paska postępu.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Przesuwa bieżącej pozycji formantu paska postępu o określoną wartość i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Ustawia kolor linii paska wskaźnika postępu w bieżącym formantu paska postępu.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła paska postępu.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Włącza tryb ustawiony na marquee lub wyłącz bieżącego formantu paska postępu.|  
|[CProgressCtrl::SetPos](#setpos)|Ustawia bieżącego położenia kontrolki paska postępu i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.|  
|[CProgressCtrl::SetRange](#setrange)|Ustawia zakresy minimalną i maksymalną dla formantu paska postępu i ponownie rysuje pasku w celu uwzględnienia nowych zakresów.|  
|[CProgressCtrl::SetState](#setstate)|Ustawia stan bieżącego formantu paska postępu.|  
|[CProgressCtrl::SetStep](#setstep)|Określa przyrost krok dla formantu paska postępu.|  
|[CProgressCtrl::StepIt](#stepit)|Przechodzi przez przyrost krok bieżącego położenia kontrolki paska postępu (zobacz [SetStep](#setstep)) i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolka paska postępu jest oknem, używaną przez aplikację do przedstawienia postępu długotrwałej operacji. Składa się z prostokąt stopniowo jest wypełniony, od lewej do prawej strony, w systemie kolor zaznaczenia w trakcie operacji.  
  
 Kontrolka paska postępu ma zakres i bieżącego położenia. Zakres reprezentuje całkowity czas trwania operacji, a bieżące położenie — postęp wprowadzone aplikacji ukończenia operacji. Procedurę okna korzysta z zakresu i bieżącą pozycję, aby określić procent pasek postępu, aby wypełnić kolorem wyróżnienia. Ponieważ zakresu i bieżące wartości pozycji są wyrażane jako liczb całkowitych ze znakiem, jest możliwej bieżącej wartości pozycji od -2,147,483,648 2 147 483 647 włącznie.  
  
 Aby uzyskać więcej informacji na temat używania `CProgressCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
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
 Po konstruowania `CProgressCtrl` obiekt, należy wywołać `CProgressCtrl::Create` można utworzyć formantu paska postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Tworzy kontrolkę paska postępu i dołącza go do `CProgressCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu paska postępu. Zastosuj dowolną kombinację stylesdescribed okna w [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie SDK systemu Windows oprócz pasek stylów formantu do formantu postępu następujące:  
  
- `PBS_VERTICAL` Wyświetla postęp informacji w pionie, od góry do dołu. Bez tej flagi formantu paska postępu Wyświetla poziomie, do lewej do prawej.  
  
- `PBS_SMOOTH` Wyświetla stopniowe, smooth wypełnianie formantu paska postępu. Bez tej flagi formantu wprowadzi bloków.  
  
 `rect`  
 Określa rozmiar i położenie formantu paska postępu. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury. Ponieważ formantu musi być oknem podrzędnym, określonych współrzędnych są względem obszaru klienckiego `pParentWnd`.  
  
 `pParentWnd`  
 Określa postęp paska okno nadrzędne kontrolki, zwykle `CDialog`. Nie może być **wartości NULL.**  
  
 `nID`  
 Określa identyfikator formantu paska postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli `CProgressCtrl` obiektu jest pomyślnie utworzony; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CProgressCtrl` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, który tworzy `CProgressCtrl` obiekt, a następnie wywołać **Utwórz**, która tworzy kontrolkę paska postępu.  
  
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
 `dwExStyle`  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa styl formantu paska postępu. Zastosuj dowolną kombinację Style okna opisanego w [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie Windows SDK.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor bieżącego pasek postępu, reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, lub `CLR_DEFAULT` Jeśli kolor paska wskaźnika postępu jest domyślny kolor.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Pobiera kolor tła bieżącego pasek postępu.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor tła paska postępu bieżącego reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Pobiera bieżącą pozycję pasek postępu.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Pozycja formantu paska postępu nie jest to lokalizację fizyczną na ekranie, ale raczej między górny i dolny zakres określonej w [SetRange](#setrange).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Pobiera bieżący limity dolna i górna lub zakresu formantu paska postępu.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nLower`  
 Odwołanie do typu integer odbieranie dolny limit formantu paska postępu.  
  
 `nUpper`  
 Odwołanie do typu integer odbieranie górne granice formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja kopiuje wartości limitów dolna i górna na liczby całkowite, odwołuje się `nLower` i `nUpper`odpowiednio.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl::GetState  
 Pobiera stan bieżącego formantu paska postępu.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan bieżący formantu paska postępu, które jest jednym z następujących wartości:  
  
|Wartość|Stan|  
|-----------|-----------|  
|`PBST_NORMAL`|w toku|  
|`PBST_ERROR`|Błąd|  
|`PBST_PAUSED`|Wstrzymane|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera stan bieżącego formantu paska postępu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Pobiera przyrost kroku paska postępu bieżącego formantu paska postępu.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyrost krok pasek postępu.  
  
### <a name="remarks"></a>Uwagi  
 Przyrost kroku jest wartość, o którą wywołanie [CProgressCtrl::StepIt](#stepit) zwiększa bieżąca pozycja paska postępu.  
  
 Ta metoda wysyła [PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera przyrost krok bieżącego formantu paska postępu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Przechodzi przez określony przez wartość przyrostu pasek bieżącego położenia kontrolki postępu `nPos` i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Kwota można poprawić położenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Ustawia kolor linii paska wskaźnika postępu w bieżącym formantu paska postępu.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `clrBar`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która określa nowy kolor paska wskaźnika postępu. Określ `CLR_DEFAULT` spowodować pasek postępu użyć jego domyślny kolor.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie kolor pasek postępu wskaźnika reprezentowane jako [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, lub `CLR_DEFAULT` Jeśli kolor paska wskaźnika postępu jest domyślny kolor.  
  
### <a name="remarks"></a>Uwagi  
 `SetBarColor` Metoda ustawia pasek koloru tylko wtedy, gdy postępu [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] [motyw](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx) nie jest włączone.  
  
 Ta metoda wysyła [PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu zmienia kolor pasek postępu do czerwony, zielony, niebieski lub wartość domyślną.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Ustawia kolor tła paska postępu.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parametry  
 `clrNew`  
 A **COLORREF** wartość, która określa nowy kolor tła. Określ `CLR_DEFAULT` wartość domyślny kolor tła dla pasek postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość wskazującą poprzedniej kolor tła lub **CLR_DEFAULT** Jeśli kolor tła jest domyślny kolor.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Włącza tryb ustawiony na marquee lub wyłącz bieżącego formantu paska postępu.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `fMarqueeMode`|`true` Aby włączyć tryb zaznaczenia, lub `false` wyłączyć tryb ustawiony na marquee.|  
|[in] `nInterval`|Czas w milisekundach między aktualizacjami animacji neonu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zawsze zwraca `true`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy jest włączony tryb zaznaczenia, paska postępu jest animowany i przewija, takich jak logowania ramkę kina.  
  
 Ta metoda wysyła [PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod uruchamia i zatrzymuje neon przewijanie animacji.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Ustawia postęp paska bieżącego położenia kontrolki określony przez `nPos` i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Nowa pozycja formantu paska postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Pozycja formantu paska postępu nie jest to lokalizację fizyczną na ekranie, ale raczej między górny i dolny zakres określonej w [SetRange](#setrange).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Ustawia górny i dolny limit pasek zakresu formantu postępu i ponownie rysuje pasku w celu uwzględnienia nowych zakresów.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nLower`  
 Określa dolny limit zakresu (wartość domyślna to zero).  
  
 `nUpper`  
 Określa górny limit zakresu (wartość domyślna to 100).  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska `SetRange32` ustawia zakresu 32-bitowych formantu postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 Ustawia stan bieżącego formantu paska postępu.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `iState`|Stan można ustawić pasek postępu. Użyj jednej z następujących wartości:<br /><br /> - `PBST_NORMAL` — W toku<br />- `PBST_ERROR` — Błąd<br />- `PBST_PAUSED` -Wstrzymana|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni stan bieżący formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_progressCtrl`, która jest używana do uzyskania programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia stan bieżącego formantu paska postępu, wstrzymana lub w toku.  
  
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
 Przyrost kroku jest wartość, o którą wywołanie `CProgressCtrl::StepIt` zwiększa postęp paska jego bieżącym położeniu.  
  
 Wartość kroku domyślna to 10.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Przesuwa bieżącego położenia kontrolki paska postępu przez przyrost kroku i ponownie rysuje pasku w celu uwzględnienia nowej pozycji.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji formantu paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Przyrost kroku jest ustawiana przez `CProgressCtrl::SetStep` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)


