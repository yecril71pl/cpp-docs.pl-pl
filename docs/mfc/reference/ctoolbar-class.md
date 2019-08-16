---
title: Klasa CToolBar
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502388"
---
# <a name="ctoolbar-class"></a>Klasa CToolBar

Paski sterowania, które mają wiersz przycisków mapy bitowej i separatory opcjonalne.

## <a name="syntax"></a>Składnia

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolBar:: CToolBar](#ctoolbar)|Konstruuje `CToolBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolBar:: CommandToIndex](#commandtoindex)|Zwraca indeks przycisku z danym IDENTYFIKATORem polecenia.|
|[CToolBar:: Create](#create)|Tworzy pasek narzędzi systemu Windows i dołącza go do `CToolBar` obiektu.|
|[CToolBar:: CreateEx](#createex)|Tworzy obiekt z dodatkowymi stylami dla osadzonego `CToolBarCtrl` obiektu. `CToolBar`|
|[CToolBar:: GetButtonInfo](#getbuttoninfo)|Pobiera identyfikator, styl i numer obrazu przycisku.|
|[CToolBar:: getbutton](#getbuttonstyle)|Pobiera styl przycisku.|
|[CToolBar:: GetButtonText](#getbuttontext)|Pobiera tekst, który będzie wyświetlany na przycisku.|
|[CToolBar:: GetItemID](#getitemid)|Zwraca identyfikator polecenia przycisku lub separatora w danym indeksie.|
|[CToolBar:: GetItemRect](#getitemrect)|Pobiera prostokąt wyświetlania dla elementu pod podanym indeksem.|
|[CToolBar:: GetToolBarCtrl](#gettoolbarctrl)|Zezwala na bezpośredni dostęp do podstawowej kontroli wspólnej.|
|[CToolBar:: LoadBitmap](#loadbitmap)|Ładuje mapę bitową zawierającą obrazy przycisków map bitowych.|
|[CToolBar:: LoadToolBar](#loadtoolbar)|Ładuje zasób paska narzędzi utworzony za pomocą edytora zasobów.|
|[CToolBar:: setmap](#setbitmap)|Ustawia obraz mapy bitowej.|
|[CToolBar:: SetButtonInfo](#setbuttoninfo)|Ustawia identyfikator, styl i numer obrazu przycisku.|
|[CToolBar:: SetButtons](#setbuttons)|Ustawia style przycisków i indeks obrazów przycisków w mapie bitowej.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku.|
|[CToolBar:: SetButtonText](#setbuttontext)|Ustawia tekst, który będzie wyświetlany na przycisku.|
|[CToolBar:: setheight](#setheight)|Ustawia wysokość paska narzędzi.|
|[CToolBar:: SetSizes](#setsizes)|Ustawia rozmiary przycisków i ich mapy bitowe.|

## <a name="remarks"></a>Uwagi

Przyciski mogą pełnić rolę przycisków, przycisków pól wyboru lub przycisków radiowych. `CToolBar`obiekty są zwykle osadzonymi elementami członkowskimi obiektów okien ramowych, które pochodzą z klasy [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar:: GetToolBarCtrl](#gettoolbarctrl), funkcja członkowska New to MFC 4,0, umożliwia korzystanie z pomocy technicznej formantu wspólnego systemu Windows na potrzeby dostosowywania pasków narzędzi i dodatkowych funkcji. `CToolBar`funkcje składowe zapewniają większość funkcji formantów standardowych systemu Windows; Jednak po wywołaniu `GetToolBarCtrl`programu można dać paski narzędzi jeszcze bardziej charakterystykę pasków narzędzi systemu Windows 95/98. Po wywołaniu `GetToolBarCtrl`, zwróci odwołanie `CToolBarCtrl` do obiektu. Zobacz [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) , aby uzyskać więcej informacji na temat projektowania pasków narzędzi przy użyciu standardowych formantów systemu Windows. Aby uzyskać więcej ogólnych informacji na temat typowych kontrolek, zobacz [typowe kontrolki](/windows/win32/Controls/common-controls-intro) w Windows SDK.

Wizualizacja C++ oferuje dwie metody tworzenia paska narzędzi. Aby utworzyć zasób paska narzędzi przy użyciu edytora zasobów, wykonaj następujące kroki:

1. Utwórz zasób paska narzędzi.

1. Konstruowanie `CToolBar` obiektu.

1. Wywołaj funkcję [Create](#create) (lub [CreateEx](#createex)), aby utworzyć pasek narzędzi systemu Windows i dołączyć `CToolBar` go do obiektu.

1. Zadzwoń do [LoadToolBar](#loadtoolbar) w celu załadowania zasobu paska narzędzi.

W przeciwnym razie wykonaj następujące kroki:

1. Konstruowanie `CToolBar` obiektu.

1. Wywołaj funkcję [Create](#create) (lub [CreateEx](#createex)), aby utworzyć pasek narzędzi systemu Windows i dołączyć `CToolBar` go do obiektu.

1. Wywołaj [LoadBitmap](#loadbitmap) w celu załadowania mapy bitowej zawierającej obrazy przycisków paska narzędzi.

1. Wywołaj SetButtons, aby ustawić styl przycisku i skojarzyć każdy przycisk z obrazem w mapie bitowej. [](#setbuttons)

Wszystkie obrazy przycisków na pasku narzędzi są pobierane z jednej mapy bitowej, która musi zawierać jeden obraz dla każdego przycisku. Wszystkie obrazy muszą mieć ten sam rozmiar; wartość domyślna to 16 pikseli o szerokości i 15 pikseli. Obrazy muszą znajdować się obok siebie w mapie bitowej.

`SetButtons` Funkcja przyjmuje wskaźnik do tablicy identyfikatorów kontrolek i liczby całkowitej, która określa liczbę elementów w tablicy. Funkcja ustawia identyfikator każdego przycisku na wartość odpowiadającego elementu tablicy i przypisuje Każdemu przyciskowi indeks obrazu, który określa położenie obrazu przycisku w mapie bitowej. Jeśli element tablicy ma wartość ID_SEPARATOR, nie jest przypisany indeks obrazu.

Kolejność obrazów w mapie bitowej jest zazwyczaj kolejnością, w której są rysowane na ekranie, ale można użyć funkcji [SetButtonInfo](#setbuttoninfo) , aby zmienić relację między kolejności obrazu i kolejnością rysowania.

Wszystkie przyciski na pasku narzędzi mają ten sam rozmiar. Wartość domyślna to 24 x 22 piksele zgodnie z *zaleceniami interfejsu systemu Windows dotyczącymi projektowania oprogramowania*. Każde dodatkowe miejsce między wymiarem obrazu a przyciskiem jest używane do tworzenia obramowania wokół obrazu.

Każdy przycisk ma jeden obraz. Różne stany przycisku i style (naciśnięte, w górę, w dół, wyłączone, wyłączone i nieokreślone) są generowane na podstawie tego samego obrazu. Chociaż mapy bitowe mogą być dowolnym kolorem, można uzyskać najlepsze wyniki z obrazów czarno-białych i odcieni szarości.

> [!WARNING]
> `CToolBar`obsługuje mapy bitowe z maksymalnie 16 kolorami. Po załadowaniu obrazu do edytora pasków narzędzi program Visual Studio automatycznie konwertuje obraz do 16-kolorowej mapy bitowej, w razie potrzeby, a następnie wyświetla komunikat ostrzegawczy, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorami (przy użyciu zewnętrznego edytora do edycji obrazu), aplikacja może zachowywać się nieoczekiwanie.

Przyciski paska narzędzi, które są domyślnie imitacj. Jednak przyciski paska narzędzi mogą również naśladować przyciski pola wyboru lub przyciski radiowe. Przyciski pola wyboru mają trzy stany: zaznaczone, wyczyszczone i nieokreślone. Przyciski radiowe mają tylko dwa stany: zaznaczone i wyczyszczone.

Aby ustawić pojedynczy przycisk lub styl separatora bez wskazywania tablicy, wywołaj [](#getbuttonstyle) metodę getbutton, aby pobrać styl, a następnie Wywołaj metodę SetButton zamiast `SetButtons`. [](#setbuttonstyle) `SetButtonStyle`jest najbardziej przydatna, gdy chcesz zmienić styl przycisku w czasie wykonywania.

Aby przypisać tekst, który ma być wyświetlany na przycisku, wywołaj [GetButtonText](#getbuttontext) , aby pobrać tekst, który ma być wyświetlany na przycisku, a następnie Wywołaj [SetButtonText](#setbuttontext) , aby ustawić tekst.

Aby utworzyć przycisk pola wyboru, przypisz do niego styl TBBS_CHECKBOX lub Użyj `CCmdUI` funkcji `SetCheck` składowej obiektu w procedurze obsługi ON_UPDATE_COMMAND_UI. Wywołanie `SetCheck` powoduje zamianę przycisku na przycisk pola wyboru. Przekaż `SetCheck` argument 0 dla opcji niezaznaczone, 1 dla opcji zaznaczone lub 2 dla nieokreślonego.

Aby utworzyć przycisk radiowy, wywołaj funkcję elementu członkowskiego [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) z procedury obsługi ON_UPDATE_COMMAND_UI. Przekazanie `SetRadio` argumentu 0 dla opcji niezaznaczone lub niezerowego dla zaznaczenia. Aby zapewnić wzajemnie wykluczające się zachowanie grupy radiowej, musisz mieć programy obsługi ON_UPDATE_COMMAND_UI dla wszystkich przycisków w grupie.

Aby uzyskać więcej informacji na `CToolBar`temat korzystania z programu, zobacz artykuł [implementacja paska narzędzi MFC](../../mfc/mfc-toolbar-implementation.md) i [Uwaga techniczna 31: Paski](../../mfc/tn031-control-bars.md)sterowania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="commandtoindex"></a>CToolBar:: CommandToIndex

Ta funkcja członkowska zwraca indeks pierwszego przycisku paska narzędzi, rozpoczynając od pozycji 0, której identyfikator polecenia jest zgodny `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
Identyfikator polecenia przycisku paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Indeks przycisku lub-1, jeśli żaden przycisk nie ma danego identyfikatora polecenia.

##  <a name="create"></a>CToolBar:: Create

Ta funkcja członkowska tworzy pasek narzędzi systemu Windows (okno podrzędne) i kojarzy go `CToolBar` z obiektem.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym paska narzędzi.

*dwStyle*<br/>
Styl paska narzędzi. Obsługiwane są dodatkowe style paska narzędzi:

- CBRS_TOP pasek sterowania znajduje się u góry okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się u dołu okna ramki.

- Po zmianie rozmiaru elementu nadrzędnego CBRS_NOALIGN pasek sterowania nie jest zmieniany.

- Na pasku sterowania CBRS_TOOLTIPS są wyświetlane etykietki narzędzi.

- CBRS_SIZE_DYNAMIC pasek sterowania jest dynamiczny.

- Pasek sterowania CBRS_SIZE_FIXED został rozwiązany.

- CBRS_FLOATING pasek sterowania jest przestawny.

- Pasek stanu CBRS_FLYBY wyświetla informacje o przycisku.

- CBRS_HIDE_INPLACE pasek sterowania nie jest widoczny dla użytkownika.

*nID*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>CToolBar:: CreateEx

Wywołaj tę funkcję, aby utworzyć pasek narzędzi systemu Windows (okno podrzędne) i skojarzyć go `CToolBar` z obiektem.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym paska narzędzi.

*dwCtrlStyle*<br/>
Dodatkowe style tworzenia osadzonego obiektu [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) . Domyślnie ta wartość jest ustawiona na TBSTYLE_FLAT. Aby uzyskać pełną listę stylów paska narzędzi, zobacz *dwStyle*.

*dwStyle*<br/>
Styl paska narzędzi. Aby uzyskać listę odpowiednich stylów, zobacz [kontrolki paska narzędzi i style przycisków](/windows/win32/Controls/toolbar-control-and-button-styles) w Windows SDK.

*rcBorders*<br/>
Obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który definiuje szerokości obramowania okna paska narzędzi. Te obramowania są domyślnie ustawione na 0, 0, 0, 0, co powoduje wyświetlenie okna paska narzędzi bez obramowania.

*nID*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

Użyj `CreateEx`zamiast [tworzenia](#create), gdy pewne style muszą być obecne podczas tworzenia osadzonej kontrolki paska narzędzi. Na przykład ustaw *dwCtrlStyle* na TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT, aby utworzyć pasek narzędzi przypominający paski narzędzi programu Internet Explorer 4.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>CToolBar:: CToolBar

Ta funkcja członkowska konstruuje `CToolBar` obiekt i ustawia rozmiary domyślne.

```
CToolBar();
```

### <a name="remarks"></a>Uwagi

Wywołaj funkcję [Utwórz](#create) element członkowski, aby utworzyć okno paska narzędzi.

##  <a name="getbuttoninfo"></a>CToolBar:: GetButtonInfo

Ta funkcja członkowska Pobiera identyfikator kontrolki, styl i indeks obrazu przycisku paska narzędzi lub separatora w lokalizacji określonej przez *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku paska narzędzi lub separatora, którego informacje mają zostać pobrane.

*nID*<br/>
Odwołanie do typu UINT, który jest ustawiony na identyfikator polecenia przycisku.

*nStyle*<br/>
Odwołanie do typu UINT, który jest ustawiony na styl przycisku.

*iImage*<br/>
Odwołanie do liczby całkowitej, która jest ustawiona na indeks obrazu przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

Te wartości są przypisywane do zmiennych, do których odwołuje się *NID*, *nStyle*i *IImage*. Indeks obrazu to pozycja obrazu w mapie bitowej, która zawiera obrazy dla wszystkich przycisków paska narzędzi. Pierwszy obraz znajduje się na pozycji 0.

Jeśli *nIndex* określa separator, *IImage* jest ustawiona na Szerokość separatora (w pikselach).

##  <a name="getbuttonstyle"></a>CToolBar:: getbutton

Wywołaj tę funkcję elementu członkowskiego, aby pobrać styl przycisku lub separatora na pasku narzędzi.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku paska narzędzi lub stylu separatora, który ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Styl przycisku lub separatora określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl przycisku określa, jak pojawia się przycisk i jak reaguje na dane wejściowe użytkownika. Zobacz [](#setbuttonstyle) setbuttonname, aby poznać przykłady stylów przycisków.

##  <a name="getbuttontext"></a>CToolBar:: GetButtonText

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tekst wyświetlany na przycisku.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks tekstu do pobrania.

*rString*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który będzie zawierać tekst do pobrania.

### <a name="return-value"></a>Wartość zwracana

`CString` Obiekt zawierający tekst przycisku.

### <a name="remarks"></a>Uwagi

Druga forma tej funkcji składowej wypełnia `CString` obiekt ciągiem tekstu.

##  <a name="getitemid"></a>CToolBar:: GetItemID

Ta funkcja członkowska zwraca identyfikator polecenia przycisku lub separatora określonego przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu, którego identyfikator ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia przycisku lub separatora określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Separatory zwracają ID_SEPARATOR.

##  <a name="getitemrect"></a>CToolBar:: GetItemRect

Ta funkcja członkowska wypełnia `RECT` strukturę, której adres jest zawarty w *lpRect* ze współrzędnymi przycisku lub separatora określonego przez *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu (przycisk lub separator), którego współrzędne prostokąta mają zostać pobrane.

*lpRect*<br/>
Adres struktury [Rect](/windows/win32/api/windef/ns-windef-rect) , który będzie zawierać współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są w pikselach względem lewego górnego rogu paska narzędzi.

Użyj `GetItemRect` , aby uzyskać współrzędne separatora, który ma zostać zamieniony na pole kombi lub inną kontrolkę.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CToolBar::](#setsizes)SetSizes.

##  <a name="gettoolbarctrl"></a>CToolBar:: GetToolBarCtrl

Ta funkcja członkowska umożliwia bezpośredni dostęp do zasadniczej kontroli wspólnej.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CToolBarCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Użyj `GetToolBarCtrl` , aby skorzystać z funkcji typowej kontrolki paska narzędzi systemu Windows i skorzystać z [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pomocy technicznej w celu dostosowania paska narzędzi.

Aby uzyskać więcej informacji na temat używania formantów wspólnych, zobacz [kontrolki](../../mfc/controls-mfc.md) artykułu i [typowe kontrolki](/windows/win32/Controls/common-controls-intro) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>CToolBar:: LoadBitmap

Wywołaj tę funkcję elementu członkowskiego, aby załadować `lpszResourceName` mapę `nIDResource`bitową określoną przez lub.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik na nazwę zasobu mapy bitowej, która ma zostać załadowana.

*nIDResource*<br/>
Identyfikator zasobu mapy bitowej do załadowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa powinna zawierać jeden obraz dla każdego przycisku paska narzędzi. Jeśli obrazy nie mają rozmiaru standardowego (16 pikseli o szerokości i 15 pikseli), wywołaj metodę SetSizes, aby ustawić rozmiary przycisków i ich obrazy. [](#setsizes)

> [!WARNING]
> `CToolBar`obsługuje mapy bitowe z maksymalnie 16 kolorami. Po załadowaniu obrazu do edytora pasków narzędzi program Visual Studio automatycznie konwertuje obraz do 16-kolorowej mapy bitowej, w razie potrzeby, a następnie wyświetla komunikat ostrzegawczy, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorami (przy użyciu zewnętrznego edytora do edycji obrazu), aplikacja może zachowywać się nieoczekiwanie.

##  <a name="loadtoolbar"></a>CToolBar:: LoadToolBar

Wywołaj tę funkcję elementu członkowskiego, aby załadować pasek narzędzi określony przez *lpszResourceName* lub *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik na nazwę zasobu paska narzędzi, który ma zostać załadowany.

*nIDResource*<br/>
Identyfikator zasobu paska narzędzi do załadowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zobacz [Edytor paska narzędzi](../../windows/toolbar-editor.md) w programie, aby uzyskać więcej informacji na temat tworzenia zasobu paska narzędzi.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CToolBar:: CreateEx](#createex).

##  <a name="setbitmap"></a>CToolBar:: setmap

Wywołaj tę funkcję elementu członkowskiego, aby ustawić obraz mapy bitowej dla paska narzędzi.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Uchwyt obrazu mapy bitowej, który jest skojarzony z paskiem narzędzi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład, wywołaj `SetBitmap` , aby zmienić obraz mapy bitowej, gdy użytkownik wykona akcję w dokumencie, który zmienia akcję przycisku.

##  <a name="setbuttoninfo"></a>CToolBar:: SetButtonInfo

Wywołaj tę funkcję elementu członkowskiego, aby ustawić identyfikator polecenia, styl i numer obrazu przycisku.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) przycisku lub separatora, dla którego ma zostać ustawiona informacja.

*nID*<br/>
Wartość, dla której ustawiono identyfikator polecenia przycisku.

*nStyle*<br/>
Nowy styl przycisku. Obsługiwane są następujące style przycisków:

- TBBS_BUTTON — standardowy przycisk (domyślnie)

- Separator TBBS_SEPARATOR

- Przycisk pola wyboru TBBS_CHECKBOX

- TBBS_GROUP oznacza początek grupy przycisków

- TBBS_CHECKGROUP oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN tworzy przycisk listy rozwijanej.

- TBBS_AUTOSIZE szerokość przycisku zostanie obliczona na podstawie tekstu przycisku, a nie rozmiaru obrazu.

- TBBS_NOPREFIX tekst przycisku nie będzie skojarzony z nim prefiks akceleratora.

*iImage*<br/>
Nowy indeks obrazu przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

W przypadku separatorów, które mają styl TBBS_SEPARATOR, ta funkcja ustawia szerokość separatora (w pikselach) na wartość przechowywaną w *IImage*.

> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu parametru *nStyle* ; Jednak ze względu na to, że Stany przycisków są kontrolowane przez program obsługi [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , `SetButtonInfo` każdy stan ustawiony przy użyciu zostanie utracony podczas następnego bezczynności przetwarzania. Zobacz, [jak aktualizować obiekty interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski](../../mfc/tn031-control-bars.md) sterowania, aby uzyskać więcej informacji.

Aby uzyskać informacje o obrazach i przyciskach mapy bitowej, zobacz Omówienie [CToolBar](../../mfc/reference/ctoolbar-class.md) i [CToolBar:: LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>CToolBar:: SetButtons

Ta funkcja członkowska ustawia identyfikator polecenia każdego przycisku paska narzędzi na wartość określoną przez odpowiedni element tablicy *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Wskaźnik do tablicy identyfikatorów poleceń. Może mieć wartość NULL, aby przydzielić puste przyciski.

*nIDCount*<br/>
Liczba elementów w tablicy wskazywanych przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli element tablicy ma wartość ID_SEPARATOR, separator jest tworzony w odpowiedniej pozycji paska narzędzi. Ta funkcja ustawia również styl każdego przycisku na TBBS_BUTTON oraz każdy styl separatora na TBBS_SEPARATOR i przypisuje indeks obrazu do każdego przycisku. Indeks obrazu określa pozycję obrazu przycisku w mapie bitowej.

Nie trzeba uwzględniać separatorów w mapie bitowej, ponieważ ta funkcja nie przypisuje indeksów obrazu dla separatorów. Jeśli na pasku narzędzi znajdują się przyciski z położeniami 0, 1 i 3 i separator na pozycji 2, obrazy na pozycjach 0, 1 i 2 w mapie bitowej są przypisane do przycisków odpowiednio do pozycji 0, 1 i 3.

Jeśli *lpIDArray* ma wartość null, ta funkcja przydziela miejsce dla liczby elementów określonych przez *nIDCount*. Użyj [SetButtonInfo](#setbuttoninfo) , aby ustawić atrybuty każdego elementu.

##  <a name="setbuttonstyle"></a>CToolBar:: SetButton

Wywołaj tę funkcję elementu członkowskiego, aby ustawić styl przycisku lub separatora lub grupy przycisków.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku lub separatora, którego informacje mają zostać ustawione.

*nStyle*<br/>
Styl przycisku. Obsługiwane są następujące style przycisków:

- TBBS_BUTTON — standardowy przycisk (domyślnie)

- Separator TBBS_SEPARATOR

- Przycisk pola wyboru TBBS_CHECKBOX

- TBBS_GROUP oznacza początek grupy przycisków

- TBBS_CHECKGROUP oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN tworzy przycisk listy rozwijanej

- TBBS_AUTOSIZE szerokość przycisku zostanie obliczona na podstawie tekstu przycisku, a nie rozmiaru obrazu.

- TBBS_NOPREFIX tekst przycisku nie będzie skojarzony z nim prefiks akceleratora

### <a name="remarks"></a>Uwagi

Styl przycisku określa, jak pojawia się przycisk i jak reaguje na dane wejściowe użytkownika.

Przed wywołaniem `SetButtonStyle`należy wywołać funkcję elementu członkowskiego getbutton, aby pobrać styl przycisku lub separatora. [](#getbuttonstyle)

> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu parametru *nStyle* ; Jednak ze względu na to, że Stany przycisków są kontrolowane przez program obsługi [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , `SetButtonStyle` każdy stan ustawiony przy użyciu zostanie utracony podczas następnego bezczynności przetwarzania. Zobacz, [jak aktualizować obiekty interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski](../../mfc/tn031-control-bars.md) sterowania, aby uzyskać więcej informacji.

##  <a name="setbuttontext"></a>CToolBar:: SetButtonText

Wywołaj tę funkcję, aby ustawić tekst na przycisku.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku, którego tekst ma zostać ustawiony.

*lpszText*<br/>
Wskazuje tekst, który ma zostać ustawiony na przycisku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CToolBar:: GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>CToolBar:: setheight

Ta funkcja członkowska Ustawia wysokość paska narzędzi na wartość (w pikselach) określoną w *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyHeight*<br/>
Wysokość (w pikselach) paska narzędzi.

### <a name="remarks"></a>Uwagi

Po wywołaniu [](#setsizes)metody SetSizes Użyj tej funkcji elementu członkowskiego, aby zastąpić standardową wysokość paska narzędzi. Jeśli wysokość jest za mała, przyciski są przycinane u dołu.

Jeśli ta funkcja nie jest wywoływana, struktura używa rozmiaru przycisku, aby określić wysokość paska narzędzi.

##  <a name="setsizes"></a>CToolBar:: SetSizes

Wywołaj tę funkcję elementu członkowskiego, aby ustawić przyciski paska narzędzi na rozmiar (w pikselach) określonych w *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*sizeButton*<br/>
Rozmiar w pikselach każdego przycisku.

*sizeImage*<br/>
Rozmiar w pikselach każdego obrazu.

### <a name="remarks"></a>Uwagi

Parametr *sizeImage* musi zawierać rozmiar (w pikselach) obrazów na mapie bitowej paska narzędzi. Wymiary w *sizeButton* muszą być wystarczające do przechowywania obrazu oraz 7 pikseli o dodatkowe szerokości i 6 pikseli. Ta funkcja ustawia również wysokość paska narzędzi, aby pasowała do przycisków.

Wywołaj tę funkcję elementu członkowskiego tylko dla pasków narzędzi, które nie przestrzegają *wytycznych dotyczących interfejsu systemu Windows dla* zaleceń dotyczących projektowania oprogramowania dla przycisków i rozmiarów obrazów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład CTRLBARS MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład DLGCBR32 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład DOCKTOOL MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
