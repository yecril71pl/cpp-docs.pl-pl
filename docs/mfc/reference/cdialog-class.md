---
title: Klasa CDialog
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: cad762f426012d9d1931b96d54d8a53c9bab465d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375645"
---
# <a name="cdialog-class"></a>Klasa CDialog

Klasa podstawowa używana do wyświetlania okien dialogowych na ekranie.

## <a name="syntax"></a>Składnia

```
class CDialog : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Konstruuje `CDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::Utwórz](#create)|Inicjuje `CDialog` obiekt. Tworzy niemodowe okno dialogowe i `CDialog` dołącza je do obiektu.|
|[CDialog::CreateIndirect](#createindirect)|Tworzy niemodowe okno dialogowe z szablonu okna dialogowego w pamięci (nie opartej na zasobach).|
|[CDialog::DoModal](#domodal)|Wywołuje modalne okno dialogowe i zwraca po zakończeniu.|
|[CDialog::KoniecDialog](#enddialog)|Zamyka okno dialogowe modalne.|
|[CDialog::GetDefID](#getdefid)|Pobiera identyfikator domyślnego formantu przycisku dla okna dialogowego.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Przenosi fokus do określonego formantu okna dialogowego w oknie dialogowym.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Tworzy modalne okno dialogowe z szablonu okna dialogowego w pamięci (nie opartej na zasobach). Parametry są przechowywane, `DoModal` dopóki funkcja jest wywoływana.|
|[CDialog::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Przenosi fokus do następnego formantu okna dialogowego w oknie dialogowym.|
|[CDialog::OnInitDialog](#oninitdialog)|Zastąrpnąć, aby rozszerzyć inicjowanie okna dialogowego.|
|[CDialog::OnSetFont](#onsetfont)|Zastąd, aby określić czcionkę, którą ma używać kontrolka okna dialogowego podczas losowania tekstu.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Przenosi fokus do poprzedniego formantu okna dialogowego w oknie dialogowym.|
|[CDialog::SetDefID](#setdefid)|Zmienia domyślną kontrolkę przycisku dla okna dialogowego na określony przycisk.|
|[CDialog::SetHelpID](#sethelpid)|Ustawia kontekstowy identyfikator pomocy dla okna dialogowego.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Zastąp, aby wykonać akcję przycisku Anuluj lub KLAWISZ ESC. Wartość domyślna zamyka okno `DoModal` dialogowe i zwraca identyfikator IDCANCEL.|
|[CDialog::OnOK](#onok)|Zastąp, aby wykonać akcję przycisku OK w oknie dialogowym modalnego. Wartość domyślna zamyka okno `DoModal` dialogowe i zwraca identyfikator IDOK.|

## <a name="remarks"></a>Uwagi

Okna dialogowe są dwa typy: modalne i modless. Modalne okno dialogowe musi zostać zamknięte przez użytkownika przed kontynuowaniem aplikacji. Niemodowe okno dialogowe umożliwia użytkownikowi wyświetlenie okna dialogowego i powrót do innego zadania bez anulowania lub usunięcia okna dialogowego.

Obiekt `CDialog` jest kombinacją szablonu okna `CDialog`dialogowego i klasy pochodnej. Użyj edytora dialogów, aby utworzyć szablon okna dialogowego i przechowywać go w `CDialog`zasobie, a następnie użyć kreatora Dodaj klasę, aby utworzyć klasę pochodną .

Okno dialogowe, podobnie jak każde inne okno, odbiera wiadomości z systemu Windows. W oknie dialogowym użytkownik jest szczególnie zainteresowany obsługą komunikatów powiadomień z formantów okna dialogowego, ponieważ w ten sposób użytkownik wchodzi w interakcję z okólszym. Użyj [Kreatora klas,](mfc-class-wizard.md) aby wybrać wiadomości, które chcesz obsłużyć, a dodasz odpowiednie wpisy mapy wiadomości i funkcje członkowskie obsługi wiadomości do klasy. Wystarczy napisać kod specyficzne dla aplikacji w funkcji elementu członkowskiego programu obsługi.

Jeśli wolisz, zawsze możesz ręcznie pisać wpisy mapy wiadomości i funkcje członkowskie.

We wszystkich, z wyjątkiem najbardziej trywialne okno dialogowe, należy dodać zmienne członkowskie do klasy okna dialogowego pochodne do przechowywania danych wprowadzonych w formanty okna dialogowego przez użytkownika lub do wyświetlania danych dla użytkownika. Za pomocą Kreatora dodawania zmiennych można tworzyć zmienne członkowskie i kojarzyć je z formantami. W tym samym czasie można wybrać typ zmiennej i dopuszczalny zakres wartości dla każdej zmiennej. Kreator kodu dodaje zmienne członkowskie do klasy pochodnego okna dialogowego.

Mapa danych jest generowana w celu automatycznego obchodzenia się z wymianą danych między zmiennymi elementów członkowskich a formantami okna dialogowego. Mapa danych zawiera funkcje, które inicjują formanty w oknie dialogowym z odpowiednimi wartościami, pobierają dane i weryfikują dane.

Aby utworzyć modalne okno dialogowe, skonstruuj obiekt na stosie przy `DoModal` użyciu konstruktora dla pochodnej klasy okna dialogowego, a następnie wywołaj, aby utworzyć okno dialogowe i jego formanty. Jeśli chcesz utworzyć niemodowe okno `Create` dialogowe, wywołaj w konstruktorze klasy okna dialogowego.

Można również utworzyć szablon w pamięci przy użyciu struktury danych [DLGTEMPLATE,](/windows/win32/api/winuser/ns-winuser-dlgtemplate) zgodnie z opisem w windows SDK. Po skonstruowaniu `CDialog` obiektu [wywołaj polecenie CreateIndirect,](#createindirect) aby utworzyć niemodalne okno dialogowe, lub wywołaj [initModalIndirect](#initmodalindirect) i [DoModal,](#domodal) aby utworzyć modalne okno dialogowe.

Mapa danych wymiany i sprawdzania poprawności jest zapisywana w `CWnd::DoDataExchange` zastąpieniu, który jest dodawany do nowej klasy okna dialogowego. Zobacz [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) funkcji `CWnd` elementu członkowskiego, aby uzyskać więcej informacji na temat funkcji wymiany i sprawdzania poprawności.

Zarówno programista, jak `DoDataExchange` i framework wywołać pośrednio za pośrednictwem wywołania [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Struktura wywołuje, `UpdateData` gdy użytkownik kliknie przycisk OK, aby zamknąć okno dialogowe modalne. (Dane nie są pobierane po kliknięciu przycisku Anuluj). Domyślna implementacja [OnInitDialog](#oninitdialog) również wywołuje, `UpdateData` aby ustawić wartości początkowe formantów. Zazwyczaj należy zastąpić `OnInitDialog` do dalszego inicjowania formantów. `OnInitDialog`jest wywoływana po utworzeniu wszystkich formantów okna dialogowego i tuż przed wyświetleniem okna dialogowego.

Wywołanie `CWnd::UpdateData` można wywołać w dowolnym momencie podczas wykonywania modalnego lub trybutowego okna dialogowego.

Jeśli programujesz okno dialogowe ręcznie, należy samodzielnie dodać niezbędne zmienne członkowskie do klasy pochodnego okna dialogowego i dodać funkcje członkowskie, aby ustawić lub uzyskać te wartości.

Modalne okno dialogowe zamyka się automatycznie, gdy użytkownik naciśnie przyciski `EndDialog` OK lub Anuluj lub gdy kod wywołuje funkcję elementu członkowskiego.

Podczas implementowania niemodytowego okna dialogowego zawsze należy zastąpić funkcję `OnCancel` elementu członkowskiego i wywołać `DestroyWindow` z wewnątrz niego. Nie nazywaj klasy `CDialog::OnCancel`podstawowej, `EndDialog`ponieważ wywołuje , co sprawi, że okno dialogowe będzie niewidoczne, ale nie zniszczy go. Należy również zastąpić `PostNcDestroy` niemodytowane okna dialogowe, aby usunąć **to**, ponieważ niemodowe okna dialogowe są zwykle przydzielane z **nowym**. Modalne okna dialogowe są zwykle konstruowane `PostNcDestroy` na ramce i nie wymagają czyszczenia.

Aby uzyskać `CDialog`więcej informacji na temat , zobacz [Okna dialogowe](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog

Aby skonstruować modalne okno dialogowe oparte na zasobach, wywołaj albo publiczną formę konstruktora.

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

### <a name="remarks"></a>Uwagi

Jeden formularz konstruktora zapewnia dostęp do zasobu okna dialogowego według nazwy szablonu. Drugi konstruktor zapewnia dostęp według numeru identyfikatora szablonu, zwykle z prefiksem **IDD_** (na przykład IDD_DIALOG1).

Aby skonstruować modalne okno dialogowe z szablonu w pamięci, najpierw wywołaj `InitModalIndirect`bezwamiametryczny, chroniony konstruktor, a następnie wywołanie .

Po skonstruowaniu modalnego okna dialogowego przy za `DoModal`pomocą jednej z powyższych metod wywołaj program .

Aby skonstruować niemodless okna dialogowego, `CDialog` należy użyć chronionej formy konstruktora. Konstruktor jest chroniony, ponieważ należy wyprowadzić własną klasę okna dialogowego, aby zaimplementować niemodne okno dialogowe. Budowa niemodytowego okna dialogowego jest procesem dwuetapowym. Najpierw wywołać konstruktora; następnie wywołaj `Create` funkcję elementu członkowskiego, aby utworzyć `CreateIndirect` okno dialogowe oparte na zasobach, lub wywołanie utworzenia okna dialogowego z szablonu w pamięci.

## <a name="cdialogcreate"></a><a name="create"></a>CDialog::Utwórz

Wywołanie, `Create` aby utworzyć niemodowe okno dialogowe przy użyciu szablonu okna dialogowego z zasobu.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Oba formularze zwracają nonzero, jeśli tworzenie i inicjowanie okna dialogowego zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można umieścić wywołanie `Create` wewnątrz konstruktora lub wywołać go po wywołaniu konstruktora.

Dwie formy `Create` funkcji elementu członkowskiego są dostępne dla dostępu do zasobu szablonu okna dialogowego przy nazwie szablonu lub numerze identyfikatora szablonu (na przykład IDD_DIALOG1).

Dla każdego formularza przekaż wskaźnik do obiektu okna nadrzędnego. Jeśli *pParentWnd* ma wartość NULL, okno dialogowe zostanie utworzone z jego nadrzędnym lub właścicielem okno ustawione na główne okno aplikacji.

Funkcja `Create` elementu członkowskiego zwraca natychmiast po tym, jak utworzy okno dialogowe.

Użyj stylu WS_VISIBLE w szablonie okna dialogowego, jeśli okno dialogowe powinno być wyświetlane podczas tworzenia okna nadrzędnego. W przeciwnym razie `ShowWindow`należy wywołać . Aby uzyskać więcej stylów okna dialogowego i ich aplikacji, zobacz strukturę [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) w windows SDK i [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) w *odwołaniu MFC*.

Użyj `CWnd::DestroyWindow` funkcji, aby zniszczyć okno `Create` dialogowe utworzone przez funkcję.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::CreateIndirect

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć niemodowe okno dialogowe z szablonu okna dialogowego w pamięci.

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpDialogTemplate*<br/>
Wskazuje na pamięć zawierającą szablon okna dialogowego użyty do utworzenia okna dialogowego. Ten szablon ma postać struktury I informacji sterującej [DLGTEMPLATE,](/windows/win32/api/winuser/ns-winuser-dlgtemplate) zgodnie z opisem w panelu Windows SDK.

*pParentWnd*<br/>
Points to the dialog object's parent window object (of type [CWnd](../../mfc/reference/cwnd-class.md)). Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

*lpDialogInit*<br/>
Wskazuje zasób DLGINIT.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej zawierające szablon okna dialogowego. Ten szablon ma postać `DLGTEMPLATE` struktury i danych dla każdego formantu w oknie dialogowym.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli okno dialogowe zostało utworzone i zainicjowane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `CreateIndirect` elementu członkowskiego zwraca natychmiast po tym, jak utworzy okno dialogowe.

Użyj stylu WS_VISIBLE w szablonie okna dialogowego, jeśli okno dialogowe powinno być wyświetlane podczas tworzenia okna nadrzędnego. W przeciwnym razie `ShowWindow` należy wywołać, aby spowodować jego pojawienie się. Aby uzyskać więcej informacji na temat określania innych stylów okna dialogowego w szablonie, zobacz strukturę [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) w programie Windows SDK.

Użyj `CWnd::DestroyWindow` funkcji, aby zniszczyć okno `CreateIndirect` dialogowe utworzone przez funkcję.

Okna dialogowe zawierające formanty ActiveX wymagają dodatkowych informacji podanych w zasobie DLGINIT.

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModal

Wywołanie tej funkcji elementu członkowskiego, aby wywołać modalne okno dialogowe i zwrócić wynik okna dialogowego po zakończeniu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Wartość **int,** która określa wartość parametru *nResult,* który został przekazany do funkcji elementu członkowskiego [CDialog::EndDialog,](#enddialog) która jest używana do zamykania okna dialogowego. Zwracana wartość wynosi -1, jeśli funkcja nie może utworzyć okna dialogowego, lub IDABORT, jeśli wystąpił jakiś inny błąd, w którym to przypadku okno wyjściowe będzie zawierać informacje o błędzie z [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego obsługuje całą interakcję z użytkownikiem, gdy okno dialogowe jest aktywne. To, co sprawia, że modalne okno dialogowe; oznacza to, że użytkownik nie może wchodzić w interakcje z innymi oknami, dopóki okno dialogowe nie zostanie zamknięte.

Jeśli użytkownik kliknie jeden z przycisków w oknie dialogowym, takich jak OK lub Anuluj, funkcja elementu członkowskiego obsługi wiadomości, takich jak [OnOK](#onok) lub [OnCancel,](#oncancel)jest wywoływana w celu zamknięcia okna dialogowego. Domyślna `OnOK` funkcja elementu członkowskiego będzie sprawdzać poprawność i aktualizować dane okna dialogowego `OnCancel` oraz zamykać okno dialogowe z wynikiem IDOK, a domyślna funkcja elementu członkowskiego zamknie okno dialogowe z wynikiem IDCANCEL bez sprawdzania poprawności lub aktualizowania danych okna dialogowego. Można zastąpić te funkcje obsługi wiadomości, aby zmienić ich zachowanie.

> [!NOTE]
> `PreTranslateMessage`jest teraz wywoływana do przetwarzania komunikatów modalnego okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog::KoniecDialog

Wywołanie tej funkcji elementu członkowskiego, aby zakończyć modalne okno dialogowe.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*nWysklij*<br/>
Zawiera wartość zwracaną z okna dialogowego do `DoModal`osoby dzwoniącej programu .

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca *nResult* jako wartość zwracaną `DoModal`. Za pomocą `EndDialog` tej funkcji należy ukończyć przetwarzanie przy każdym utworzeniu modalnego okna dialogowego.

Można wywołać `EndDialog` w dowolnym momencie, nawet w [OnInitDialog](#oninitdialog), w którym to przypadku należy zamknąć okno dialogowe przed jego pokazano lub przed ustawieniem fokusu wejściowego.

`EndDialog`nie zamyka natychmiast okna dialogowego. Zamiast tego ustawia flagę, która kieruje okno dialogowe, aby zamknąć tak szybko, jak bieżący program obsługi wiadomości zwraca.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID

Wywołanie `GetDefID` funkcji elementu członkowskiego, aby uzyskać identyfikator domyślnego formantu przycisku dla okna dialogowego.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość 32-bitowa `DWORD`( ). Jeśli domyślny przycisk pushton ma wartość identyfikatora, słowo wysokiego rzędu zawiera DC_HASDEFID, a słowo niskiego rzędu zawiera wartość identyfikatora. Jeśli domyślny przycisk pushton nie ma wartości identyfikatora, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Zazwyczaj jest to przycisk OK.

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl

Przenosi fokus do określonego formantu w oknie dialogowym.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl (właśc.*<br/>
Identyfikuje okno (formant), który ma otrzymać fokus.

### <a name="remarks"></a>Uwagi

Aby uzyskać wskaźnik do formantu (okno podrzędne), aby przekazać `CWnd::GetDlgItem` jako *pWndCtrl*, wywołać funkcję elementu członkowskiego, który zwraca wskaźnik do obiektu [CWnd.](../../mfc/reference/cwnd-class.md)

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect

Wywołanie tej funkcji elementu członkowskiego, aby zainicjować obiekt modalnego okna dialogowego przy użyciu szablonu okna dialogowego, który można utworzyć w pamięci.

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpDialogTemplate*<br/>
Wskazuje na pamięć zawierającą szablon okna dialogowego użyty do utworzenia okna dialogowego. Ten szablon ma postać struktury I informacji sterującej [DLGTEMPLATE,](/windows/win32/api/winuser/ns-winuser-dlgtemplate) zgodnie z opisem w panelu Windows SDK.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej zawierające szablon okna dialogowego. Ten szablon ma postać `DLGTEMPLATE` struktury i danych dla każdego formantu w oknie dialogowym.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

*lpDialogInit*<br/>
Wskazuje zasób DLGINIT.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt okna dialogowego został pomyślnie utworzony i zainicjowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby utworzyć modalne okno dialogowe pośrednio, najpierw przydzielić globalny blok pamięci i wypełnić go szablonem okna dialogowego. Następnie wywołać `CDialog` pusty konstruktora do konstruowania obiektu okna dialogowego. Następnie wywołanie `InitModalIndirect` do przechowywania dojście do szablonu okna dialogowego w pamięci. Okno dialogowe Systemu Windows jest tworzone i wyświetlane później, gdy wywoływana jest funkcja elementu członkowskiego [DoModal.](#domodal)

Okna dialogowe zawierające formanty ActiveX wymagają dodatkowych informacji podanych w zasobie DLGINIT.

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect

Wywołanie konwertowania jednostek okna dialogowego prostokąta na jednostki ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) który zawiera współrzędne okna dialogowego do przekonwertowania.

### <a name="remarks"></a>Uwagi

Jednostki okna dialogowego są podane w kategoriach bieżącej jednostki bazowej okna dialogowego pochodzącej od średniej szerokości i wysokości znaków w czcionce używanej dla tekstu okna dialogowego. Jedna jednostka pozioma to jedna czwarta jednostki szerokości podstawy okna dialogowego, a jedna jednostka pionowa to jedna ósma jednostki wysokości podstawy okna dialogowego.

Funkcja `GetDialogBaseUnits` Systemu Windows zwraca informacje o rozmiarze czcionki systemowej, ale można określić inną czcionkę dla każdego okna dialogowego, jeśli w pliku definicji zasobów jest używany styl DS_SETFONT. Funkcja `MapDialogRect` Systemu Windows używa odpowiedniej czcionki dla tego okna dialogowego.

Funkcja `MapDialogRect` elementu członkowskiego zastępuje jednostki okna dialogowego w *lpRect* jednostkami ekranu (pikselami), dzięki czemu prostokąt może być użyty do utworzenia okna dialogowego lub umieszczenia formantu w polu.

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl

Przenosi fokus do następnego formantu w oknie dialogowym.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus znajduje się na ostatnim formancie w oknie dialogowym, przechodzi do pierwszego formantu.

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel

Struktura wywołuje tę metodę, gdy użytkownik kliknie **przycisk Anuluj** lub naciśnie klawisz ESC w oknie dialogowym modalnej lub niemodalnej.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby wykonać akcje (takie jak przywracanie starych danych), gdy użytkownik zamknie okno dialogowe, klikając **przycisk Anuluj** lub naciskając klawisz ESC. Domyślnie zamyka modalne okno dialogowe, wywołując [EndDialog](#enddialog) i powodując [DoModal](#domodal) do zwrócenia IDCANCEL.

Jeśli zaimplementujesz przycisk **Anuluj** w niemodytnym oknie dialogowym, należy zastąpić `OnCancel` metodę i [wywołać DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niego. Nie należy wywoływać metody klasy podstawowej, ponieważ wywołuje `EndDialog`ona , co spowoduje, że okno dialogowe będzie niewidoczne, ale nie zniszczy go.

> [!NOTE]
> Nie można zastąpić tej metody podczas `CFileDialog` używania obiektu w programie skompilowanym w systemie Windows XP. Aby uzyskać `CFileDialog`więcej informacji na temat , zobacz [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog

Ta metoda jest wywoływana `WM_INITDIALOG` w odpowiedzi na komunikat.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Określa, czy aplikacja ustawiła fokus wejściowy na jeden z formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość niezerową, system Windows ustawia fokus wejściowy na lokalizację domyślną, pierwszy formant w oknie dialogowym. Aplikacja może zwrócić 0 tylko wtedy, gdy jawnie ustawić fokus wejściowy do jednego z formantów w oknie dialogowym.

### <a name="remarks"></a>Uwagi

System Windows `WM_INITDIALOG` wysyła wiadomość do okna dialogowego podczas [wywołań Tworzenie](#create), [Tworzenieindirect](#createindirect)lub [DoModal,](#domodal) które występują bezpośrednio przed wyświetleniem okna dialogowego.

Zastąpość tę metodę, jeśli chcesz wykonać specjalne przetwarzanie po zainicjowaniu okna dialogowego. W wersji zastąpione najpierw wywołać `OnInitDialog` klasę podstawową, ale zignorować jego wartość zwracaną. Zazwyczaj będzie zwracać `TRUE` z nadpisanej metody.

System Windows `OnInitDialog` wywołuje tę funkcję przy użyciu standardowej globalnej procedury okna dialogowego wspólnej dla wszystkich okien dialogowych biblioteki klas programu Microsoft Foundation. Nie wywołanie tej funkcji za pośrednictwem mapy wiadomości i dlatego nie trzeba wpis mapy wiadomości dla tej metody.

> [!NOTE]
> Nie można zastąpić tej metody podczas `CFileDialog` używania obiektu w programie skompilowanym w systemach operacyjnych Windows Vista lub nowszych. Aby uzyskać więcej `CFileDialog` informacji na temat zmian w systemie Windows Vista i nowszych, zobacz [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

Wywoływana, gdy użytkownik kliknie przycisk **OK** (przycisk z identyfikatorem IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby wykonać akcje po włączeniu przycisku **OK.** Jeśli okno dialogowe zawiera automatyczne sprawdzanie poprawności i wymianę danych, domyślna implementacja tej metody sprawdza poprawność danych okna dialogowego i aktualizuje odpowiednie zmienne w aplikacji.

Jeśli zaimplementujesz przycisk **OK** w niemodless okna `OnOK` dialogowego, należy zastąpić metodę i wywołać [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niego. Nie należy wywoływać metody klasy podstawowej, ponieważ wywołuje [EndDialog,](#enddialog) który sprawia, że okno dialogowe jest niewidoczne, ale nie niszczy go.

> [!NOTE]
> Nie można zastąpić tej metody podczas `CFileDialog` używania obiektu w programie skompilowanym w systemie Windows XP. Aby uzyskać `CFileDialog`więcej informacji na temat , zobacz [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont

Określa czcionkę używaną przez formant okna dialogowego podczas rysowania tekstu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
[w] Określa wskaźnik do czcionki, która będzie używana jako czcionka domyślna dla wszystkich formantów w tym oknie dialogowym.

### <a name="remarks"></a>Uwagi

W oknie dialogowym zostanie użyta określona czcionka jako domyślna dla wszystkich jej formantów.

Edytor okien dialogowych zazwyczaj ustawia czcionkę okna dialogowego jako część zasobu szablonu okna dialogowego.

> [!NOTE]
> Nie można zastąpić tej metody podczas `CFileDialog` używania obiektu w programie skompilowanym w systemach operacyjnych Windows Vista lub nowszych. Aby uzyskać więcej `CFileDialog` informacji na temat zmian w systemie Windows Vista i nowszych, zobacz [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

Ustawia fokus na poprzedni kontrolkę w oknie dialogowym.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus znajduje się przy pierwszym formancie w oknie dialogowym, zostanie przeniesiony do ostatniego formantu w polu.

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID

Zmienia domyślny przycisk sterujący okna dialogowego.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Określa identyfikator formantu przycisku, który stanie się wartością domyślną.

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID

Ustawia kontekstowy identyfikator pomocy dla okna dialogowego.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Określa kontekstowy identyfikator pomocy.

## <a name="see-also"></a>Zobacz też

[Próbka MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
