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
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418721"
---
# <a name="cdialog-class"></a>Klasa CDialog

Klasa bazowa używana do wyświetlania okien dialogowych na ekranie.

## <a name="syntax"></a>Składnia

```
class CDialog : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDialog:: CDialog](#cdialog)|Konstruuje obiekt `CDialog`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDialog:: Create](#create)|Inicjuje obiekt `CDialog`. Tworzy niemodalne okno dialogowe i dołącza je do obiektu `CDialog`.|
|[CDialog:: IsDirect](#createindirect)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego w pamięci (nie opartego na zasobach).|
|[CDialog::D oModal](#domodal)|Wywołuje modalne okno dialogowe i zwraca po zakończeniu.|
|[CDialog:: zdarzenie EndDialog](#enddialog)|Zamyka modalne okno dialogowe.|
|[CDialog:: GetDefID](#getdefid)|Pobiera identyfikator domyślnej kontrolki przesuwania dla okna dialogowego.|
|[CDialog:: GotoDlgCtrl](#gotodlgctrl)|Przenosi fokus do określonego formantu okna dialogowego w oknie dialogowym.|
|[CDialog:: InitModalIndirect](#initmodalindirect)|Tworzy modalne okno dialogowe z szablonu okna dialogowego w pamięci (nie opartego na zasobach). Parametry są przechowywane do momentu wywołania funkcji `DoModal`.|
|[CDialog:: MapDialogRect](#mapdialogrect)|Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.|
|[CDialog:: NextDlgCtrl](#nextdlgctrl)|Przenosi fokus do następnej kontrolki okna dialogowego w oknie dialogowym.|
|[CDialog:: OnInitDialog](#oninitdialog)|Przesłoń, aby rozszerzyć Inicjowanie okna dialogowego.|
|[CDialog:: OnSetFont](#onsetfont)|Przesłoń, aby określić czcionkę, która ma być używana przez formant okna dialogowego podczas rysowania tekstu.|
|[CDialog::P revDlgCtrl](#prevdlgctrl)|Przenosi fokus do poprzedniej kontrolki okna dialogowego w oknie dialogowym.|
|[CDialog:: SetDefID](#setdefid)|Zmienia domyślny formant kontrolki dla okna dialogowego na określony przycisk.|
|[CDialog:: SetHelpID](#sethelpid)|Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDialog:: OnCancel](#oncancel)|Przesłoń, aby wykonać akcję Cancel lub klawisza ESC. Domyślnie zamyka okno dialogowe, a `DoModal` zwraca IDCANCEL.|
|[CDialog:: OnOK —](#onok)|Przesłoń, aby wykonać akcję przycisku OK w modalnym oknie dialogowym. Domyślnie zamyka okno dialogowe, a `DoModal` zwraca IDOK.|

## <a name="remarks"></a>Uwagi

Okna dialogowe mają dwa typy: modalne i niemodalne. Modalne okno dialogowe musi zostać zamknięte przez użytkownika przed kontynuowaniem aplikacji. Niemodalne okno dialogowe umożliwia użytkownikowi wyświetlanie okna dialogowego i powrót do innego zadania bez anulowania lub usuwania okna dialogowego.

Obiekt `CDialog` jest kombinacją szablonu okna dialogowego i klasy pochodnej `CDialog`. Użyj edytora okien dialogowych, aby utworzyć szablon okna dialogowego i zapisać go w zasobie, a następnie użyj Kreatora dodawania klasy, aby utworzyć klasę pochodną `CDialog`.

Okno dialogowe, jak każde inne okno, odbiera komunikaty z systemu Windows. W oknie dialogowym szczególnie interesuje się obsługę komunikatów powiadomień z formantów okna dialogowego, ponieważ jest to sposób interakcji użytkownika z oknem dialogowym. Użyj [kreatora klas](mfc-class-wizard.md) , aby wybrać komunikaty, które chcesz obsłużyć i dodać odpowiednie wpisy mapy komunikatów i funkcje członkowskie obsługi komunikatów do klasy. Musisz tylko napisać kod specyficzny dla aplikacji w funkcjach składowych programu obsługi.

Jeśli wolisz, zawsze możesz pisać wpisy mapy komunikatów i funkcje członkowskie ręcznie.

We wszystkich, ale najbardziej uproszczonym oknie dialogowym, możesz dodać zmienne członkowskie do klasy dialog pochodna, aby przechowywać dane wprowadzone w kontrolkach okna dialogowego przez użytkownika lub wyświetlać dane dla użytkownika. Za pomocą Kreatora dodawania zmiennej można tworzyć zmienne Członkowskie i kojarzyć je z kontrolkami. W tym samym czasie wybierasz typ zmiennej i dopuszczalny zakres wartości dla każdej zmiennej. Kreator kodu dodaje Zmienne Członkowskie do klasy dialogu pochodnego.

Mapa danych jest generowana w celu automatycznego obsłużenia wymiany danych między zmiennymi składowymi i kontrolkami okna dialogowego. Mapa danych zawiera funkcje, które inicjują kontrolki w oknie dialogowym z odpowiednimi wartościami, pobierają dane i weryfikują dane.

Aby utworzyć modalne okno dialogowe, Skonstruuj obiekt na stosie przy użyciu konstruktora dla klasy dialogu pochodnego, a następnie Wywołaj `DoModal`, aby utworzyć okno dialogowe i jego formanty. Jeśli chcesz utworzyć niemodalne okno dialogowe, wywołaj `Create` w konstruktorze klasy dialogowej.

Możesz również utworzyć szablon w pamięci przy użyciu struktury danych [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) , zgodnie z opisem w Windows SDK. Po utworzeniu obiektu `CDialog` Wywołaj metodę [Undirect](#createindirect) , aby utworzyć niemodalne okno dialogowe lub wywołać [InitModalIndirect](#initmodalindirect) i [DoModal](#domodal) w celu utworzenia modalnego okna dialogowego.

Mapa danych wymiany i walidacji jest zapisywana w przesłonięciu `CWnd::DoDataExchange`, który jest dodawany do nowej klasy okna dialogowego. Aby uzyskać więcej informacji na temat funkcji Exchange i Validation, zobacz [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) member function in in `CWnd`.

Zarówno programista, jak i struktura wywołania `DoDataExchange` pośrednio przez wywołanie [CWnd:: UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Struktura wywołuje `UpdateData`, gdy użytkownik kliknie przycisk OK, aby zamknąć modalne okno dialogowe. (Dane nie są pobierane, jeśli kliknięto przycisk Anuluj). Domyślna implementacja [OnInitDialog](#oninitdialog) wywołuje również `UpdateData` w celu ustawienia wartości początkowych kontrolek. Zwykle przesłonięcie `OnInitDialog` do dalszych zainicjowania kontrolek. `OnInitDialog` jest wywoływana po utworzeniu wszystkich kontrolek okna dialogowego, gdy zostanie wyświetlone okno dialogowe.

`CWnd::UpdateData` można wywołać w dowolnym momencie podczas wykonywania modalnych lub niemodalnych okien dialogowych.

W przypadku tworzenia okna dialogowego z ręcznym dodawaniem niezbędnych zmiennych składowych do pochodnej klasy okna dialogowego i Dodawanie lub pobieranie tych wartości.

Modalne okno dialogowe jest automatycznie zamykane, gdy użytkownik naciśnie przyciski OK lub Anuluj albo gdy kod wywołuje funkcję elementu członkowskiego `EndDialog`.

W przypadku zaimplementowania niemodalnego okna dialogowego zawsze Przesłoń `OnCancel` funkcję członkowską i Wywołaj `DestroyWindow` z niej. Nie wywołuj klasy bazowej `CDialog::OnCancel`, ponieważ wywołuje `EndDialog`, co spowoduje, że okno dialogowe zostanie niewidoczne, ale nie zostanie zniszczone. Należy również przesłonić `PostNcDestroy` dla niemodalnych okien dialogowych, aby **je usunąć,** ponieważ modalne okna dialogowe są zwykle przydzielono z **nowymi**. Modalne okna dialogowe są zwykle konstruowane w ramce i nie wymagają czyszczenia `PostNcDestroy`.

Aby uzyskać więcej informacji na temat `CDialog`, zobacz [okna dialogowe](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cdialog"></a>CDialog:: CDialog

Aby skonstruować modalne okno dialogowe oparte na zasobach, wywołaj albo publiczną postać konstruktora.

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
Zawiera ciąg zakończony znakiem null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu szablonu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt obiektu nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Jedna z form konstruktora zapewnia dostęp do zasobu okna dialogowego według nazwy szablonu. Inny Konstruktor zapewnia dostęp według numeru IDENTYFIKACYJNego szablonu, zazwyczaj z prefiksem **IDD_** (na przykład IDD_DIALOG1).

Aby skonstruować modalne okno dialogowe na podstawie szablonu w pamięci, najpierw Wywołaj bezparametryczny Konstruktor, a następnie Wywołaj `InitModalIndirect`.

Po utworzeniu modalnego okna dialogowego z jedną z powyższych metod Wywołaj `DoModal`.

Aby utworzyć niemodalne okno dialogowe, użyj chronionej formy konstruktora `CDialog`. Konstruktor jest chroniony, ponieważ należy utworzyć własną klasę okna dialogowego, aby zaimplementować niemodalne okno dialogowe. Konstrukcja niemodalnego okna dialogowego jest procesem dwuetapowym. Najpierw Wywołaj konstruktora; następnie wywołaj funkcję członkowską `Create`, aby utworzyć okno dialogowe oparte na zasobach, lub wywołaj `CreateIndirect`, aby utworzyć okno dialogowe z szablonu w pamięci.

##  <a name="create"></a>CDialog:: Create

Wywołaj `Create`, aby utworzyć niemodalne okno dialogowe przy użyciu szablonu okna dialogowego z zasobu.

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
Zawiera ciąg zakończony znakiem null, który jest nazwą zasobu szablonu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny (typu [CWnd](../../mfc/reference/cwnd-class.md)), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

*nIDTemplate*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu szablonu okna dialogowego.

### <a name="return-value"></a>Wartość zwrócona

Oba formularze zwracają wartość różną od zera, jeśli Tworzenie i Inicjowanie okna dialogowego zakończyło się pomyślnie. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz umieścić wywołanie do `Create` wewnątrz konstruktora lub wywołać je po wywołaniu konstruktora.

Dwie formy funkcji członkowskiej `Create` są udostępniane na potrzeby dostępu do zasobu szablonu okna dialogowego z nazwą szablonu lub numerem IDENTYFIKACYJNym szablonu (na przykład IDD_DIALOG1).

Dla obu formularzy Przekaż wskaźnik do obiektu okna nadrzędnego. Jeśli *pParentWnd* ma wartość null, okno dialogowe zostanie utworzone z oknem nadrzędnym lub jego właścicielem ustawionym na okno aplikacji głównej.

Funkcja członkowska `Create` zwraca natychmiast po utworzeniu okna dialogowego.

Użyj stylu WS_VISIBLE w szablonie okna dialogowego, jeśli okno dialogowe ma być wyświetlane po utworzeniu okna nadrzędnego. W przeciwnym razie musisz wywołać `ShowWindow`. Aby uzyskać więcej stylów okna dialogowego i ich aplikacji, zapoznaj się ze strukturą [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) w [stylach](../../mfc/reference/styles-used-by-mfc.md#window-styles) Windows SDK i okna w *Kompendium MFC*.

Użyj funkcji `CWnd::DestroyWindow`, aby zniszczyć okno dialogowe utworzone przez funkcję `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>CDialog:: IsDirect

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
Wskazuje pamięć, która zawiera szablon okna dialogowego użyty do utworzenia okna dialogowego. Ten szablon ma postać struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) i informacji o kontroli, zgodnie z opisem w Windows SDK.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny okna dialogowego (typu [CWnd](../../mfc/reference/cwnd-class.md)). Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

