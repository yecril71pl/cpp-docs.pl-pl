---
title: Klasa CPrintDialog
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: 2a856c8067394e33976ba8ccdaa34be81ee11091
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372897"
---
# <a name="cprintdialog-class"></a>Klasa CPrintDialog

Hermetyzuje usługi świadczone przez wspólne okno dialogowe Windows do drukowania.

## <a name="syntax"></a>Składnia

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Konstruuje `CPrintDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki, bez wyświetlania okna dialogowego drukowania.|
|[CPrintDialog::DoModal](#domodal)|Zostanie wyświetlone okno dialogowe i umożliwia użytkownikowi dokonać wyboru.|
|[CPrintDialog::GetCopies](#getcopies)|Pobiera liczbę kopii żądanie.|
|[CPrintDialog::GetDefaults](#getdefaults)|Pobiera ustawienia domyślne urządzenia bez wyświetlania okna dialogowego.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Pobiera nazwę drukarki aktualnie wybranego urządzenia.|
|[CPrintDialog::GetDevMode](#getdevmode)|Pobiera `DEVMODE` struktury.|
|[CPrintDialog::GetDriverName](#getdrivername)|Pobiera nazwę aktualnie wybranego sterownika.|
|[CPrintDialog::GetFromPage](#getfrompage)|Pobiera stronę początkową zakresu wydruku.|
|[CPrintDialog::GetPortName](#getportname)|Pobiera nazwę portu aktualnie wybranego drukarki.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Pobiera uchwyt do kontekstu urządzenia drukarki.|
|[CPrintDialog::GetToPage](#gettopage)|Pobiera końcowy strony zakres wydruku.|
|[CPrintDialog::PrintAll](#printall)|Określa, czy umożliwia wydrukowanie wszystkich stron dokumentu.|
|[CPrintDialog::PrintCollate](#printcollate)|Określa, czy sortowane są żądane kopii.|
|[CPrintDialog::PrintRange](#printrange)|Określa, czy do drukowania określony zakres stron.|
|[CPrintDialog::PrintSelection](#printselection)|Określa, czy drukować tylko aktualnie wybrane elementy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktury używane w celu dostosowania `CPrintDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Wspólne okna dialogowe drukowania zapewniają prosty sposób implementacji okna dialogowe drukowania i zarządzania ustawienia wydruku w sposób zgodny ze standardami Windows.

> [!NOTE]
>  `CPrintDialogEx` Klasa hermetyzuje usługi świadczone przez arkusz własności drukowania Windows. Aby uzyskać więcej informacji, zobacz [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) Przegląd.

`CPrintDialog`w funkcji zostało zastąpione przez z [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), który jest przeznaczony do przedstawienia wspólne okno dialogowe dla obu konfiguracji drukowania i ustawienia strony.

Możesz polegać na platformę, by obsłużyć wiele aspektów proces drukowania dla danej aplikacji. W tym przypadku ramach automatycznie wyświetla Windows wspólne okno dialogowe drukowania. Można również obsłużył framework drukowania dla aplikacji, ale zastąp wspólne okno dialogowe drukowania własne okna dialogowego drukowania. Aby uzyskać więcej informacji o używaniu platformę do obsługi zadań drukowania, zobacz artykuł [drukowania](../../mfc/printing.md).

Jeśli chcesz, aby aplikacja obsługiwała drukowanie bez angażowania struktury, możesz użyć `CPrintDialog` klasy "w jakim jest" za pomocą konstruktora przewidzianej lub może pochodzić własne klasy okien dialogowych z `CPrintDialog` i zapisywanie konstruktora do własnych potrzeb. W obu przypadkach tych okien dialogowych będą zachowywać się jak standardowego okna dialogowe MFC, ponieważ są pochodnymi klasy `CCommonDialog`.

