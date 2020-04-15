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
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372176"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Klasa CMFCToolBarDateTimeCtrl

Przycisk paska narzędzi zawierający kontrolkę selektora daty i godziny.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Konstruuje `CMFCToolBarDateTimeCtrl` obiekt.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania. (Zastępuje [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Zastępuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Zarezerwowane do użytku w przyszłości.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopiuje tekst z przycisku paska narzędzi do menu.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Zwraca wskaźnik do kontrolki selektora daty i godziny.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Pobiera uchwyt okna, który jest skojarzony z przyciskiem paska narzędzi. (Zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Pobiera wybrany czas z kontrolki selektora daty i godziny i umieszcza go w określonej struktury [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Zwraca wybrany czas z przycisku sterowania selektorem czasu, który ma określony identyfikator polecenia.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku jest wyświetlane, gdy użytkownik wybierze przycisk. (Zastępuje [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza komunikat [WM_COMMAND.](/windows/win32/menurc/wm-command) (Zastępuje [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez strukturę, gdy przycisk jest dodawany do **dostosowywania** okna dialogowego. (Zastępuje [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Wywoływana przez strukturę, aby obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Zastępuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Zastępuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Wywoływane przez strukturę, gdy użytkownik kliknie formant. (Zastępuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR. (Zastępuje [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Wywoływane przez strukturę, aby narysować przycisk przy użyciu określonych stylów i opcji. (Zastępuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Wywoływane przez strukturę, aby narysować przycisk w okienku **Polecenia** okna dialogowego **Dostosowywanie.** (Zastępuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsZmienił](#onglobalfontschanged)|Wywoływana przez platformę po zmianie czcionki globalnej. (Zastępuje [CMFCToolBarButton::OnGlobalFontsZmieniem).)](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Wywoływane przez strukturę, gdy przesuwa się nadrzędny pasek narzędzi. (Zastępuje [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Wywoływane przez strukturę, gdy przycisk staje się widoczne lub niewidoczne. (Zastępuje [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Wywoływana przez platformę, gdy nadrzędny pasek narzędzi zmienia swój rozmiar lub położenie, a ta zmiana powoduje, że przycisk zmienia rozmiar. (Zastępuje [cmfctoolbarbutton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia. (Zastępuje [przycisk CMFCToolBarButton::OnUpdateToolTip.)](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum (Zastępuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Ustawia styl przycisku paska narzędzi. (Zastępuje [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Ustawia godzinę i datę w formancie selektora czasu.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Ustawia godzinę i datę we wszystkich wystąpieniach formantu selektora czasu, które mają określony identyfikator polecenia.|

## <a name="remarks"></a>Uwagi

Na przykład, jak używać kontrolki selektora daty i godziny, zobacz ToolbarDateTimePicker przykładowy projekt. Aby uzyskać informacje dotyczące dodawania przycisków sterowania do pasków narzędzi, zobacz [Instruktaż: Umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie zezwala użytkownikowi na rozciąganie przycisku paska narzędzi podczas dostosowywania. Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), umożliwiając użytkownikowi rozciągnąć przycisk paska narzędzi daty i godziny podczas dostosowywania.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Tworzy i inicjuje [obiekt CMFCToolBarDateTimeCtrl.](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Identyfikator sterowania.

*Iimage*<br/>
[w] Indeks obrazu w obiekcie paska `CMFCToolBarImages` narzędzi.

*Dwstyle*<br/>
[w] Styl `CMFCToolBarDateTimeCtrlImpl` okna, które jest tworzone, gdy użytkownik kliknie przycisk.

*iWidth ( iWidth )*<br/>
[w] Szerokość formantu w pikselach.

### <a name="remarks"></a>Uwagi

Ten obiekt jest inicjowany do daty i godziny systemowej. Styl okna obiektu `CMFCToolBarDateTimeCtrlImpl` wewnętrznego zawiera parametr *dwStyle* oraz style WS_CHILD i WS_VISIBLE. Nie można zmienić `CMFCToolBarDateTimeCtrl::SetStyle`tych stylów za pomocą programu . Służy `SetStyle` do zmiany stylu `CMFCToolBarDateTimeCtrl` formantu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarDateTimeCtrl` skonstruować obiekt klasy. Ten fragment kodu jest częścią [przykładu selektora dat na pasku narzędzi toolbaru](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Odwołanie do przycisku źródłowego, z którego mają być kopiowane.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być `CMFCToolBarDateTimeCtrl`typu .

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

Kopiuje tekst z przycisku paska narzędzi do menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[w] Odwołanie do przycisku menu docelowego.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) przez załadowanie zasobu ciągu skojarzonego z identyfikatorem polecenia formantu. Aby uzyskać więcej informacji na temat zasobów ciągów, zobacz [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku do pobrania.

### <a name="return-value"></a>Wartość zwracana

Pierwszy `CMFCToolBarDateTimeCtrl` obiekt w aplikacji, który ma określony identyfikator polecenia `CMFCToolBarDateTimeCtrl` lub NULL, jeśli żadne obiekty nie mają określonego identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta udostępniona metoda narzędzia jest używana przez metody takie jak [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) i [CMFCToolBarDateTimeCtrl::GetTimeAll,](#gettimeall) aby ustawić lub uzyskać godzinę i datę wszystkich wystąpień formantu selektora czasu, które mają określony identyfikator polecenia.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Zwraca wskaźnik do kontrolki selektora daty i godziny.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do daty i kontrolki selektora czasu; lub NULL, jeśli formant nie istnieje.

### <a name="remarks"></a>Uwagi

Klasa `CMFCToolBarDateTimeCtrl` inicjuje `m_pWndDateTime` element członkowski `CMFCToolBarDateTimeCtrl` danych podczas wstawiania obiektu do paska narzędzi.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

Pobiera uchwyt okna, który jest skojarzony z przyciskiem paska narzędzi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna skojarzony z przyciskiem paska narzędzi daty i godziny.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody.

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime

Pobiera wybrany czas od skojarzonej kontrolki selektora daty i godziny i umieszcza ją w określonej strukturze [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest (czas)*<br/>
[na zewnątrz] W pierwszym przeciążeniu [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który otrzyma informacje o czasie systemowym. W drugim przeciążeniu [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który otrzyma informacje o czasie systemowym.

*pTimeDest (Identyfikator czasu)*<br/>
[na zewnątrz] Wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) aby otrzymać informacje o czasie systemowym. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

W pierwszym przeciążeniu, nonzero, jeśli czas jest pomyślnie zapisany do [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu; w przeciwnym razie 0. W drugim i trzecim przeciążenia, zwracana wartość jest DWORD, który jest równy element członkowski dwFlag, który został ustawiony w [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) struktury.

### <a name="remarks"></a>Uwagi

Metoda ustawia [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) struktury elementów członkowskich dwFlags, aby wskazać, czy selektor daty i godziny jest ustawiona na datę i godzinę. Jeśli wartość jest równa GDT_NONE, formant jest `no date` ustawiony na stan i używa stylu DTS_SHOWNONE. Jeśli zwrócona wartość jest równa GDT_VALID, czas systemowy jest pomyślnie przechowywany w lokalizacji docelowej.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Zwraca czas wybrany przez użytkownika z przycisku sterującego selektora czasu, który ma określony identyfikator polecenia.

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

*Uicmd*<br/>
[w] Określa identyfikator polecenia przycisku paska narzędzi.

*timeDest (czas)*<br/>
[na zewnątrz] W pierwszym przeciążeniu [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który otrzyma informacje o czasie systemowym. W drugim przeciążeniu [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który otrzyma informacje o czasie systemowym.

*pTimeDest (Identyfikator czasu)*<br/>
[na zewnątrz] Wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) aby otrzymać informacje o czasie systemowym. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

Jeśli struktura nie może znaleźć przycisku paska narzędzi, który pasuje do polecenia ID *uiCmd,* zwracana wartość wynosi zero w pierwszym przeciążeniu i GDT_NONE w innych przeciążeniach. Jeśli zostanie znaleziony przycisk paska narzędzi, zwracana wartość jest taka sama jak wartość zwracana z wywołania do [CMFCToolBarDateTimeCtrl::GetTime](#gettime) na tym przycisku. Zwracana wartość zero lub GDT_NONE może wystąpić po znalezieniu przycisku, co `GetTime` oznacza, że wywołanie nie zwróciło prawidłowej daty z innego powodu.

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje przycisk paska narzędzi, który ma określony identyfikator polecenia i wywołuje [METODĘ CMFCToolBarDateTimeCtrl::GetTime](#gettime) na tym przycisku.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Określa, czy obramowanie przycisku jest wyświetlane, gdy użytkownik wybierze przycisk.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk wyświetla obramowanie po wybraniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość niezerową, jeśli formant jest widoczny.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Określa, czy przycisk przetwarza komunikat [WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*Kod iNotifyCode*<br/>
[w] Komunikat powiadomienia skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk przetwarza komunikat WM_COMMAND lub FALSE, aby wskazać, że wiadomość powinna być obsługiwana przez nadrzędny pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy ma zamiar wysłać wiadomość [WM_COMMAND](/windows/win32/menurc/wm-command) do okna nadrzędnego.

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [powiadomienia DTN_DATETIMECHANGE.](/windows/win32/Controls/dtn-datetimechange) Aktualizuje wewnętrzny stan czasu i aktualizuje `CMFCToolBarDateTimeCtrl` właściwość czasu wszystkich obiektów o tym samym identyfikatorze polecenia.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Wywoływane przez strukturę, gdy przycisk jest dodawany do **dostosowywania** okna dialogowego.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), kopiując właściwości z pierwszej daty i kontroli czasu w dowolnym pasku narzędzi, który ma ten sam identyfikator polecenia jako ten obiekt. Ta metoda nic nie robi, jeśli żaden pasek narzędzi nie ma kontrolki daty i godziny, która ma ten sam identyfikator polecenia co ten obiekt.

Aby uzyskać więcej informacji na temat okna dialogowego **Dostosowywanie,** zobacz [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Nowe okno nadrzędne.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd) `CMFCToolBarDateTimeCtrlImpl` ) przez odtworzenie obiektu wewnętrznego.

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick

Wywoływane przez strukturę, gdy użytkownik kliknie formant.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Nieużywane.

*bDelay (własówce)*<br/>
[w] Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), zwracając wartość `CMFCToolBarDateTimeCtrlImpl` niezerową, jeśli obiekt wewnętrzny jest widoczny.

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*nCtlColor ( nCtlColor )*<br/>
[w] Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Dojście do pędzla globalnego, który służy do malowania tła przycisku.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), ustawiając tekst i kolory tła kontekstu urządzenia pod warunkiem, do tekstu globalnego i kolorów tła, odpowiednio.

Aby uzyskać więcej informacji na temat opcji globalnych dostępnych dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsZmienił

Wywoływana przez platformę po zmianie czcionki globalnej.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) zmieniając czcionkę formantu do czcionki globalnej.

Aby uzyskać więcej informacji na temat opcji globalnych dostępnych dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

Wywoływane przez strukturę, gdy przesuwa się nadrzędny pasek narzędzi.

```
virtual void OnMove();
```

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) `CMFCToolBarDateTimeCtrlImpl` przez aktualizowanie pozycji obiektu wewnętrznego.

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

Wywoływane przez strukturę, gdy przycisk staje się widoczne lub niewidoczne.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość PRAWDA, przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) przez wyświetlenie przycisku, jeśli *bShow* jest TRUE. W przeciwnym razie ta metoda ukrywa przycisk.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize

Wywoływana przez platformę, gdy nadrzędny pasek narzędzi zmienia swój rozmiar lub położenie, a ta zmiana powoduje, że przycisk zmienia rozmiar.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*rozmiar iSize*<br/>
[w] Nowa szerokość przycisku w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) aktualizując rozmiar i położenie obiektu wewnętrznego. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Okno nadrzędne.

*iButtonIndex*<br/>
[w] Indeks od zera przycisku w kolekcji przycisków nadrzędnych.

*wndToolTip*<br/>
[w] Formant, który wyświetla tekst etykietki narzędzia.

*Str*<br/>
[na zewnątrz] Obiekt, `CString` który odbiera zaktualizowany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) przez wyświetlanie tekstu etykietki narzędzia, który jest skojarzony z przyciskiem. Jeśli przycisk nie jest zadokowany poziomo, ta metoda nic nie robi i zwraca FALSE.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime

Ustawia godzinę i datę w formancie selektora czasu.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*czasNowy*<br/>
[w] W pierwszej wersji odwołanie do [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który zawiera czas, do którego formant zostanie ustawiony. W drugiej wersji wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który zawiera czas, do którego formant zostanie ustawiony.

*pCzasNowy*<br/>
[w] Wskaźnik do [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury, która zawiera czas, do którego formant zostanie ustawiony.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia godzinę w formancie selektora daty i godziny, wywołując [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Ustawia godzinę i datę we wszystkich wystąpieniach formantu selektora czasu, które mają określony identyfikator polecenia.

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

*Uicmd*<br/>
[w] Określa identyfikator polecenia przycisku paska narzędzi.

*czasNowy*<br/>
[w] W pierwszej wersji [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który zawiera czas, do którego formant zostanie ustawiony. W drugiej wersji wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który zawiera czas, do którego formant zostanie ustawiony.

*pCzasNowy*<br/>
[w] Wskaźnik do [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury, która zawiera czas, do którego formant zostanie ustawiony.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyszukuje przycisk paska narzędzi o określonym identyfikatorze polecenia i ustawia godzinę w formancie selektora daty i godziny, wywołując [CMFCToolBarDateTimeCtrl::SetTime](#settime).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