*lpDialogInit*<br/>
Wskazuje zasób DLGINIT.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej zawierającej szablon okna dialogowego. Ten szablon ma postać struktury `DLGTEMPLATE` i danych dla każdej kontrolki w oknie dialogowym.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli okno dialogowe zostało utworzone i zainicjowane pomyślnie. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja członkowska `CreateIndirect` zwraca natychmiast po utworzeniu okna dialogowego.

Użyj stylu WS_VISIBLE w szablonie okna dialogowego, jeśli okno dialogowe ma być wyświetlane po utworzeniu okna nadrzędnego. W przeciwnym razie należy wywołać `ShowWindow`, aby spowodować pojawienie się. Aby uzyskać więcej informacji na temat sposobu określania innych stylów okna dialogowego w szablonie, zobacz strukturę [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) w Windows SDK.

Użyj funkcji `CWnd::DestroyWindow`, aby zniszczyć okno dialogowe utworzone przez funkcję `CreateIndirect`.

Okna dialogowe zawierające kontrolki ActiveX wymagają dodatkowych informacji podanych w zasobie DLGINIT.

##  <a name="domodal"></a>CDialog::D oModal

Wywołaj tę funkcję elementu członkowskiego, aby wywołać modalne okno dialogowe i zwrócić wynik okna dialogowego po zakończeniu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość **int** , która określa wartość parametru *nwynik* , który został przekazano do funkcji członkowskiej [CDialog:: zdarzenie EndDialog](#enddialog) , która jest używana do zamykania okna dialogowego. Wartość zwracana to-1, jeśli funkcja nie może utworzyć okna dialogowego lub IDABORT, jeśli wystąpił inny błąd, w takim przypadku okno dane wyjściowe będzie zawierać informacje o błędzie z funkcji [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska obsługuje całą interakcję z użytkownikiem, gdy okno dialogowe jest aktywne. To sprawia, że okno dialogowe jest modalne; oznacza to, że użytkownik nie może współdziałać z innymi oknami, dopóki okno dialogowe nie zostanie zamknięte.

Jeśli użytkownik kliknie jeden z elementów w oknie dialogowym, na przykład OK lub Anuluj, funkcja członkowska obsługi komunikatów, taka jak [OnOK —](#onok) lub [OnCancel](#oncancel), jest wywoływana w celu zamknięcia okna dialogowego. Domyślna funkcja członkowska `OnOK` będzie sprawdzać poprawność i zaktualizować dane okna dialogowego i zamknąć okno dialogowe z wynikiem IDOK, a domyślna `OnCancel` funkcja członkowska zamknie okno dialogowe z wynikiem IDCANCEL bez weryfikowania ani aktualizowania danych okna dialogowego. Można zastąpić te funkcje programu obsługi komunikatów, aby zmienić ich zachowanie.

> [!NOTE]
> `PreTranslateMessage` jest teraz wywoływana dla modalnego przetwarzania komunikatów okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>CDialog:: zdarzenie EndDialog

Wywołaj tę funkcję elementu członkowskiego, aby zakończyć modalne okno dialogowe.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*Nwynik*<br/>
Zawiera wartość, która ma zostać zwrócona z okna dialogowego do obiektu wywołującego `DoModal`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwraca *nwynik* jako wartość zwracaną `DoModal`. Należy użyć funkcji `EndDialog`, aby zakończyć przetwarzanie po każdym utworzeniu modalnego okna dialogowego.

Możesz wywoływać `EndDialog` w dowolnym momencie, nawet w [OnInitDialog](#oninitdialog), w takim przypadku należy zamknąć okno dialogowe przed jego wyświetleniem lub przed ustawieniem fokus wprowadzania.

`EndDialog` nie zamyka natychmiast okna dialogowego. Zamiast tego ustawia flagę, która kieruje okno dialogowe, aby zamknąć, gdy tylko bieżąca procedura obsługi komunikatów zwróci wartość.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>CDialog:: GetDefID

Wywołaj funkcję elementu członkowskiego `GetDefID`, aby uzyskać identyfikator domyślnej kontrolki łącznika dla okna dialogowego.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość 32-bitowa (`DWORD`). Jeśli domyślny przycisk ma wartość identyfikatora, wyraz o wysokiej kolejności zawiera DC_HASDEFID a wyraz o niskiej kolejności zawiera wartość identyfikatora. Jeśli domyślny przycisk nie ma wartości identyfikatora, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Jest to zazwyczaj przycisk OK.

##  <a name="gotodlgctrl"></a>CDialog:: GotoDlgCtrl

Przenosi fokus do określonego formantu w oknie dialogowym.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Identyfikuje okno (formant), które ma otrzymać fokus.

### <a name="remarks"></a>Uwagi

Aby uzyskać wskaźnik do kontrolki (okno potomne) do przekazania jako *pWndCtrl*, wywołaj funkcję członkowską `CWnd::GetDlgItem`, która zwraca wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>CDialog:: InitModalIndirect

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować modalny obiekt okna dialogowego przy użyciu szablonu okna dialogowego, który został skonstruowany w pamięci.

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
Wskazuje pamięć, która zawiera szablon okna dialogowego użyty do utworzenia okna dialogowego. Ten szablon ma postać struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) i informacji o kontroli, zgodnie z opisem w Windows SDK.

*hDialogTemplate*<br/>
Zawiera dojście do pamięci globalnej zawierającej szablon okna dialogowego. Ten szablon ma postać struktury `DLGTEMPLATE` i danych dla każdej kontrolki w oknie dialogowym.

*pParentWnd*<br/>
Wskazuje obiekt obiektu nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

*lpDialogInit*<br/>
Wskazuje zasób DLGINIT.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli obiekt okna dialogowego został pomyślnie utworzony i zainicjowany. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby bezpośrednio utworzyć modalne okno dialogowe, należy najpierw przydzielić globalny blok pamięci i wypełnić go szablonem okna dialogowego. Następnie Wywołaj pustego konstruktora `CDialog`, aby utworzyć obiekt okna dialogowego. Następnie Wywołaj `InitModalIndirect`, aby przechowywać uchwyt w szablonie okna dialogowego w pamięci. Okno dialogowe systemu Windows jest tworzone i wyświetlane później, gdy wywoływana jest funkcja członkowska [DoModal](#domodal) .

Okna dialogowe zawierające kontrolki ActiveX wymagają dodatkowych informacji podanych w zasobie DLGINIT.

##  <a name="mapdialogrect"></a>CDialog:: MapDialogRect

Wywołaj, aby przekonwertować jednostki okna dialogowego prostokąta na jednostki ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który zawiera współrzędne okna dialogowego do przekonwertowania.

### <a name="remarks"></a>Uwagi

Jednostki okna dialogowego są określane jako bieżąca jednostka bazowa okna dialogowego, która pochodzi od średniej szerokości i wysokości znaków w czcionce używanej dla tekstu okna dialogowego. Jedna jednostka w poziomie jest jedną czwartą jednostkowej szerokości okna dialogowego, a jedna jednostka pionowa to jedna ósma jednostki podstawowej wysokości okna dialogowego.

Funkcja `GetDialogBaseUnits` systemu Windows zwraca informacje o rozmiarze dla czcionki systemowej, ale można określić inną czcionkę dla każdego okna dialogowego, jeśli używasz stylu DS_SETFONT w pliku definicji zasobu. Funkcja `MapDialogRect` systemu Windows używa odpowiedniej czcionki dla tego okna dialogowego.

Funkcja członkowska `MapDialogRect` zastępuje jednostki okna dialogowego w *lpRect* za pomocą jednostek ekranu (pikseli), dzięki czemu prostokąt może służyć do tworzenia okna dialogowego lub umieszczania kontrolki w obrębie pola.

##  <a name="nextdlgctrl"></a>CDialog:: NextDlgCtrl

Przenosi fokus do następnego formantu w oknie dialogowym.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus znajduje się na ostatnim formancie w oknie dialogowym, przenosi do pierwszej kontrolki.

##  <a name="oncancel"></a>CDialog:: OnCancel

Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk **Anuluj** lub NACIŚNIE klawisz ESC w modalnym lub niemodalnym oknie dialogowym.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby wykonać akcje (na przykład Przywracanie starych danych), gdy użytkownik zamknie okno dialogowe, klikając **przycisk Anuluj** lub naciskając klawisz ESC. Domyślnie zamyka modalne okno dialogowe przez wywołanie [zdarzenie EndDialog](#enddialog) i powoduje, że [DoModal](#domodal) zwraca IDCANCEL.

W przypadku zaimplementowania przycisku **Anuluj** w niemodalnym oknie dialogowym należy zastąpić metodę `OnCancel` i wywołać [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) . Nie wywołuj metody klasy bazowej, ponieważ wywołuje `EndDialog`, co spowoduje, że okno dialogowe jest niewidoczne, ale nie niszczy.

> [!NOTE]
>  Nie można zastąpić tej metody, jeśli używasz obiektu `CFileDialog` w programie, który jest kompilowany w systemie Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>CDialog:: OnInitDialog

Ta metoda jest wywoływana w odpowiedzi na komunikat `WM_INITDIALOG`.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwrócona

Określa, czy aplikacja ustawi fokus wprowadzania na jeden z kontrolek w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość różną od zera, system Windows ustawia fokus wprowadzania do lokalizacji domyślnej, a pierwszy formant w oknie dialogowym. Aplikacja może zwrócić 0 tylko wtedy, gdy jawnie ustawił fokus wprowadzania na jeden z kontrolek w oknie dialogowym.

### <a name="remarks"></a>Uwagi

System Windows wysyła komunikat `WM_INITDIALOG` do okna dialogowego podczas wywołań [Create](#create), DoModal lub [](#domodal) [, które](#createindirect)występują bezpośrednio przed wyświetleniem okna dialogowego.

Zastąp tę metodę, jeśli chcesz przeprowadzić przetwarzanie specjalne po zainicjowaniu okna dialogowego. W zastąpionej wersji najpierw Wywołaj klasę bazową `OnInitDialog` ale zignoruj jej wartość zwracaną. Zwykle zwracasz `TRUE` z przesłoniętej metody.

System Windows wywołuje funkcję `OnInitDialog` przy użyciu standardowej globalnej procedury okna dialogowego, która jest wspólna dla wszystkich biblioteka MFC okien dialogowych. Nie wywołuje tej funkcji za pomocą mapy komunikatów, dlatego nie jest potrzebny wpis mapy komunikatów dla tej metody.

> [!NOTE]
> Nie można zastąpić tej metody, jeśli używasz obiektu `CFileDialog` w programie, który jest kompilowany w systemie Windows Vista lub nowszych systemach operacyjnych. Aby uzyskać więcej informacji na temat zmian w `CFileDialog` w systemie Windows Vista lub nowszym, zobacz [Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog:: OnOK —

Wywoływana, gdy użytkownik kliknie przycisk **OK** (przycisk z identyfikatorem IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby wykonać akcje po aktywowaniu przycisku **OK** . Jeśli okno dialogowe zawiera automatyczne sprawdzanie poprawności danych i program Exchange, domyślna implementacja tej metody weryfikuje dane okna dialogowego i aktualizuje odpowiednie zmienne w aplikacji.

W przypadku zaimplementowania przycisku **OK** w niemodalnym oknie dialogowym należy zastąpić metodę `OnOK` i wywołać [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) . Nie wywołuj metody klasy bazowej, ponieważ wywołuje [zdarzenie EndDialog](#enddialog) , co sprawia, że okno dialogowe jest niewidoczne, ale nie niszczy.

> [!NOTE]
>  Nie można zastąpić tej metody, jeśli używasz obiektu `CFileDialog` w programie, który jest kompilowany w systemie Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>CDialog:: OnSetFont

Określa czcionkę, która będzie używana przez formant okna dialogowego podczas rysowania tekstu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
podczas Określa wskaźnik do czcionki, która będzie używana jako czcionka domyślna dla wszystkich kontrolek w tym oknie dialogowym.

### <a name="remarks"></a>Uwagi

W oknie dialogowym zostanie użyta określona czcionka jako domyślna dla wszystkich jej kontrolek.

Edytor okien dialogowych zwykle ustawia czcionkę okna dialogowego jako część zasobu szablonu okna dialogowego.

> [!NOTE]
> Nie można zastąpić tej metody, jeśli używasz obiektu `CFileDialog` w programie, który jest kompilowany w systemie Windows Vista lub nowszych systemach operacyjnych. Aby uzyskać więcej informacji na temat zmian w `CFileDialog` w systemie Windows Vista lub nowszym, zobacz [Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>CDialog::P revDlgCtrl

Ustawia fokus na poprzednią kontrolkę w oknie dialogowym.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Uwagi

Jeśli fokus jest ustawiony na pierwszej kontrolce w oknie dialogowym, przenosi się do ostatniej kontrolki w polu.

##  <a name="setdefid"></a>CDialog:: SetDefID

Zmienia domyślny formant z kontrolką dla okna dialogowego.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Określa identyfikator kontrolki przycisk, która stanie się wartością domyślną.

##  <a name="sethelpid"></a>CDialog:: SetHelpID

Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Określa identyfikator pomocy kontekstowej.

## <a name="see-also"></a>Zobacz też

[Przykład DLGCBR32 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład DLGTEMPL MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