Aby użyć `CPrintDialog` obiektów, najpierw utwórz obiekt przy użyciu `CPrintDialog` konstruktora. Gdy okno dialogowe został skonstruowany, można ustawić lub zmodyfikować dowolne wartości na [m_pd](#m_pd) strukturę, aby zainicjować wartości formantów w oknie dialogowym. `m_pd` Struktury jest typu [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda). Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.

Jeśli nie podasz własne dojść w `m_pd` dla `hDevMode` i `hDevNames` członków, pamiętaj wywołać funkcję Windows `GlobalFree` dla te dojścia, gdy są wykonywane za pomocą okna dialogowego. Korzystając z ramowych implementacji ustawienia wydruku, dostarczone przez `CWinApp::OnFilePrintSetup`, nie masz zwolnienie uchwyty. Uchwyty są obsługiwane przez `CWinApp` i są zwalniane w `CWinApp`przez destruktora. Jest tylko bezpłatne te dojścia, korzystając z `CPrintDialog` autonomicznych.

Po inicjalizacji formantów okna dialogowego, należy wywołać `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. `DoModal` Zwraca, czy użytkownik wybrał przycisk OK (IDOK) lub anulować (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, możesz użyć jednej z `CPrintDialog`przez funkcje Członkowskie można pobrać informacji o danych wejściowych przez użytkownika.

`CPrintDialog::GetDefaults` Funkcja członkowska jest przydatne do pobierania bieżące ustawienia domyślne drukarki bez wyświetlania okna dialogowego. Ta funkcja elementu członkowskiego nie wymaga interakcji użytkownika.

Możesz użyć Windows `CommDlgExtendedError` funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i Dowiedz się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji zobacz zestaw Windows SDK.

`CPrintDialog` opiera się na pliku COMMDLG. Plik DLL, który jest dostarczany z programem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, należy wyprowadzić klasę z `CPrintDialog`, udostępniają szablon niestandardowy dialog i dodać mapy wiadomości, przetwarzanie komunikatów powiadomień od formantów rozszerzonego. Wszystkie nieprzetworzone komunikaty powinny być przekazywane do klasy bazowej. Dostosowywanie funkcji punktów zaczepienia nie jest wymagana.

Aby przetwarzać tę samą wiadomość inaczej w zależności od tego, czy jest okno dialogowe Ustawienia drukarki, musi pochodzić klasy dla każdego okna dialogowego. Konieczne jest również przesłonięcie Windows `AttachOnSetup` funkcji, która obsługuje tworzenie nowego okna dialogowego, gdy przycisk Ustawienia wydruku jest zaznaczony w oknie dialogowym drukowania.

Aby uzyskać więcej informacji na temat korzystania z `CPrintDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Tworzy obiekt okna dialogowego drukowania Windows albo ustawienia wydruku.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Określa, czy jest wyświetlany standardowe okno dialogowe drukowania Windows lub okno dialogowe Ustawienia wydruku. Ustaw ten parametr na wartość true, ekran standardowe okno dialogowe Ustawienia wydruku Windows. Ustaw ją na wartość FALSE, aby wyświetlić okno dialogowe drukowania Windows. Jeśli *bPrintSetupOnly* ma wartość FALSE, ustawienia wydruku, opcję, jeśli jest nadal wyświetlany w oknie dialogowym drukowania.

*dwFlags*<br/>
Co najmniej jeden flagi, których można użyć, aby dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Na przykład flaga PD_ALLPAGES ustawia domyślny zakres wydruku dla wszystkich stron dokumentu. Zobacz [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktury w zestawie Windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego tylko tworzy obiekt. Użyj `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe.

Należy pamiętać, że podczas wywoływania konstruktora z *bPrintSetupOnly* ma wartość FALSE, Flaga PD_RETURNDC automatycznie jest używana. Po wywołaniu `DoModal`, `GetDefaults`, lub `GetPrinterDC`, drukarki kontrolera domeny, które zostaną zwrócone w `m_pd.hDC`. Ten kontroler domeny musi być zwolniona przez wywołanie [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) przez obiekt wywołujący `CPrintDialog`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki (DC) na podstawie [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) struktury.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia nowo utworzoną drukarkę.

### <a name="remarks"></a>Uwagi

Ten kontroler domeny jest zakłada się, że bieżąca drukarka kontrolera domeny, a inne zostały wcześniej uzyskane drukarki, które kontrolery domeny muszą zostać usunięte przez użytkownika. Ta funkcja może zostać wywołana, a wynikowy DC określono, nigdy nie wyświetlania okna dialogowego drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Wyświetla wspólne okno dialogowe drukowania Windows i pozwala użytkownikowi na wybranie różnych opcji drukowania, takich jak liczba kopii, zakres stron oraz tego, czy mają być sortowane kopii.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli zwracana jest IDCANCEL, wywołaj Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcję, aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne opcje Okno dialogowe drukowania, ustawiając członkowie `m_pd` struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Po wywołaniu `DoModal`, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

Należy pamiętać, że podczas wywoływania konstruktora z *bPrintSetupOnly* ma wartość FALSE, Flaga PD_RETURNDC automatycznie jest używana. Po wywołaniu `DoModal`, `GetDefaults`, lub `GetPrinterDC`, drukarki kontrolera domeny, które zostaną zwrócone w `m_pd.hDC`. Ten kontroler domeny musi być zwolniona przez wywołanie [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) przez obiekt wywołujący `CPrintDialog`.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

Pobiera liczbę kopii żądanie.

```
int GetCopies() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kopii żądanie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` można pobrać liczby kopii żądane.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

Pobiera ustawienia domyślne urządzenia drukarki domyślnej bez wyświetlania okna dialogowego.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobrane wartości są umieszczane w `m_pd` struktury.

W niektórych przypadkach wywołanie tej funkcji będzie wywoływać [Konstruktor](#cprintdialog) dla `CPrintDialog` z *bPrintSetupOnly* ustawiony na wartość FALSE. W takich przypadkach drukarki kontrolera domeny i `hDevNames` i `hDevMode` (obsługuje dwa znajduje się w `m_pd` element członkowski danych) są przydzielane automatycznie.

IF konstruktora dla `CPrintDialog` została wywołana z *bPrintSetupOnly* ma wartość FALSE, ta funkcja nie zwróci jedynie `hDevNames` i `hDevMode` znajduje się w `m_pd.hDevNames` i `m_pd.hDevMode`) do obiektu wywołującego, ale zwróci drukarkę kontrolera domeny w `m_pd.hDC`. Jest odpowiedzialny za obiekt wywołujący, aby usunąć drukarki kontrolera domeny, a następnie wywołać Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) funkcja obsługuje po zakończeniu `CPrintDialog` obiektu.

### <a name="example"></a>Przykład

Ten fragment kodu pobiera kontekst urządzenia drukarki domyślnej i zgłasza użytkownikowi rozdzielczość drukarki w punktach na cal. (Ten atrybut możliwości drukarki jest często nazywany DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

Pobiera nazwę drukarki aktualnie wybranego urządzenia.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego drukarki.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) można pobrać nazwę aktualnie wybranej drukarki lub po wywołaniu [GetDefaults](#getdefaults) można pobrać bieżącego ustawienia domyślne urządzenia domyślnej drukarki. Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDeviceName` jako wartość `lpszDeviceName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

Ten fragment kodu przedstawia nazwę drukarki domyślnej użytkownika oraz port, który jest połączony, wraz z nazwą buforu, używanych przez drukarki. Kod może wyświetlać okno komunikatu, informujący, że, "drukarki domyślnej włączeniu HP LaserJet IIIP \\\server\share przy użyciu winspool.", na przykład.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

Pobiera `DEVMODE` struktury.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury danych, który zawiera informacje na temat inicjowania urządzenia i środowisko sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) funkcji, która jest opisana w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać informacji o urządzeniu drukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

Pobiera nazwę aktualnie wybranego sterownika.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określający nazwę sterownika zdefiniowaną przez system.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać nazwę sterownika drukarki zdefiniowaną przez system. Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

Pobiera stronę początkową zakresu wydruku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer strony początkowej w zakresie stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do pobrania na numer strony początkowej w zakresie stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

##  <a name="getportname"></a>  CPrintDialog::GetPortName

Pobiera nazwę portu aktualnie wybranego drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa portu aktualnie wybranego drukarki.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) pobrać nazwy portu aktualnie wybranego drukarki.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Pobiera uchwyt do kontekstu urządzenia drukarki.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia drukarki, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli *bPrintSetupOnly* parametru `CPrintDialog` konstruktor został FALSE (wskazująca, że wyświetlane jest okno dialogowe drukowania), następnie `GetPrinterDC` zwraca uchwyt do kontekstu urządzenia drukarki. Należy wywołać Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) funkcję, aby usunąć kontekst urządzenia, po zakończeniu korzystania z niego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Pobiera końcowy strony zakres wydruku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Końcowy numer z zakresu stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do pobrania na numer strony końcowej zakresu stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Struktura, w której członkowie przechowywania właściwości obiektu okna dialogowego.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Uwagi

Po konstruowanie `CPrintDialog` obiektu, możesz użyć `m_pd` można ustawić różne aspekty okno dialogowe przed wywołaniem [DoModal](#domodal) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat `m_pd` struktury, zobacz [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) w zestawie Windows SDK.

Jeśli zmodyfikujesz `m_pd` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Określa, czy umożliwia wydrukowanie wszystkich stron dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wszystkich stron w dokumencie mają być drukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy umożliwia wydrukowanie wszystkich stron w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

Określa, czy sortowane są żądane kopii.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli użytkownik wybierze collate pole wyboru w oknie dialogowym. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy drukarka powinna sortować wszystkie kopie dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

Określa, czy do drukowania określony zakres stron.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli tylko zakres stron w dokumencie mają być drukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy drukowanie szeroką gamę stron w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

Określa, czy drukować tylko aktualnie wybrane elementy.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli tylko wybrane elementy mają być drukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy można drukować tylko aktualnie wybrane elementy.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Zobacz także

[Próbki MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
