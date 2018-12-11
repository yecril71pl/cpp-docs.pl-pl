---
title: Cdialog — klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: 9eac0f7efdacc6181d8aaa15398f4d7365c0edd3
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178502"
---
# <a name="cdialog-class"></a>Cdialog — klasa

Klasa podstawowa używana do wyświetlania okien dialogowych na ekranie.

## <a name="syntax"></a>Składnia

```
class CDialog : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Konstruuje `CDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::Create](#create)|Inicjuje `CDialog` obiektu. Tworzy niemodalne okno dialogowe i dołącza je do `CDialog` obiektu.|
|[CDialog::CreateIndirect](#createindirect)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego w pamięci (nie opartego na zasobach).|
|[CDialog::DoModal](#domodal)|Wywołuje modalne okno dialogowe, a następnie zwraca po zakończeniu.|
|[CDialog::EndDialog](#enddialog)|Zamyka okno modalne okno dialogowe.|
|[CDialog::GetDefID](#getdefid)|Pobiera identyfikator formantu mapami domyślny dla okna dialogowego.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Przenosi fokus do formantu okno dialogowe, w oknie dialogowym.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Tworzy modalne okno dialogowe z szablonu okna dialogowego w pamięci (nie opartego na zasobach). Parametry są przechowywane do momentu funkcja `DoModal` jest wywoływana.|
|[CDialog::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Przenosi fokus do następnego formantu okno dialogowe, w oknie dialogowym.|
|[CDialog::OnInitDialog](#oninitdialog)|Należy przesłonić, aby rozszerzyć Inicjowanie okna dialogowego.|
|[CDialog::OnSetFont](#onsetfont)|Należy przesłonić, aby określić czcionki, okno dialogowe formantu jest używana podczas jego rysuje tekst.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Przenosi fokus do poprzedniego okno dialogowe formantu w oknie dialogowym.|
|[CDialog::SetDefID](#setdefid)|Zmienia domyślny formant mapami dla okna dialogowego określony przycisk.|
|[CDialog::SetHelpID](#sethelpid)|Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Należy przesłonić, aby wykonać przycisk anulowania lub działania kluczowych ESC. Domyślnie zamknięcie okna dialogowego i `DoModal` zwraca IDCANCEL.|
|[CDialog::OnOK](#onok)|Przesłonięcie w celu wykonania akcji przycisku OK w modalne okno dialogowe. Domyślnie zamknięcie okna dialogowego i `DoModal` zwraca IDOK.|

## <a name="remarks"></a>Uwagi

Okna dialogowe istnieją dwa typy: modalne i niemodalne. Modalne okno dialogowe muszą być zamknięte przez użytkownika, przed kontynuowaniem aplikacji. Niemodalne okno dialogowe umożliwia użytkownikowi zostanie wyświetlone okno dialogowe i wrócić do innego zadania bez anulowanie i usuwanie okno dialogowe.

A `CDialog` obiektu składa się z szablonu okna dialogowego i `CDialog`-klasy pochodnej. Edytor okien dialogowych sposób tworzenia szablonu okna dialogowego i zapisz go w zasobach, a następnie Utwórz klasę pochodną za pomocą Kreatora dodawania klasy `CDialog`.

Okno dialogowe, podobnie jak inne okno odbiera komunikaty z Windows. W oknie dialogowym interesuje Cię szczególnie obsługi komunikatów powiadomień od formantów w oknie dialogowym, ponieważ jest jak użytkownik wchodzi w interakcję z okna dialogowego. Użyj okna właściwości, aby wybrać wiadomości, które chcesz dojścia i doda wpisy odpowiedniej mapie komunikatów i elementów członkowskich obsługi wiadomości do klasy dla Ciebie. Musisz napisać kod specyficzne dla aplikacji w funkcji elementów członkowskich programu obsługi.

Jeśli wolisz, możesz zawsze napisać wpisy mapy komunikatów i elementów członkowskich ręcznie.

We wszystkich oprócz najbardziej proste okno dialogowe Dodaj zmiennych składowych do klasy pochodnej okien dialogowych do przechowywania danych wprowadzonych w oknie dialogowym formanty przez użytkownika lub, aby wyświetlić dane użytkownika. Dodaj zmienną Kreator służy do tworzenia zmiennych Członkowskich i skojarzyć je z formantami. W tym samym czasie możesz wybrać typ zmiennej, a dopuszczalny zakres wartości dla każdej zmiennej. Kreator kod dodaje zmiennych składowych do klasy pochodnej okien dialogowych.

Mapowanie danych jest generowany automatycznie obsłużyć wymianę danych między zmiennych składowych i formantów w oknie dialogowym. Mapowanie danych udostępnia funkcje, które zainicjować formantów w oknie dialogowym z odpowiednimi wartościami, pobierania danych i sprawdzania poprawności danych.

Aby utworzyć modalne okno dialogowe, utworzenia obiektu na stosie, za pomocą konstruktora dla klasy pochodnej okien dialogowych, a następnie wywołać `DoModal` do utworzenia okna dialogowego i jego środków kontroli. Jeśli chcesz utworzyć niemodalnego okna dialogowego, wywołać `Create` w konstruktorze klasy okien dialogowych.

Można również utworzyć szablon w pamięci, za pomocą [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktury danych, zgodnie z opisem w zestawie Windows SDK. Po konstruowania `CDialog` obiektu, wywołaj [CreateIndirect](#createindirect) do tworzenia niemodalny okno dialogowe lub wywołanie [InitModalIndirect](#initmodalindirect) i [DoModal](#domodal) utworzyć modalne okno dialogowe.

Wymiana i Walidacja mapowania danych są zapisywane w zastąpieniu obiektu `CWnd::DoDataExchange` który został dodany do nowej klasy okien dialogowych. Zobacz [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) funkcji składowej we `CWnd` Aby uzyskać więcej informacji na temat funkcji programu exchange i sprawdzania poprawności.

Wywołanie framework i programistę `DoDataExchange` pośrednio poprzez wywołanie [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Struktura wywołuje `UpdateData` po użytkownik kliknie przycisk OK, aby zamknąć okno modalne okno dialogowe. (Dane nie są pobierane, jeśli kliknięto przycisk Anuluj.) Domyślna implementacja klasy [OnInitDialog](#oninitdialog) wywołuje również `UpdateData` można ustawić wartość początkową kontrolki. Zazwyczaj zastąpienie `OnInitDialog` dalsze zainicjować kontrolki. `OnInitDialog` jest wywoływana po wszystkich kontrolkach okna dialogowe są tworzone i tuż przed okno dialogowe zostanie wyświetlone okno.

Możesz wywołać `CWnd::UpdateData` w dowolnym momencie podczas wykonywania modalne lub niemodalne okno dialogowe.

Ręcznie w przypadku tworzenia okno dialogowe, możesz dodać zmienne Członkowskie niezbędne do klasy pochodnej okno dialogowe samodzielnie, a następnie dodaj funkcje Członkowskie, aby ustawić lub pobrać te wartości.

Modalne okno dialogowe zostanie zamknięte automatycznie, gdy użytkownik naciśnie przycisk OK lub Anuluj lub gdy kod wywołuje `EndDialog` funkcja elementu członkowskiego.

Podczas implementowania niemodalnego okna dialogowego zawsze zastępuje `OnCancel` funkcja elementu członkowskiego, a następnie wywołać `DestroyWindow` z znajdujący się w nim. Nie wywołuj klasy bazowej `CDialog::OnCancel`, ponieważ wywołuje `EndDialog`, które spowoduje, że okno dialogowe niewidoczne, ale nie spowoduje zniszczenie. Należy również zastąpić `PostNcDestroy` dla niemodalnych okien dialogowych, aby możliwe było usunięcie **to**, ponieważ Niemodalne okna dialogowe zwykle są przydzielane przy użyciu **nowe**. Zazwyczaj są konstruowane na ramce modalnych okien dialogowych i nie ma potrzeby `PostNcDestroy` oczyszczania.

Aby uzyskać więcej informacji na temat `CDialog`, zobacz [okna dialogowe](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cdialog"></a>  CDialog::CDialog

Do konstruowania opartego na zasobach modalne okno dialogowe, należy wywołać dowolnej postaci publicznego konstruktora.

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
Zawiera ciąg zakończony znakiem null, który nazywa się okno dialogowe zasobu szablon.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablon okno dialogowe.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

### <a name="remarks"></a>Uwagi

Jeden formularz Konstruktor zapewnia dostęp do zasobu okna dialogowego według nazwy szablonu. Innego konstruktora zapewnia dostęp, numer Identyfikatora szablonu, zwykle za pomocą **IDD_** prefiksu (na przykład IDD_DIALOG1).

Aby utworzyć modalne okno dialogowe z szablonu w pamięci, najpierw wywołać konstruktora bez parametrów, chronione, a następnie wywołać `InitModalIndirect`.

Po konstruujesz modalne okno dialogowe z jednej z metod powyżej wywołać `DoModal`.

Do konstruowania niemodalnego okna dialogowego, należy użyć formy chronionych `CDialog` konstruktora. Konstruktor jest chroniony, ponieważ należy wywieść klasę własne okno dialogowe w taki sposób, aby wdrożyć niemodalnego okna dialogowego. Konstrukcja niemodalne okno dialogowe jest procesem dwuetapowym. Pierwsze wywołanie konstruktora; następnie wywołaj `Create` funkcji elementu członkowskiego, aby utworzyć okno dialogowe oparte na zasobach, lub zadzwoń `CreateIndirect` utworzyć okno dialogowe z szablonu w pamięci.

##  <a name="create"></a>  CDialog::Create

Wywołaj `Create` utworzyć niemodalnego okna dialogowego za pomocą szablonu okno dialogowe z zasobu.

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
Zawiera ciąg zakończony znakiem null, który nazywa się okno dialogowe zasobu szablon.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego (typu [CWnd](../../mfc/reference/cwnd-class.md)) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablon okno dialogowe.

### <a name="return-value"></a>Wartość zwracana

Obie formy zwracają wartość różną od zera, jeśli okno dialogowe Tworzenie i Inicjowanie zostały pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można umieścić wywołanie `Create` w konstruktorze lub wywołania po Konstruktor jest wywoływany.

Dwa rodzaje `Create` funkcja elementu członkowskiego są udostępniane na potrzeby dostępu do zasobu szablonu okno dialogowe Nazwa szablonu lub numer identyfikacyjny szablonu (na przykład IDD_DIALOG1).

Dla obu formularzy należy przekazać wskaźnik do obiektu okna nadrzędnego. Jeśli *pParentWnd* ma wartość NULL, okno dialogowe zostanie utworzona z jej okna nadrzędnego lub właściciela równa okna głównego aplikacji.

`Create` Funkcja elementu członkowskiego zwraca natychmiast, po utworzeniu okno dialogowe.

Jeśli podczas tworzenia okna nadrzędnego, powinny zostać wyświetlone okno dialogowe, należy użyć stylu WS_VISIBLE w szablonie okno dialogowe. W przeciwnym razie należy wywołać `ShowWindow`. Dodatkowo style okno dialogowe i aplikacji, zobacz [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktury w zestawie Windows SDK i [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) w *odwołanie MFC*.

Użyj `CWnd::DestroyWindow` funkcję, aby zniszczyć okno dialogowe, utworzone przez `Create` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć niemodalne okno dialogowe z szablonu okna dialogowego w pamięci.

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
Wskazuje pamięci, który zawiera szablon okno dialogowe pozwala utworzyć okno dialogowe. Ten szablon jest w formie [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) informacje dotyczące struktury i kontroli, zgodnie z opisem w zestawie Windows SDK.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego obiektu okna dialogowego (typu [CWnd](../../mfc/reference/cwnd-class.md)). Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

*lpDialogInit*<br/>
Wskazuje na zasób DLGINIT.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej, zawierający szablon okno dialogowe. Ten szablon jest w formie `DLGTEMPLATE` struktury i danych dla każdego formantu w oknie dialogowym.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli okno dialogowe zostało utworzone i zainicjowane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CreateIndirect` Funkcja elementu członkowskiego zwraca natychmiast, po utworzeniu okno dialogowe.

Jeśli podczas tworzenia okna nadrzędnego, powinny zostać wyświetlone okno dialogowe, należy użyć stylu WS_VISIBLE w szablonie okno dialogowe. W przeciwnym razie należy wywołać `ShowWindow` aby spowodować, że są wyświetlane. Aby uzyskać więcej informacji na temat określania innymi stylami okno dialogowe w szablonie, zobacz [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktury w zestawie Windows SDK.

Użyj `CWnd::DestroyWindow` funkcję, aby zniszczyć okno dialogowe, utworzone przez `CreateIndirect` funkcji.

Okna dialogowe, które zawierają formanty ActiveX wymagają dodatkowe informacje podane w zasobie DLGINIT.

##  <a name="domodal"></a>  CDialog::DoModal

Wywołaj tę funkcję elementu członkowskiego wywołuje modalne okno dialogowe i zwracają wynik okno dialogowe po zakończeniu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

**Int** wartość, która określa wartość *Nwynik* parametr, który został przekazany do [CDialog::EndDialog](#enddialog) funkcja elementu członkowskiego, który jest używany, aby zamknąć okno dialogowe. Wartość zwracana jest wartość -1, jeśli funkcja nie można utworzyć okna dialogowego lub IDABORT Jeśli wystąpił inny błąd, w którym to przypadku w oknie danych wyjściowych będzie zawierać informacje o błędzie z [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego obsługuje wszystkich interakcji z użytkownikiem, gdy okno dialogowe jest aktywne. Jest to, co sprawia, że okno dialogowe modalne; oznacza to użytkownik nie może korzystać z innymi oknami, do czasu zamknięcia okna dialogowego.

Jeśli użytkownik kliknie jeden z przycisków w oknie dialogowym, takich jak OK lub przycisk Anuluj, funkcji składowej obsługi wiadomości, takich jak [onok —](#onok) lub [OnCancel](#oncancel), jest wywoływana, aby zamknąć okno dialogowe. Wartość domyślna `OnOK` funkcja elementu członkowskiego zostanie weryfikacji i aktualizować dane okno dialogowe i zamknąć okno dialogowe z wynikiem IDOK i wartość domyślna `OnCancel` składowa zostanie zamknięte okno dialogowe z wynikiem IDCANCEL bez sprawdzania poprawności i aktualizowanie okno dialogowe dane. Możesz przesłonić te funkcje obsługi komunikatów, aby zmienić ich zachowanie.

> [!NOTE]
> `PreTranslateMessage` jest teraz nazywana do przetwarzania komunikatów okno modalne okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

Wywołaj tę funkcję elementu członkowskiego, aby zakończyć modalne okno dialogowe.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*Nwynik*<br/>
Zawiera wartość zwracaną z okna dialogowego do obiektu wywołującego `DoModal`.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca *Nwynik* jako wartość zwracaną `DoModal`. Należy użyć `EndDialog` funkcję, aby zakończyć przetwarzanie po każdym utworzeniu modalne okno dialogowe.

Możesz wywołać `EndDialog` w dowolnym momencie, nawet w [OnInitDialog](#oninitdialog), w którym to przypadku należy zamknąć okno dialogowe przed nią jest wyświetlany lub przed ustawieniem fokus wprowadzania.

`EndDialog` nie natychmiast zamknąć okno dialogowe. Zamiast ustawia flagę, która określa, że okno dialogowe, aby zamknąć tak szybko, jak zwraca bieżącej obsługi wiadomości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

Wywołaj `GetDefID` funkcję elementu członkowskiego, aby uzyskać identyfikator formantu mapami domyślny dla okna dialogowego.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość 32-bitowa ( `DWORD`). Jeśli przycisk domyślny ma wartość Identyfikatora, słowa wyższego rzędu zawiera DC_HASDEFID i słowo niskiego rzędu zawiera wartość Identyfikatora. Jeśli przycisk domyślny ma wartość, wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

Jest to zazwyczaj przycisku OK.

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

Przenosi fokus do określonego formantu w oknie dialogowym.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Identyfikuje okna (kontrola), który ma zostać ustawiony fokus.

### <a name="remarks"></a>Uwagi

Aby uzyskać wskaźnik do kontrolki (okno podrzędne) do przekazania jako *pWndCtrl*, wywołaj `CWnd::GetDlgItem` funkcji elementu członkowskiego, która zwraca wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować obiektu modalne okno dialogowe, za pomocą szablonu okno dialogowe, które konstruowania w pamięci.

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
Wskazuje pamięci, który zawiera szablon okno dialogowe pozwala utworzyć okno dialogowe. Ten szablon jest w formie [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) informacje dotyczące struktury i kontroli, zgodnie z opisem w zestawie Windows SDK.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej, zawierający szablon okno dialogowe. Ten szablon jest w formie `DLGTEMPLATE` struktury i danych dla każdego formantu w oknie dialogowym.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

*lpDialogInit*<br/>
Wskazuje na zasób DLGINIT.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiektu okna dialogowego zostało utworzone i zainicjowane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby utworzyć modalne okno dialogowe pośrednio, przydzielają blok pamięci globalnej i wypełnić ją z szablonu okna dialogowego. Następnie wywołaj pustą `CDialog` konstruktora do konstruowania obiektu okno dialogowe. Następnie wywołaj `InitModalIndirect` przechowywać swoje dojście do szablonu okna dialogowego w pamięci. Okno dialogowe Windows jest utworzony i wyświetlony później, gdy [DoModal](#domodal) funkcja członkowska jest wywoływana.

Okna dialogowe, które zawierają formanty ActiveX wymagają dodatkowe informacje podane w zasobie DLGINIT.

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

Wywołanie konwersji jednostek okno dialogowe prostokąta do jednostek ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lprect —*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera okno dialogowe służy do koordynowania ma zostać przekonwertowany.

### <a name="remarks"></a>Uwagi

Okno dialogowe jednostki są wyrażony w postaci bieżące okno dialogowe podstawowej jednostce pochodzi od średniej szerokości i wysokości znaków czcionkę tekstu okno dialogowe. Jedna jednostka poziomy to jedna czwarta jednostki podstawowej szerokość okno dialogowe, a jedna jednostka w pionie jest jednej ósmej jednostki podstawowej wysokość okno dialogowe.

`GetDialogBaseUnits` Windows funkcja zwraca informacje o rozmiarze do czcionki systemowej, ale można określić inną czcionkę dla każdego okna dialogowego, jeśli używasz stylu DS_SETFONT w pliku definicji zasobu. `MapDialogRect` Funkcja Windows używa czcionki odpowiednie dla tego okna dialogowego.

`MapDialogRect` Funkcji składowej zastępuje jednostki okno dialogowe *lprect —* z ekranu jednostki (w pikselach), dzięki czemu prostokąt można utworzyć okno dialogowe lub położenie formantu w polu.

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Przenosi fokus do następnego formantu w oknie dialogowym.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus jest na ostatni formantu w oknie dialogowym, przenosi się do pierwszego formantu.

##  <a name="oncancel"></a>  CDialog::OnCancel

Struktura wywołuje tę metodę, gdy użytkownik kliknie **anulować** lub naciśnięcie klawisza ESC w oknie dialogowym modalne lub niemodalne.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Uwagi

Przesłoń tę metodę w celu wykonywania akcji (taką jak przywracanie stare dane) po użytkownik zamknie okno dialogowe, klikając **anulować** lub naciskając klawisz ESC. Modalne okno dialogowe zostanie zamknięte domyślnie przez wywołanie metody [EndDialog](#enddialog) i powodują, że [DoModal](#domodal) do zwrócenia IDCANCEL.

W przypadku zaimplementowania **anulować** przycisku w niemodalnego okna dialogowego, konieczne jest przesłonięcie `OnCancel` metody i wywołania [destroywindow —](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niego. Nie wywołuj metody klasy podstawowej, ponieważ wywołuje `EndDialog`, który będzie ukrywanie okna dialogowego, ale nie niszczy go.

> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który jest kompilowany w Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

Ta metoda jest wywoływana w odpowiedzi na `WM_INITDIALOG` wiadomości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Określa, czy aplikacja ma fokus wprowadzania formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość różną od zera, Windows ustawia fokus wprowadzania do domyślnej lokalizacji, pierwszy formant w oknie dialogowym. Aplikacja może zwrócić 0, tylko wtedy, gdy jawnie ustawiono fokus wprowadzania formantów w oknie dialogowym.

### <a name="remarks"></a>Uwagi

Windows wysyła `WM_INITDIALOG` wiadomości do okna dialogowego podczas [Utwórz](#create), [CreateIndirect](#createindirect), lub [DoModal](#domodal) wywołania, które występują, bezpośrednio przed okno dialogowe zostanie wyświetlona.

Przesłania tę metodę, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno dialogowe jest zainicjowany. W wersji zastąpione, należy najpierw wywołać klasy bazowej `OnInitDialog` ignorowanie wartość zwracaną. Zazwyczaj zwróci `TRUE` ze zgodnym z przesłoniętą metodę.

Windows wywołuje `OnInitDialog` funkcji przy użyciu wspólnej procedury standardowe globalne — okno dialogowe do wszystkich okien dialogowych biblioteki klas Microsoft Foundation. Nie wywołuje tę funkcję za pomocą mapy wiadomości, a w związku z tym nie trzeba wpis mapy komunikatów dla tej metody.

> [!NOTE]
> Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który jest kompilowany w Windows Vista lub nowszych systemach operacyjnych. Aby uzyskać więcej informacji o zmianach `CFileDialog` w obszarze Windows Vista i nowszych, zobacz [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

Wywołuje się, gdy użytkownik kliknie **OK** (przycisk z Identyfikatorem IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Przesłoń tę metodę, aby wykonywać akcje podczas **OK** zostanie aktywowany przycisk. Jeśli okno dialogowe zawiera sprawdzanie poprawności danych automatyczne i programu exchange, domyślna implementacja tej metody sprawdza poprawność danych okna dialogowego i aktualizuje odpowiednich zmiennych w aplikacji.

W przypadku zaimplementowania **OK** przycisku w niemodalnego okna dialogowego, konieczne jest przesłonięcie `OnOK` metody i wywołania [destroywindow —](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niego. Nie wywołuj metody klasy podstawowej, ponieważ wywołuje [EndDialog](#enddialog) które sprawia, że okno dialogowe jest niewidoczny, ale nie niszczy.

> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który jest kompilowany w Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

Określa czcionkę, którą kontrolkę okno dialogowe będzie używana podczas rysowania tekstu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Określa wskaźnik na czcionkę, która będzie służyć jako domyślną czcionkę dla wszystkich kontrolek w oknie dialogowym.

### <a name="remarks"></a>Uwagi

Okno dialogowe użyje określonej czcionki jako domyślny dla wszystkich jej kontrolek.

Edytor okien dialogowych zwykle Ustawia czcionkę okno dialogowe, w ramach zasobu szablon okno dialogowe.

> [!NOTE]
> Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który jest kompilowany w Windows Vista lub nowszych systemach operacyjnych. Aby uzyskać więcej informacji o zmianach `CFileDialog` w obszarze Windows Vista i nowszych, zobacz [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Ustawia fokus do poprzedniego formantu w oknie dialogowym.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus jest ustawiony na pierwszą kontrolkę w oknie dialogowym, przenosi do ostatniego formantu w oknie.

##  <a name="setdefid"></a>  CDialog::SetDefID

Zmienia domyślny formant mapami dla okna dialogowego.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Określa identyfikator kontrolki mapami, który ma zostać domyślny.

##  <a name="sethelpid"></a>  CDialog::SetHelpID

Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Określa identyfikator pomocy kontekstowej.

## <a name="see-also"></a>Zobacz też

[DLGCBR32 próbki MFC](../../visual-cpp-samples.md)<br/>
[Próbki MFC DLGTEMPL](../../visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

