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
ms.openlocfilehash: 6490e5488c5ab3b808a02e3608b75541e4063d8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364065"
---
# <a name="cprintdialog-class"></a>Klasa CPrintDialog

Hermetyzuje usługi świadczone przez wspólne okno dialogowe systemu Windows do drukowania.

## <a name="syntax"></a>Składnia

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Konstruuje `CPrintDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki bez wyświetlania okna dialogowego Drukowanie.|
|[CPrintDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[CPrintDialog::GetCopies](#getcopies)|Pobiera liczbę żądanych kopii.|
|[CPrintDialog::GetDefaults](#getdefaults)|Pobiera ustawienia domyślne urządzenia bez wyświetlania okna dialogowego.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Pobiera nazwę aktualnie wybranego urządzenia drukarki.|
|[CPrintDialog::GetDevMode](#getdevmode)|Pobiera strukturę. `DEVMODE`|
|[CPrintDialog::GetDriverName](#getdrivername)|Pobiera nazwę aktualnie wybranego sterownika drukarki.|
|[CPrintDialog::GetFromPage](#getfrompage)|Pobiera stronę początkową zakresu wydruku.|
|[CPrintDialog::GetPortName](#getportname)|Pobiera nazwę aktualnie wybranego portu drukarki.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Pobiera dojście do kontekstu urządzenia drukarki.|
|[CPrintDialog::GetToPage](#gettopage)|Pobiera końcową stronę zakresu wydruku.|
|[CPrintDialog::PrintAll](#printall)|Określa, czy mają być drukowane wszystkie strony dokumentu.|
|[CPrintDialog::PrintCollate](#printcollate)|Określa, czy wymagane są posortowane kopie.|
|[CPrintDialog::PrintRange](#printrange)|Określa, czy mają być drukowane tylko określony zakres stron.|
|[CPrintDialog::PzmarszczekWyborzowanie](#printselection)|Określa, czy mają być drukowane tylko aktualnie zaznaczone elementy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktura używana do dostosowywania `CPrintDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Typowe okna dialogowe drukowania umożliwiają łatwe implementowanie okien dialogowych Instalacji drukowania i drukowania w sposób zgodny ze standardami systemu Windows.

> [!NOTE]
> Klasa `CPrintDialogEx` hermetyzuje usługi świadczone przez arkusz właściwości Windows Print. Aby uzyskać więcej informacji, zobacz [omówienie CPrintDialogEx.](../../mfc/reference/cprintdialogex-class.md)

`CPrintDialog`'s funkcjonalność jest zastępowany przez [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), który ma na celu zapewnienie wspólnego okna dialogowego dla konfiguracji drukowania i konfiguracji strony.

Można polegać na platformie do obsługi wielu aspektów procesu drukowania dla aplikacji. W takim przypadku struktura automatycznie wyświetla typowe okno dialogowe systemu Windows do drukowania. Można również mieć dojście do obsługi struktury dla aplikacji, ale zastąpić typowe okno dialogowe Drukowanie własnym ok. Aby uzyskać więcej informacji na temat używania struktury do obsługi zadań drukowania, zobacz artykuł [Drukowanie](../../mfc/printing.md).

Jeśli chcesz, aby aplikacja do obsługi drukowania bez zaangażowania `CPrintDialog` struktury, można użyć klasy "tak, jak jest" z `CPrintDialog` konstruktora pod warunkiem, lub można wyprowadzić własną klasę okna dialogowego z i napisać konstruktora do własnych potrzeb. W obu przypadkach te okna dialogowe będą zachowywać się jak standardowe `CCommonDialog`okna dialogowe MFC, ponieważ pochodzą z klasy .

