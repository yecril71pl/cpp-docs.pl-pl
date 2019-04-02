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
ms.openlocfilehash: aa49ebed2d48d9818c2d39ae4894d8caf1fbbf81
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773141"
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
|[CToolBar::CToolBar](#ctoolbar)|Konstruuje `CToolBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Zwraca indeks przycisk za pomocą identyfikatora polecenia.|
|[CToolBar::Create](#create)|Tworzy pasek narzędzi Windows i dołącza je do `CToolBar` obiektu.|
|[CToolBar::CreateEx](#createex)|Tworzy `CToolBar` obiektu o dodatkowe style osadzonego `CToolBarCtrl` obiektu.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Pobiera identyfikator, stylu i numer obrazu przycisku.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Pobiera styl przycisku.|
|[CToolBar::GetButtonText](#getbuttontext)|Pobiera tekst, który będzie wyświetlany na przycisku.|
|[CToolBar::GetItemID](#getitemid)|Zwraca identyfikator polecenia przycisku lub separator pod danym indeksem.|
|[CToolBar::GetItemRect](#getitemrect)|Pobiera prostokątny obszar wyświetlania elementu pod danym indeksem.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.|
|[CToolBar::LoadBitmap](#loadbitmap)|Ładuje mapę bitową zawierająca obrazy mapy bitowej przycisku.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Ładuje zasób paska narzędzi, utworzony za pomocą edytora zasobów.|
|[CToolBar::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Określa identyfikator, stylu i numer obrazu przycisku.|
|[CToolBar::SetButtons](#setbuttons)|Ustawia przycisku — style i indeks obrazy przycisków w mapie bitowej.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku.|
|[CToolBar::SetButtonText](#setbuttontext)|Ustawia tekst, który będzie wyświetlany na przycisku.|
|[CToolBar::SetHeight](#setheight)|Określa wysokość paska narzędzi.|
|[CToolBar::SetSizes](#setsizes)|Ustawia wielkości przycisków i ich map bitowych.|

## <a name="remarks"></a>Uwagi

Przyciski może zachowywać się jak przyciski, pola wyboru lub przycisków radiowych. `CToolBar` obiekty są zazwyczaj osadzone elementy członkowskie obiektów okien ramowych pochodzących od klasy [CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), funkcją składową nowe 4.0 MFC pozwala na korzystanie z zalet obsługę Windows formantu typowego pasków narzędzi i dodatkowe funkcje. `CToolBar` Funkcje Członkowskie zapewniają większość funkcji wspólnych formantów Windows; Jednak jeśli wywołasz `GetToolBarCtrl`, zapewnić paski narzędzi jeszcze więcej właściwości pasków narzędzi Windows 95/98. Gdy wywołujesz `GetToolBarCtrl`, to zostanie zwrócona odwołanie do `CToolBarCtrl` obiektu. Zobacz [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) Aby uzyskać więcej informacji na temat projektowania pasków narzędzi za pomocą wspólnych formantów Windows. Aby uzyskać więcej ogólnych informacji o wspólnych formantów, zobacz [wspólnych formantów](/windows/desktop/Controls/common-controls-intro) w zestawie Windows SDK.

Visual C++ udostępnia dwie metody tworzenia paska narzędzi. Aby utworzyć zasób paska narzędzi, za pomocą edytora zasobów, wykonaj następujące kroki:

1. Utwórz zasób paska narzędzi.

1. Konstruowania `CToolBar` obiektu.

1. Wywołaj [Utwórz](#create) (lub [CreateEx](#createex)) funkcji, aby utworzyć pasek narzędzi Windows i dołączyć go do `CToolBar` obiektu.

1. Wywołaj [LoadToolBar](#loadtoolbar) można załadować zasobu paska narzędzi.

W przeciwnym razie wykonaj następujące kroki:

1. Konstruowania `CToolBar` obiektu.

1. Wywołaj [Utwórz](#create) (lub [CreateEx](#createex)) funkcji, aby utworzyć pasek narzędzi Windows i dołączyć go do `CToolBar` obiektu.

1. Wywołaj [loadbitmap —](#loadbitmap) można załadować mapy bitowej, który zawiera obrazy przycisków paska narzędzi.

1. Wywołaj [setbuttons —](#setbuttons) Ustaw styl przycisku i skojarzyć każdy przycisk za pomocą obrazu w mapie bitowej.

Wszystkie obrazy przycisk na pasku narzędzi są pobierane z jednego mapy bitowej, który musi zawierać jeden obraz dla każdego przycisku. Wszystkie obrazy muszą mieć taki sam rozmiar; Wartość domyślna to 16 pikseli szerokości i wysokości 15 pikseli. Obrazy muszą dawać się obok siebie w mapie bitowej.

`SetButtons` Funkcja przyjmuje wskaźnik do tablicy kontroli identyfikatorów i liczba całkowita określająca liczbę elementów w tablicy. Funkcja Ustawia identyfikator każdego przycisku na wartość odpowiedni element tablicy i przypisuje każdego przycisku Indeks obrazu, który określa pozycję obrazu na przycisku w mapie bitowej. Jeśli do elementu tablicy ma wartość ID_SEPARATOR, indeks obrazu, nie zostanie przypisany.

Kolejność w mapie bitowej jest zwykle kolejność, w którym są rysowane na ekranie, ale można użyć [SetButtonInfo](#setbuttoninfo) funkcję, aby zmienić relacji między kolejność obrazów i kolejności rysowania.

Wszystkie przyciski na pasku narzędzi mają taki sam rozmiar. Wartość domyślna to 24 x 22 piksele, zgodnie z *Windows interfejsu wytyczne dotyczące projektowania oprogramowania*. Dodatkowe miejsce między wymiarami obrazu i przycisk będzie stosowany do tworzenia obramowania wokół obrazu.

Każdy przycisk ma jeden obraz. Przycisk różnych stanów i style (po naciśnięciu, Strzałka w dół, wyłączone, wyłączone w dół i nieokreślone) są generowane na podstawie tego jednego obrazu. Mimo że mapy bitowe, może być dowolny kolor, można osiągnąć najlepsze rezultaty, przy użyciu obrazów czarno odcieni szarości.

> [!WARNING]
> `CToolBar` obsługuje mapy bitowe z maksymalnie 16 kolorów. Podczas ładowania obrazu do paska narzędzi edytora, Visual Studio automatycznie konwertuje obraz mapy bitowej 16 kolorów, jeśli to konieczne i wyświetla ostrzeżenie, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (przy użyciu zewnętrznego edytora do edycji obraz), aplikacja może zachowywać się nieoczekiwanie.

Przyciski paska narzędzi naśladowania przycisków domyślnie. Jednak przycisków paska narzędzi można także naśladowania przyciski pola wyboru lub przycisków radiowych. Przyciski pole wyboru ma trzy stany: checked, wyczyszczone i nieokreślony. Przyciski radiowe przyjmować tylko dwa stany: zaznaczone, a wyczyszczone.

Aby ustawić indywidualne przycisku lub styl separatora bez wskazuje do tablicy, należy wywołać [GetButtonStyle](#getbuttonstyle) do pobrania styl, a następnie wywołaj [SetButtonStyle](#setbuttonstyle) zamiast `SetButtons`. `SetButtonStyle` Aby zmienić styl przycisku w czasie wykonywania, jest najbardziej przydatne.

Aby przypisać tekst wyświetlany na przycisku, należy wywołać [GetButtonText](#getbuttontext) pobrać tekst wyświetlany na przycisku, a następnie wywołaj [SetButtonText](#setbuttontext) można ustawić tekst.

Tworzy przycisk pola wyboru, należy ją przypisać stylu TBBS_CHECKBOX lub użyć `CCmdUI` obiektu `SetCheck` funkcja elementu członkowskiego w obsłudze ON_UPDATE_COMMAND_UI. Wywoływanie `SetCheck` przycisk jest przekształcany przycisk pola wyboru. Przekaż `SetCheck` argument 0 nie jest zaznaczone, 1 dla zaznaczony lub 2 dla nieokreślony.

Aby utworzyć przycisk radiowy, wywołaj [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu [setradio —](../../mfc/reference/ccmdui-class.md#setradio) funkcji składowej z nieprawidłowego ON_UPDATE_COMMAND_UI. Przekaż `SetRadio` argument 0 unchecked lub wartość różną od zera, aby sprawdzić. Aby zapewnić zachowanie wzajemnie wykluczających się grupą radio, musi mieć ON_UPDATE_COMMAND_UI obsługi wszystkie przyciski w grupie.

Aby uzyskać więcej informacji na temat korzystania z `CToolBar`, zapoznaj się z artykułem [MFC — implementacja paska narzędzi](../../mfc/mfc-toolbar-implementation.md) i [techniczne 31 Uwaga: Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

Ta funkcja elementu członkowskiego zwraca indeks pierwszego przycisku paska narzędzi, zaczynając od pozycji 0, o identyfikatorze polecenia zgodnym `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
Identyfikator polecenia przycisku paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Indeks przycisk lub -1, gdy przycisk nie ma identyfikatora polecenia.

##  <a name="create"></a>  CToolBar::Create

Ta funkcja elementu członkowskiego Windows paska narzędzi (okno podrzędne) tworzy i kojarzy ją z `CToolBar` obiektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym w pasku narzędzi.

*dwStyle*<br/>
Styl paska narzędzi. Style dodatkowych narzędzi, obsługiwane są następujące:

- Pasek sterowania CBRS_TOP to u góry okna ramki.

- Pasek sterowania CBRS_BOTTOM jest w dolnej części okna ramki.

- Pasek sterowania CBRS_NOALIGN nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.

- Pasek sterowania CBRS_TOOLTIPS Wyświetla etykietek narzędzi.

- Pasek sterowania CBRS_SIZE_DYNAMIC jest dynamiczny.

- Pasek sterowania CBRS_SIZE_FIXED jest stała.

- Pasek sterowania CBRS_FLOATING jest liczb zmiennoprzecinkowych.

- Pasek stanu CBRS_FLYBY Wyświetla informacje o przycisku.

- Pasek sterowania CBRS_HIDE_INPLACE są niewidoczne dla użytkownika.

*nID*<br/>
Identyfikator paska narzędzi okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

Wywołaj tę funkcję, aby utworzyć pasek narzędzi Windows (okno podrzędne) i powiąż ją z `CToolBar` obiektu.

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
Wskaźnik do okna, które jest elementem nadrzędnym w pasku narzędzi.

*dwCtrlStyle*<br/>
Dodatkowe style Tworzenie osadzonego [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) obiektu. Domyślnie ta wartość jest równa TBSTYLE_FLAT. Aby uzyskać pełną listę Style paska narzędzi, zobacz *dwStyle*.

*dwStyle*<br/>
Styl paska narzędzi. Zobacz [formantu paska narzędzi oraz style przycisku](/windows/desktop/Controls/toolbar-control-and-button-styles) w zestawie Windows SDK dla listy odpowiednie style.

*rcBorders*<br/>
A [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który definiuje szerokość obramowania okna narzędzi. Te obramowania są domyślnie 0,0,0,0, powodując w oknie narzędzi z brak obramowania.

*nID*<br/>
Identyfikator paska narzędzi okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

Użyj `CreateEx`, zamiast [Utwórz](#create), gdy określone style musi być obecny podczas tworzenia formantu paska narzędzi osadzony. Na przykład ustawić *dwCtrlStyle* do TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT, aby utworzyć pasek narzędzi, który przypomina pasków narzędzi programu Internet Explorer 4.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

Ta funkcja elementu członkowskiego tworzy `CToolBar` obiektu i ustawia domyślne rozmiary.

```
CToolBar();
```

### <a name="remarks"></a>Uwagi

Wywołaj [Utwórz](#create) funkcja elementu członkowskiego, można utworzyć okna narzędzi.

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

Ta funkcja elementu członkowskiego pobiera identyfikator kontrolki, stylu i indeks obrazu na przycisku paska narzędzi lub separatorem w lokalizacji określonej przez *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku paska narzędzi lub separatora, o których informacje są do pobrania.

*nID*<br/>
Odwołanie do UINT, który jest ustawiony na identyfikator polecenia przycisku.

*nStyle*<br/>
Odwołanie do UINT, który jest ustawiony na styl przycisku.

*iImage*<br/>
Odwołanie do liczba całkowita, która jest ustawiona na indeks obrazu na przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

Te wartości są przypisane do zmienne przywoływane przez *nID*, *nStyle*, i *iImage*. Indeks obrazu jest położenia obrazu w obrębie mapy bitowej, który zawiera obrazy dla przycisków paska narzędzi. Pierwszy obraz znajduje się na pozycji 0.

Jeśli *nIndex* Określa separator *iImage* jest ustawiona na separator szerokość w pikselach.

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

Wywołaj tę funkcję elementu członkowskiego, aby pobrać styl przycisku lub menu na pasku narzędzi.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks styl przycisku lub separator narzędzi do pobrania.

### <a name="return-value"></a>Wartość zwracana

Styl przycisku lub separator określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl przycisku określa sposób wyświetlania przycisku i sposobu odpowiedzi na dane wejściowe użytkownika. Zobacz [SetButtonStyle](#setbuttonstyle) przykłady style przycisku.

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

Wywołaj tę funkcję elementu członkowskiego, aby przywrócić tekst, który jest wyświetlany na przycisku.

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
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu, który będzie zawierać tekst, który ma zostać pobrane.

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt zawierający tekst przycisku.

### <a name="remarks"></a>Uwagi

Druga forma ten element członkowski funkcji wypełnienia `CString` obiektu z ciąg tekstu.

##  <a name="getitemid"></a>  CToolBar::GetItemID

Ta funkcja elementu członkowskiego zwraca identyfikator polecenia przycisku lub separator określony przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu, którego identyfikator jest do pobrania.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia przycisku lub separator określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Separatory Zwróć ID_SEPARATOR.

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

Ta funkcja elementu członkowskiego wypełnia `RECT` strukturę, której adres znajduje się w *lprect —* współrzędnych przycisku lub separator określony przez *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu (przycisk lub separatorem), którego współrzędne prostokąt, które mają być pobierane.

*lpRect*<br/>
Adres [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) strukturę, która będzie zawierać współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są podawane w pikselach względem lewego górnego rogu paska narzędzi.

Użyj `GetItemRect` by uzyskać współrzędne separator, który ma zostać zamieniony pola kombi lub inny formant.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CToolBarCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Użyj `GetToolBarCtrl` wykorzystać funkcje formantu typowego paska narzędzi Windows i korzystać z pomocy technicznej [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) zapewnia dostosowywanie paska narzędzi.

Aby uzyskać więcej informacji o używaniu wspólnych formantów, zobacz artykuł [kontrolki](../../mfc/controls-mfc.md) i [wspólnych formantów](/windows/desktop/Controls/common-controls-intro) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

Wywołaj tę funkcję elementu członkowskiego, aby załadować mapy bitowej, określony przez `lpszResourceName` lub `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik do nazwy zasobu mapy bitowej do załadowania.

*nIDResource*<br/>
Identyfikator zasobu mapy bitowej do załadowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa może zawierać jeden obraz dla przycisku paska narzędzi. Jeśli obrazy nie są standardowy rozmiar 16 pikseli szerokości i 15 pikseli, wywołanie [SetSizes](#setsizes) można ustawić rozmiar przycisku i obrazów.

> [!WARNING]
> `CToolBar` obsługuje mapy bitowe z maksymalnie 16 kolorów. Podczas ładowania obrazu do paska narzędzi edytora, Visual Studio automatycznie konwertuje obraz mapy bitowej 16 kolorów, jeśli to konieczne i wyświetla ostrzeżenie, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (przy użyciu zewnętrznego edytora do edycji obraz), aplikacja może zachowywać się nieoczekiwanie.

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

Wywołaj tę funkcję elementu członkowskiego, aby załadować narzędzi określony przez *lpszResourceName* lub *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik do nazwy zasobu paska narzędzi, aby go załadować.

*nIDResource*<br/>
Identyfikator zasobu paska narzędzi do załadowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zobacz [Edytor paska narzędzi](../../windows/toolbar-editor.md) w Aby uzyskać więcej informacji na temat tworzenia zasobu paska narzędzi.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::CreateEx](#createex).

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

Wywołaj tę funkcję elementu członkowskiego, aby ustawić obraz mapy bitowej dla paska narzędzi.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Dojście do obrazu mapy bitowej, który jest skojarzony z paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład wywołać `SetBitmap` zmienić obraz mapy bitowej, po użytkownik wykonuje akcję na dokument, który zmienia działanie przycisku.

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

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
Liczony od zera indeks przycisku lub separatora, dla którego ma można ustawić informacji.

*nID*<br/>
Wartość, do której jest ustawiony identyfikator polecenia przycisku.

*nStyle*<br/>
Nowy styl przycisku. Obsługiwane są następujące style przycisku:

- Przycisk TBBS_BUTTON standardowe (domyślne)

- TBBS_SEPARATOR Separator

- Przycisk pola wyboru automatycznie TBBS_CHECKBOX

- TBBS_GROUP oznacza początek grupy przycisków

- TBBS_CHECKGROUP oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN tworzy przycisk listy rozwijanej.

- TBBS_AUTOSIZE szerokość przycisku będzie obliczany na podstawie tekstu przycisku, nie na rozmiar obrazu.

- TBBS_NOPREFIX tekst przycisku nie będą mieć prefiks akceleratora skojarzonych z nim.

*iImage*<br/>
Nowy indeks obrazu na przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

Separatorami, których styl TBBS_SEPARATOR, funkcja ta Ustawia szerokość separatora w pikselach na wartość przechowywaną w *iImage*.

> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu *nStyle* parametru; Jednakże, ponieważ Stany przycisku są kontrolowane przez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obsługi żadnego stanu można ustawić za pomocą `SetButtonInfo` zostaną utracone podczas następnego przetwarzania bezczynności. Zobacz [jak aktualizowanie obiektów interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski sterowania](../../mfc/tn031-control-bars.md) Aby uzyskać więcej informacji.

Aby uzyskać informacje na temat obrazy bitmapowe i przyciski, zobacz [CToolBar](../../mfc/reference/ctoolbar-class.md) Przegląd i [CToolBar::LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>  CToolBar::SetButtons

Ta funkcja elementu członkowskiego Ustawia identyfikator polecenia przycisku paska narzędzi na wartość określoną przez odpowiedni element tablicy *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Wskaźnik do tablicy identyfikatorów poleceń. Może być NULL można przydzielić pusty przycisków.

*nIDCount*<br/>
Liczba elementów w tablicy, wskazywana przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli element tablicy zawiera wartość ID_SEPARATOR, separator jest tworzony w odpowiednim miejscu na pasku narzędzi. Ta funkcja także ustawia styl każdy przycisk TBBS_BUTTON i styl każdego separatora TBBS_SEPARATOR i przypisuje indeks obrazu do każdego przycisku. Indeks obrazu Określa pozycję obrazu przycisku w mapie bitowej.

Potrzebujesz konta separatorami w mapie bitowej, ponieważ ta funkcja nie ma przypisanego indeksów obrazu dla separatorów. Jeśli pasek narzędzi z przyciskami na pozycji 0, 1 i 3 oraz separator na pozycji 2, obrazy na pozycji 0, 1 i 2 w sieci mapy bitowej są przypisane do przycisków na pozycji 0, 1 i 3, odpowiednio.

Jeśli *lpIDArray* ma wartość NULL, ta funkcja przydziela miejsce dla liczby elementów określonych przez *nIDCount*. Użyj [SetButtonInfo](#setbuttoninfo) ustawić atrybuty każdego elementu.

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

Wywołaj tę funkcję elementu członkowskiego, aby ustawić styl przycisku lub separatora lub do grupy przycisków.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku lub separatora, o których informacje jest ustawienie.

*nStyle*<br/>
Styl przycisku. Obsługiwane są następujące style przycisku:

- Przycisk TBBS_BUTTON standardowe (domyślne)

- TBBS_SEPARATOR Separator

- Przycisk pola wyboru automatycznie TBBS_CHECKBOX

- TBBS_GROUP oznacza początek grupy przycisków

- TBBS_CHECKGROUP oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN tworzy przycisk listy rozwijanej

- TBBS_AUTOSIZE szerokość przycisku będzie obliczany na podstawie tekstu przycisku, nie na rozmiar obrazu

- TBBS_NOPREFIX tekst przycisku nie będzie miał prefiks akceleratora skojarzonych z nim

### <a name="remarks"></a>Uwagi

Styl przycisku określa sposób wyświetlania przycisku i sposobu odpowiedzi na dane wejściowe użytkownika.

Przed wywołaniem `SetButtonStyle`, wywołaj [GetButtonStyle](#getbuttonstyle) funkcję elementu członkowskiego, aby pobrać styl przycisku lub separatora.

> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu *nStyle* parametru; Jednakże, ponieważ Stany przycisku są kontrolowane przez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obsługi żadnego stanu można ustawić za pomocą `SetButtonStyle` zostaną utracone podczas następnego przetwarzania bezczynności. Zobacz [jak aktualizowanie obiektów interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski sterowania](../../mfc/tn031-control-bars.md) Aby uzyskać więcej informacji.

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

Wywołaj tę funkcję, aby ustawić tekst na przycisku.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks przycisku, którego tekst jest do ustawienia.

*lpszText*<br/>
Wskazuje tekst, który ma być ustawiony na przycisku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>  CToolBar::SetHeight

Ta funkcja elementu członkowskiego Ustawia wysokość paska narzędzi na wartość w pikselach, określone w *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyHeight*<br/>
Wysokość w pikselach, na pasku narzędzi.

### <a name="remarks"></a>Uwagi

Po wywołaniu [SetSizes](#setsizes), użyj tej funkcji elementu członkowskiego, aby przesłonić wysokość standardowego paska narzędzi. Gdy wysokość jest zbyt mały, przyciski zostaną przycięte u dołu.

Jeśli ta funkcja nie jest wywoływana, struktura używa rozmiar przycisku, aby określić wysokość paska narzędzi.

##  <a name="setsizes"></a>  CToolBar::SetSizes

Wywołaj tę funkcję elementu członkowskiego, aby ustawić przycisków paska narzędzi na rozmiar w pikselach, określone w *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*sizeButton*<br/>
Rozmiar w pikselach każdego przycisku.

*sizeImage*<br/>
Rozmiar każdego obrazu w pikselach.

### <a name="remarks"></a>Uwagi

*SizeImage* parametr musi zawierać rozmiar w pikselach, obrazy w pasku narzędzi mapy bitowej. Wymiary w *sizeButton* musi być wystarczająca do przechowywania obrazu, a także dodatkowe szerokość 7 pikseli i 6 pikseli dodatkowe wysokość. Ta funkcja spowoduje także ustawienie wysokość paska narzędzi do przycisków.

Wywołaj tę funkcję elementu członkowskiego tylko dla pasków narzędzi, które nie podlegają *Windows interfejsu wytyczne dotyczące projektowania oprogramowania* zaleceń dotyczących rozmiarów przycisku i obrazów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
