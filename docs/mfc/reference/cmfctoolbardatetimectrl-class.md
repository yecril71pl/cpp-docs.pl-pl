---
title: Klasa CMFCToolBarDateTimeCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504760"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Klasa CMFCToolBarDateTimeCtrl

Przycisk paska narzędzi, który zawiera kontrolkę selektora daty i godziny.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Konstruuje `CMFCToolBarDateTimeCtrl` obiekt.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania. (Przesłania [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Zarezerwowane do użytku w przyszłości.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopiuje tekst z przycisku paska narzędzi do menu.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Zwraca wskaźnik do kontrolki selektora daty i godziny.|
|[CMFCToolBarDateTimeCtrl:: GetHwnd](#gethwnd)|Pobiera uchwyt okna skojarzony z przyciskiem paska narzędzi. (Przesłania [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)).|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Pobiera wybrany czas z kontrolki selektora daty i godziny i umieszcza ją w określonej strukturze [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Zwraca wybrany czas z przycisku kontrolki selektora czasu, który ma określony identyfikator polecenia.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku ma być wyświetlane, gdy użytkownik wybierze przycisk. (Przesłania [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) . (Przesłania [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do okna dialogowego **Dostosowywanie** . (Przesłania [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Wywoływane przez platformę, by obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Przesłania [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi. (Przesłania [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie formant. (Przesłania [CMFCToolBarButton:: onkliknięciu](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR. (Przesłania [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Wywoływane przez platformę, by narysować przycisk przy użyciu określonych stylów i opcji. (Przesłania [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Wywoływane przez platformę, aby narysować przycisk w okienku **polecenia** okna dialogowego **Dostosowywanie** . (Przesłania [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy zmieniono czcionkę globalną. (Przesłania [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl:: OnMove](#onmove)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi jest przenoszony. (Zastępuje [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)).|
|[CMFCToolBarDateTimeCtrl:: OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk zostanie widoczny lub niewidoczny. (Przesłania [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi zmienia jego rozmiar lub położenie, a ta zmiana powoduje zmianę rozmiaru przycisku. (Przesłania [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia. (Przesłania [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum (Przesłania [CMFCToolBarButton:: serializacji](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Ustawia styl przycisku paska narzędzi. (Zastępuje [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)).|
|[CMFCToolBarDateTimeCtrl:: SetTime](#settime)|Ustawia godzinę i datę w kontrolce selektora czasu.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Ustawia datę i godzinę we wszystkich wystąpieniach formantu selektora czasu, który ma określony identyfikator polecenia.|

## <a name="remarks"></a>Uwagi

Przykład używania kontrolki selektora daty i godziny można znaleźć w przykładowym projekcie ToolbarDateTimePicker. Aby uzyskać informacje na temat dodawania przycisków kontroli do pasków narzędzi [, zobacz Przewodnik: Umieszczanie formantów na](../../mfc/walkthrough-putting-controls-on-toolbars.md)paskach narzędzi.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbardatetimectrl. h

##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie platforma nie zezwala użytkownikowi na rozciąganie przycisku paska narzędzi podczas dostosowywania. Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) przez umożliwienie użytkownikowi rozciągnięcia przycisku paska narzędzi daty i godziny podczas dostosowywania.

##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Tworzy i inicjuje obiekt [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) .

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
podczas Identyfikator formantu.

*iImage*<br/>
podczas Indeks obrazu w `CMFCToolBarImages` obiekcie paska narzędzi.

*dwStyle*<br/>
podczas Styl `CMFCToolBarDateTimeCtrlImpl` okna tworzonego po kliknięciu przycisku przez użytkownika.

*iWidth*<br/>
podczas Szerokość formantu (w pikselach).

### <a name="remarks"></a>Uwagi

Ten obiekt jest zainicjowany do daty i godziny systemowej. Styl okna obiektu wewnętrznego `CMFCToolBarDateTimeCtrlImpl` zawiera parametr *dwStyle* oraz style WS_CHILD i WS_VISIBLE. Nie można zmienić tych stylów przy użyciu `CMFCToolBarDateTimeCtrl::SetStyle`. Użyj `SetStyle` , aby zmienić styl `CMFCToolBarDateTimeCtrl` formantu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCToolBarDateTimeCtrl` klasy. Ten fragment kodu jest częścią [przykładu selektora daty i godziny na pasku narzędzi](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Odwołanie do przycisku źródła, z którego ma zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skopiować kolejny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być typu `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

Kopiuje tekst z przycisku paska narzędzi do menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
podczas Odwołanie do przycisku menu docelowego.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) przez załadowanie zasobu ciągu, który jest SKOJARZONY z identyfikatorem polecenia formantu. Aby uzyskać więcej informacji na temat zasobów ciągów, zobacz [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia do pobrania.

### <a name="return-value"></a>Wartość zwracana

Pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia, lub wartość null, jeśli żadne `CMFCToolBarDateTimeCtrl` obiekty nie mają określonego identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda udostępniona narzędzia jest używana przez metody, takie jak [CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall) i [CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall) , aby ustawić lub pobrać godzinę i datę wszystkich wystąpień kontrolki selektora czasu, które mają określony identyfikator polecenia.

##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Zwraca wskaźnik do kontrolki selektora daty i godziny.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Kontrolka selektora daty i godziny; lub wartość NULL, jeśli formant nie istnieje.

### <a name="remarks"></a>Uwagi

Klasa Inicjuje element członkowski danych podczas wstawiania obiektudopaskanarzędzi.`CMFCToolBarDateTimeCtrl` `m_pWndDateTime` `CMFCToolBarDateTimeCtrl`

##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl:: GetHwnd

Pobiera uchwyt okna skojarzony z przyciskiem paska narzędzi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna, który jest skojarzony z przyciskiem paska narzędzi daty i godziny.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania metodę [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) .

##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl:: GetTime

Pobiera wybrany czas od skojarzonej kontrolki selektora daty i godziny i umieszcza ją w określonej strukturze [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
określoną W pierwszym przeciążeniu obiekt [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który otrzyma informacje o czasie systemowym. W drugim przeciążeniu obiekt [CTime](../../atl-mfc-shared/reference/ctime-class.md) , który otrzyma informacje o czasie systemowym.

*pTimeDest*<br/>
określoną Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , aby uzyskać informacje o czasie systemowym. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

W pierwszym przeciążeniu, niezerowe, jeśli czas został pomyślnie zapisany w obiekcie [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ; w przeciwnym razie 0. W drugim i trzecim przeciążeniu wartość zwracana jest wartością typu DWORD, która jest równa dwFlag elementu członkowskiego, który został ustawiony w strukturze [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) .

### <a name="remarks"></a>Uwagi

Metoda ustawia element członkowski struktury [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) flagiDW, aby wskazać, czy selektor daty i godziny jest ustawiony na datę i godzinę. Jeśli wartość jest równa GDT_NONE, kontrolka jest ustawiana na `no date` stan i używa stylu DTS_SHOWNONE. Jeśli wartość zwracana jest równa GDT_VALID, czas systemowy zostanie pomyślnie zapisany w lokalizacji docelowej.

##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Zwraca godzinę wybraną przez użytkownika z przycisku kontrolki selektora czasu, który ma określony identyfikator polecenia.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Określa identyfikator polecenia paska narzędzi.

*timeDest*<br/>
określoną W pierwszym przeciążeniu obiekt [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który otrzyma informacje o czasie systemowym. W drugim przeciążeniu obiekt [CTime](../../atl-mfc-shared/reference/ctime-class.md) , który otrzyma informacje o czasie systemowym.

*pTimeDest*<br/>
określoną Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , aby uzyskać informacje o czasie systemowym. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Jeśli struktura nie może znaleźć przycisku paska narzędzi, który jest zgodny z IDENTYFIKATORem polecenia *uiCmd*, wartość zwracana wynosi zero w pierwszym przeciążeniu i GDT_NONE w innych przeciążeniach. Jeśli przycisk paska narzędzi zostanie znaleziony, wartość zwracana jest taka sama jak wartość zwracana z wywołania [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) na tym przycisku. Wartość zwracana zero lub GDT_NONE może wystąpić po znalezieniu przycisku, co oznacza, że wywołanie `GetTime` nie zwróciło prawidłowej daty z innego powodu.

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje przycisk paska narzędzi, który ma określony identyfikator polecenia i wywołuje metodę [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) na tym przycisku.

##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Określa, czy obramowanie przycisku ma być wyświetlane, gdy użytkownik wybierze przycisk.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przycisk wyświetla jego obramowanie po zaznaczeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość różną od zera, Jeśli kontrolka jest widoczna.

##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Określa, czy przycisk przetwarza komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
podczas Komunikat z powiadomieniem, który jest skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk przetwarza komunikat WM_COMMAND lub wartość FALSE, aby wskazać, że komunikat powinien być obsługiwany przez nadrzędny pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy zostanie wysłana wiadomość [WM_COMMAND](/windows/win32/menurc/wm-command) do okna nadrzędnego.

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie powiadomienia [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange) . Aktualizuje stan czasu wewnętrznego i aktualizuje właściwość czasu dla wszystkich `CMFCToolBarDateTimeCtrl` obiektów z tym samym identyfikatorem polecenia.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Wywoływane przez platformę, gdy przycisk zostanie dodany do okna dialogowego **Dostosowywanie** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej, [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), kopiując właściwości z pierwszej kontrolki Data i godzina na dowolnym pasku narzędzi, który ma ten sam identyfikator polecenia co ten obiekt. Ta metoda nie robi nic, jeśli żaden pasek narzędzi nie ma kontrolki daty i godziny, która ma ten sam identyfikator polecenia co ten obiekt.

Aby uzyskać więcej informacji na temat **dostosowywania** okna dialogowego, zobacz [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Nowe okno nadrzędne.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) przez ponowne utworzenie obiektu wewnętrznego `CMFCToolBarDateTimeCtrlImpl` .

##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl:: onkliknięcia

Wywoływane przez platformę, gdy użytkownik kliknie formant.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Przestrzeń.

*bDelay*<br/>
podczas Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej, [CMFCToolBarButton:: onkliknięcia](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), zwracając wartość różną od zera, jeśli obiekt wewnętrzny `CMFCToolBarDateTimeCtrlImpl` jest widoczny.

##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*nCtlColor*<br/>
podczas Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do globalnego pędzla, który jest wykorzystywany przez platformę do rysowania tła przycisku.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej, [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), ustawiając kolory tekstu i tła podanego kontekstu urządzenia odpowiednio do globalnego koloru tekstu i tła.

Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Wywoływane przez platformę, gdy zmieniono czcionkę globalną.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionkę kontrolki na czcionkę globalną.

Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl:: OnMove

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi jest przenoszony.

```
virtual void OnMove();
```

### <a name="remarks"></a>Uwagi

Ta metoda przesłania domyślną implementację klasy ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) przez zaktualizowanie pozycji obiektu wewnętrznego `CMFCToolBarDateTimeCtrlImpl` .

##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl:: OnShow

Wywoływane przez platformę, gdy przycisk zostanie widoczny lub niewidoczny.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
podczas Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość TRUE, przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)), wyświetlając przycisk, jeśli *bShow* ma wartość true. W przeciwnym razie ta metoda ukrywa przycisk.

##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl:: OnSize

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi zmienia jego rozmiar lub położenie, a ta zmiana powoduje zmianę rozmiaru przycisku.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
podczas Nowa szerokość przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda przesłania domyślną implementację klasy ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) przez zaktualizowanie rozmiaru i położenia obiektu wewnętrznego `CMFCToolBarDateTimeCtrlImpl` .

##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Okno nadrzędne.

*iButtonIndex*<br/>
podczas Indeks (liczony od zera) przycisku w kolekcji przycisków nadrzędnych.

*wndToolTip*<br/>
podczas Kontrolka wyświetlająca tekst etykietki narzędzia.

*str*<br/>
określoną `CString` Obiekt, który odbiera zaktualizowany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) wyświetlając tekst etykietki narzędzia, która jest skojarzona z przyciskiem. Jeśli przycisk nie jest zadokowany w poziomie, ta metoda nie wykonuje żadnych operacji i zwraca wartość FALSE.

##  <a name="settime"></a>CMFCToolBarDateTimeCtrl:: SetTime

Ustawia godzinę i datę w kontrolce selektora czasu.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
podczas W pierwszej wersji odwołanie do obiektu [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który zawiera godzinę, do której zostanie ustawiony formant. W drugiej wersji wskaźnik do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) , który zawiera godzinę, do której zostanie ustawiony formant.

*pTimeNew*<br/>
podczas Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , który zawiera czas, do którego zostanie ustawiona kontrolka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia godzinę w kontrolce selektora daty i godziny przez wywołanie [Korzystanie CDateTimeCtrl:: SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Ustawia datę i godzinę we wszystkich wystąpieniach formantu selektora czasu, który ma określony identyfikator polecenia.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Określa identyfikator polecenia paska narzędzi.

*timeNew*<br/>
podczas W pierwszej wersji obiekt [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który zawiera godzinę, do której zostanie ustawiony formant. W drugiej wersji wskaźnik do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) , który zawiera godzinę, do której zostanie ustawiony formant.

*pTimeNew*<br/>
podczas Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , który zawiera czas, do którego zostanie ustawiona kontrolka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyszukuje przycisk paska narzędzi o określonym IDENTYFIKATORze polecenia i ustawia godzinę w kontrolce selektora daty i godziny przez wywołanie [CMFCToolBarDateTimeCtrl:: SetTime](#settime).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
