---
title: Klasa CSpinButtonCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 810b59bb85d374b1cf65985a64be32c645e6f3b5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718084"
---
# <a name="cspinbuttonctrl-class"></a>Klasa CSpinButtonCtrl
Oferuje funkcje formantu Windows typowego przycisku pokrętła.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Konstruuje `CSpinButtonCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|Tworzy kontrolkę przycisku pokrętła i dołącza je do `CSpinButtonCtrl` obiektu.|  
|[CSpinButtonCtrl::CreateEx](#createex)|Tworzy kontrolkę przycisku pokrętła z określonym style rozszerzone Windows i dołącza go do `CSpinButtonCtrl` obiektu.|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|Pobiera informacje przyspieszenie dla kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::GetBase](#getbase)|Pobiera bieżący podstawa kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Pobiera wskaźnik do bieżącego okna buddy.|  
|[CSpinButtonCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::GetRange](#getrange)|Pobiera górny i dolny limit (zakres) na kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|Ustawia przyspieszanie kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::SetBase](#setbase)|Ustawia podstawa kontrolkę przycisku pokrętła.|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Ustawia okno cyklu kontrolki przycisku pokrętła.|  
|[CSpinButtonCtrl::SetPos](#setpos)|Ustawia bieżące położenie kontrolki.|  
|[CSpinButtonCtrl::SetRange](#setrange)|Ustawia górny i dolny limit (zakres) na kontrolkę przycisku pokrętła.|  
  
## <a name="remarks"></a>Uwagi  
 "Kontrolkę przycisku pokrętła" (określana także jako kontrolkę w górę i w dół) jest parę przycisków strzałek, który użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość, na przykład położenie przewijania lub liczbą wyświetlany w formancie pomocnika. Wartość skojarzona z kontrolkę przycisku pokrętła nosi nazwę bieżącej pozycji. Kontrolka przycisku pokrętła jest najczęściej używana z kontrolką pomocnika o nazwie "okno buddy".  
  
 Ta kontrolka (i w związku z tym `CSpinButtonCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Użytkownikowi kontrolkę przycisku pokrętła i okna buddy często wyglądać jeden formant. Można określić, że kontrolkę przycisku pokrętła automatycznie rozmieszczaj się obok okna znajomy i powoduje on automatyczne ustawienie podpis okna zaprzyjaźnionego do jego bieżącej pozycji. Za pomocą kontrolkę przycisku pokrętła i formant edycji na monitowanie użytkownika o wprowadzenie danych liczbowych.  
  
 Kliknij strzałkę w górę przenosi bieżącej pozycji w kierunku maksymalną, a następnie klikając strzałkę w dół przenosi bieżącą pozycję w kierunku minimum. Domyślnie wartość minimalna to 100, a maksymalna wartość to 0. Zawsze, gdy ustawienie minimalnej jest większa niż wartość maksymalna, ustawienia (na przykład, gdy używane są ustawienia domyślne), klikając się zmniejsza strzałkę wartość pozycji i klikając strzałkę w dół jej zwiększenie.  
  
 Kontrolkę przycisku pokrętła bez okno cyklu działa jako sortowania paska przewijania uproszczone. Kontrolka karty wyświetla czasami kontrolkę przycisku pokrętła, aby umożliwić użytkownikowi przewiń dodatkowe karty do widoku.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CSpinButtonCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [przy użyciu CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="create"></a>  CSpinButtonCtrl::Create  
 Tworzy kontrolkę przycisku pokrętła i dołącza je do `CSpinButtonCtrl` obiektu...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl kontrolki przycisku pokrętła. Zastosuj dowolną kombinację style kontrolki przycisku pokrętła do formantu. Te style są opisane w [style kontrolki góra-dół](/windows/desktop/Controls/up-down-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Określa rozmiar i położenie kontrolki przycisku pokrętła. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury  
  
 *pParentWnd*  
 Wskaźnik do okno nadrzędne kontrolki przycisku pokrętła, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki przycisku pokrętła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli inicjowanie się powiodła. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CSpinButtonCtrl` obiekt w dwóch etapach, wywołanie konstruktora, a następnie wywołaj `Create`, która tworzy kontrolkę przycisku pokrętła i dołącza go do `CSpinButtonCtrl` obiektu.  
  
 Aby utworzyć kontrolkę przycisku pokrętła rozszerzone Style okna, należy wywołać [CSpinButtonCtrl::CreateEx](#createex) zamiast `Create`.  
  
##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CSpinButtonCtrl` obiektu.  
  
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
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę style rozszerzone systemu windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl kontrolki przycisku pokrętła. Zastosuj dowolną kombinację style kontrolki przycisku pokrętła do formantu. Te style są opisane w [style kontrolki góra-dół](/windows/desktop/Controls/up-down-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows WS_EX_.  
  
##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl  
 Konstruuje `CSpinButtonCtrl` obiektu.  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel  
 Pobiera informacje przyspieszenie dla kontrolkę przycisku pokrętła.  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nAccel*  
 Liczba elementów w tablicy, określony przez *pAccel*.  
  
 *pAccel*  
 Wskaźnik do tablicy [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) struktur, które otrzymuje informacje przyspieszenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba klawiszy skrótów struktur pobrać.  
  
##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase  
 Pobiera bieżący podstawa kontrolkę przycisku pokrętła.  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość podstawowy.  
  
##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy  
 Pobiera wskaźnik do bieżącego okna buddy.  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego okna buddy.  
  
##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos  
 Pobiera bieżącą pozycję kontrolkę przycisku pokrętła.  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpbError*  
 Wskaźnik na wartość logiczną, która jest równa zero, jeśli wartość jest pobrane pomyślnie, lub wartości zero, jeśli wystąpi błąd. Jeśli ten parametr ma wartość null, nie są zgłaszane błędy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja Zwraca 16-bitowych bieżącą pozycję w programie word niskiego rzędu. Word wyższego rzędu jest różna od zera, jeśli wystąpił błąd.  
  
 Druga wersja zwraca pozycję 32-bitowych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przetwarzania wartości zwracanej, formant aktualizuje swoją bieżącą pozycję w oparciu o podpis okna zaprzyjaźnionego. Formant zwraca błąd, jeśli istnieje nie okno znajomy lub podpis określa wartość nieprawidłowa lub spoza zakresu.  
  
##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange  
 Pobiera górny i dolny limit (zakres) na kontrolkę przycisku pokrętła.  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Niższy*  
 Odwołanie do liczby całkowitej, która odbiera dolną granicę dla formantu.  
  
 *górny*  
 Odwołanie do liczba całkowita, która odbiera górną granicę dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja zwraca 32-bitową wartość zawierającą górny i dolny limit. Word niskiego rzędu jest górną granicę dla formantu, a program word wyższego rzędu jest niższy limit.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego `GetRange32` pobiera zakres kontrolka przycisku pokrętła jako liczba całkowita 32-bitowych.  
  
##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel  
 Ustawia przyspieszanie kontrolkę przycisku pokrętła.  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parametry  
 *nAccel*  
 Liczba [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) struktury określony przez *pAccel*.  
  
 *pAccel*  
 Wskaźnik do tablicy UDACCEL struktur, które zawierają informacje przyspieszenia. Elementy powinny być sortowane w kolejności rosnącej na podstawie `nSec` elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase  
 Ustawia podstawa kontrolkę przycisku pokrętła.  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>Parametry  
 *nBase*  
 Nowa wartość podstawowa dla formantu. Może być 10 miejsc dziesiętnych lub 16 w formacie szesnastkowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie wartości bazowej w przypadku powodzenia lub wartość zero, jeśli podano nieprawidłową podstawę.  
  
### <a name="remarks"></a>Uwagi  
 Podstawowa wartość określa, czy okno buddy zawiera liczby cyfr dziesiętnych lub szesnastkowych. Liczby szesnastkowe nigdy nie mają znaku; Zalogowano się liczby dziesiętne.  
  
##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy  
 Ustawia okno cyklu kontrolki przycisku pokrętła.  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndBuddy*  
 Wskaźnik do nowego okna buddy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do poprzedniego okna buddy.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolki pokrętła prawie zawsze jest skojarzony z innego okna, takie jak formant edycji, który wyświetla część zawartości. To inne okno nosi nazwę "buddy" kontrolki pokrętła.  
  
##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos  
 Ustawia bieżącej pozycji na kontrolkę przycisku pokrętła.  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Nowa pozycja dla formantu. Ta wartość musi być w zakresie określonym przez górny i dolny limit dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji (16-bitową precyzję `SetPos`32- bitowy precyzji dla `SetPos32`).  
  
### <a name="remarks"></a>Uwagi  
 `SetPos32` Ustawia położenie 32-bitowych.  
  
##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange  
 Ustawia górny i dolny limit (zakres) na kontrolkę przycisku pokrętła.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry

*nLower* i *nUpper*<br/>
Górne i dolne granice formantu. Aby uzyskać `SetRange`, ani limit może być większa niż UD_MAXVAL lub mniejszą od UD_MINVAL; Ponadto różnica między dwoma limity nie może przekraczać UD_MAXVAL. `SetRange32` nie nakłada żadnych ograniczeń na granicach; użyć dowolnej liczby całkowite.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego `SetRange32` Ustawia zakres 32-bitowych dla kontrolki przycisku pokrętła.  
  
> [!NOTE]
>  Domyślny zakres dla przycisku pokrętła ma maksymalną wartość zero (0) i co najmniej równa 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, klikając strzałkę w górę zostaną obniżone pozycję i klikając strzałkę w dół zwiększy jej. Użyj `CSpinButtonCtrl::SetRange` dostosować te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSliderCtrl](../../mfc/reference/csliderctrl-class.md)