Aby użyć `CPrintDialog` obiektu, należy najpierw `CPrintDialog` utworzyć obiekt przy użyciu konstruktora. Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować dowolne wartości w strukturze [m_pd,](#m_pd) aby zainicjować wartości formantów okna dialogowego. Struktura `m_pd` jest typu [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Jeśli nie podasz własnych uchwytów `m_pd` `hDevMode` dla `hDevNames` i członków, należy wywołać funkcję `GlobalFree` systemu Windows dla tych uchwytów, gdy skończysz z okna dialogowego. Podczas korzystania z implementacji instalacji `CWinApp::OnFilePrintSetup`wydruku platformy dostarczone przez , nie trzeba zwolnić te uchwyty. Uchwyty są obsługiwane `CWinApp` przez i `CWinApp`są zwalniane w 's destrutor. Jest to konieczne tylko do uwolnienia `CPrintDialog` tych uchwytów podczas korzystania z autonomicznych.

Po zainicjowaniu kontrolek okna `DoModal` dialogowego należy wywołać funkcję elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na wybranie opcji drukowania. `DoModal`zwraca, czy użytkownik wybrał przycisk OK (IDOK) czy Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można `CPrintDialog`użyć jednej z funkcji członkowskich do pobierania informacji wejściowych przez użytkownika.

Funkcja `CPrintDialog::GetDefaults` elementu członkowskiego jest przydatna do pobierania bieżących ustawień domyślnych drukarki bez wyświetlania okna dialogowego. Ta funkcja elementu członkowskiego nie wymaga interakcji z użytkownikiem.

Za pomocą funkcji `CommDlgExtendedError` Systemu Windows można określić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji, zobacz SDK systemu Windows.

`CPrintDialog`opiera się na COMMDLG. DLL, który jest dostarczany z systemem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, wydziel klasę z `CPrintDialog`programu , podaj niestandardowy szablon okna dialogowego i dodaj mapę wiadomości, aby przetworzyć wiadomości powiadomień z rozszerzonych formantów. Wszelkie nieprzetworzene wiadomości powinny być przekazywane do klasy podstawowej. Dostosowywanie funkcji haka nie jest wymagane.

Aby przetworzyć tę samą wiadomość w różny sposób w zależności od tego, czy okno dialogowe to Ustawienia drukowania czy drukowanie, należy wyprowadzić klasę dla każdego okna dialogowego. Należy również zastąpić funkcję `AttachOnSetup` systemu Windows, która obsługuje tworzenie nowego okna dialogowego po wybraniu przycisku Ustawienia drukowania w oknie dialogowym Drukowanie.

Aby uzyskać więcej `CPrintDialog`informacji na temat używania programu , zobacz [Typowe klasy dialogów dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Konstruuje obiekt okna dialogowego Windows Print lub Print Setup.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Określa, czy jest wyświetlane standardowe okno dialogowe Drukowanie systemu Windows, czy Okno dialogowe Ustawienia drukowania. Ustaw ten parametr na WARTOŚĆ TRUE, aby wyświetlić standardowe okno dialogowe Ustawienia drukowania systemu Windows. Ustaw wartość FAŁSZ, aby wyświetlić okno dialogowe Drukowanie systemu Windows. Jeśli *bPrintSetupOnly* jest FALSE, przycisk opcji Ustawienia drukowania jest nadal wyświetlany w oknie dialogowym Drukowanie.

*Dwflags*<br/>
Co najmniej jedna flaga służy do dostosowywania ustawień okna dialogowego w połączeniu z operatorem or bitowym. Na przykład flaga PD_ALLPAGES ustawia domyślny zakres wydruku na wszystkie strony dokumentu. Zobacz [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) struktury w windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub okna właściciela okna okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego tylko konstruuje obiekt. Użyj `DoModal` funkcji elementu członkowskiego, aby wyświetlić okno dialogowe.

Należy zauważyć, że po wywołaniu konstruktora z *bPrintSetupOnly ustawiona* na FALSE, flaga PD_RETURNDC jest używana automatycznie. Po `DoModal`wywołaniu `GetDefaults` `GetPrinterDC`, lub , kontroler `m_pd.hDC`dc drukarki zostanie zwrócony w . Ten kontroler domeny musi zostać zwolniony za pomocą `CPrintDialog`wywołania [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) przez wywołującego .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Obsługa nowo utworzonego kontekstu urządzenia drukarki.

### <a name="remarks"></a>Uwagi

Przyjmuje się, że ten kontroler domeny drukarki jest bieżącym kontrolerem domeny drukarki, a każdy inny wcześniej uzyskany kontroler domeny drukarki musi zostać usunięty przez użytkownika. Tę funkcję można wywołać, a wynikowy kontroler domeny był używany bez wyświetlania okna dialogowego Drukowanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModal

Wyświetla typowe okno dialogowe drukowania systemu Windows i umożliwia użytkownikowi wybranie różnych opcji drukowania, takich jak liczba kopii, zakres stron i to, czy kopie powinny być sortowane.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli funkcja IDCANCEL jest zwracana, należy wywołać funkcję Programu Windows [CommDlgExtendedError,](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL to stałe wskazujące, czy użytkownik wybrał przycisk OK, czy Anuluj.

### <a name="remarks"></a>Uwagi

Aby zainicjować różne opcje okna dialogowego drukowania, ustawiając elementy `m_pd` członkowskie `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Po `DoModal`wywołaniu programu można wywołać inne funkcje członkowskie w celu pobrania ustawień lub informacji wprowadzonych przez użytkownika w oknie dialogowym.

Należy zauważyć, że po wywołaniu konstruktora z *bPrintSetupOnly ustawiona* na FALSE, flaga PD_RETURNDC jest używana automatycznie. Po `DoModal`wywołaniu `GetDefaults` `GetPrinterDC`, lub , kontroler `m_pd.hDC`dc drukarki zostanie zwrócony w . Ten kontroler domeny musi zostać zwolniony za pomocą `CPrintDialog`wywołania [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) przez wywołującego .

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::CreatePrinterDC](#createprinterdc).

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies

Pobiera liczbę żądanych kopii.

```
int GetCopies() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba żądanych kopii.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać liczbę żądanych kopii.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults

Pobiera domyślne ustawienia urządzenia drukarki domyślnej bez wyświetlania okna dialogowego.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobrane wartości są umieszczane w `m_pd` strukturze.

W niektórych przypadkach wywołanie tej funkcji wywoła `CPrintDialog` [konstruktora](#cprintdialog) z *bPrintSetupOnly ustawiona* na FALSE. W takich przypadkach drukarka `hDevNames` `hDevMode` DC i (dwa `m_pd` uchwyty znajdujące się w człodzielni danych) są przydzielane automatycznie.

Jeśli konstruktor `CPrintDialog` dla został wywołany z *bPrintSetupOnly ustawiona* `hDevMode` na `m_pd.hDevNames` FALSE, ta funkcja nie tylko powróci `hDevNames` i `m_pd.hDC`znajduje się w i `m_pd.hDevMode`) do obiektu wywołującego, ale także zwróci kontrolera domeny drukarki w . Jest odpowiedzialny za obiekt wywołujący, aby usunąć kontroler domeny drukarki i wywołać funkcję Windows `CPrintDialog` [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na uchwytach po zakończeniu z obiektem.

### <a name="example"></a>Przykład

Ten fragment kodu pobiera domyślny kontekst urządzenia drukarki i zgłasza użytkownikowi rozdzielczość drukarki w punktach na cal. (Ten atrybut możliwości drukarki jest często określany jako DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName

Pobiera nazwę aktualnie wybranego urządzenia drukarki.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranej drukarki.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji po wywołaniu [DoModal,](#domodal) aby pobrać nazwę aktualnie wybranej drukarki lub po wywołaniu [GetDefaults,](#getdefaults) aby pobrać bieżące domyślne ustawienia domyślne urządzenia drukarki domyślnej. Użyj wskaźnika `CString` do obiektu `GetDeviceName` zwróconego `lpszDeviceName` jako wartość w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

Ten fragment kodu zawiera domyślną nazwę drukarki użytkownika i port, do którego jest podłączony, wraz z nazwą buforu używana przez drukarkę. Kod może wyświetlać okno komunikatu z napisem "Domyślną \\drukarką jest HP LaserJet IIIP na \server\share przy użyciu winspool.", na przykład.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode

Pobiera strukturę. `DEVMODE`

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura danych [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) która zawiera informacje o inicjowaniu urządzenia i środowisku sterownika wydruku. Należy odblokować pamięć pobraną przez tę strukturę za pomocą funkcji Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) która jest opisana w sdk systemu Windows.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać informacje o urządzeniu drukującym.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName

Pobiera nazwę aktualnie wybranego sterownika drukarki.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określanie nazwy sterownika zdefiniowanej przez system.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać nazwę sterownika urządzenia drukarki zdefiniowanej przez system. Użyj wskaźnika `CString` do obiektu `GetDriverName` zwróconego `lpszDriverName` jako wartość w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetFromPage

Pobiera stronę początkową zakresu wydruku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer strony początkowej w zakresie stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać numer strony początkowej w zakresie stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName

Pobiera nazwę aktualnie wybranego portu drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego portu drukarki.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać nazwę aktualnie wybranego portu drukarki.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Pobiera dojście do kontekstu urządzenia drukarki.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia drukarki, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli parametr *bPrintSetupOnly* `CPrintDialog` konstruktora miał wartość FAŁSZ (wskazując, `GetPrinterDC` że jest wyświetlane okno dialogowe Drukowanie), zwraca dojście do kontekstu urządzenia drukarki. Należy wywołać funkcję [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) systemu Windows, aby usunąć kontekst urządzenia po zakończeniu korzystania z niego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage

Pobiera końcową stronę zakresu wydruku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer strony zakończenia w zakresie stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać numer strony zakończenia w zakresie stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a>CPrintDialog::m_pd

Struktura, której członkowie przechowują właściwości obiektu okna dialogowego.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CPrintDialog` obiektu, można `m_pd` użyć, aby ustawić różne aspekty okna dialogowego przed wywołaniem Funkcji elementu członkowskiego [DoModal.](#domodal) Aby uzyskać więcej `m_pd` informacji na temat struktury, zobacz [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) w windows SDK.

Jeśli zmodyfikujesz `m_pd` element członkowski danych bezpośrednio, należy zastąpić wszelkie domyślne zachowanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll

Określa, czy mają być drukowane wszystkie strony dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wszystkie strony w dokumencie mają być wydrukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy mają być drukowane wszystkie strony w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate

Określa, czy wymagane są posortowane kopie.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wybierze pole wyboru sortowania w oknie dialogowym; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy drukarka powinna zestawić wszystkie drukowane kopie dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange

Określa, czy mają być drukowane tylko określony zakres stron.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli mają być drukowane tylko różne strony w dokumencie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy wydrukować tylko zakres stron w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PzmarszczekWyborzowanie

Określa, czy mają być drukowane tylko aktualnie zaznaczone elementy.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli mają być drukowane tylko wybrane elementy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy drukować tylko aktualnie wybrane elementy.

### <a name="example"></a>Przykład

  Zobacz przykład [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Zobacz też

[Przykładowy DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
