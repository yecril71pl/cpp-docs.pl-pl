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
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741361"
---
# <a name="cprintdialog-class"></a>Klasa CPrintDialog

Hermetyzuje usługi zapewniane przez wspólne okno dialogowe systemu Windows do drukowania.

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
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki bez wyświetlania okna dialogowego Drukuj.|
|[CPrintDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi wybranie.|
|[CPrintDialog:: getkopiującs](#getcopies)|Pobiera żądaną liczbę kopii.|
|[CPrintDialog:: GetDefaults](#getdefaults)|Pobiera wartości domyślne urządzenia bez wyświetlania okna dialogowego.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Pobiera nazwę aktualnie wybranego urządzenia drukarki.|
|[CPrintDialog:: getdevmode](#getdevmode)|`DEVMODE` Pobiera strukturę.|
|[CPrintDialog::GetDriverName](#getdrivername)|Pobiera nazwę aktualnie wybranego sterownika drukarki.|
|[CPrintDialog::GetFromPage](#getfrompage)|Pobiera stronę początkową zakresu wydruku.|
|[CPrintDialog:: GetPortName](#getportname)|Pobiera nazwę aktualnie wybranego portu drukarki.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Pobiera uchwyt do kontekstu urządzenia drukarki.|
|[CPrintDialog::GetToPage](#gettopage)|Pobiera stronę końcową zakresu wydruku.|
|[CPrintDialog::PrintAll](#printall)|Określa, czy wydrukować wszystkie strony dokumentu.|
|[CPrintDialog::P rintCollate](#printcollate)|Określa, czy posortowane kopie są wymagane.|
|[CPrintDialog::PrintRange](#printrange)|Określa, czy drukować tylko określony zakres stron.|
|[CPrintDialog::P rintSelection](#printselection)|Określa, czy drukować tylko aktualnie wybrane elementy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktura używana do dostosowywania `CPrintDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Wspólne okna dialogowe drukowania zapewniają łatwy sposób implementacji okien dialogowych konfiguracji drukowania i drukowania w sposób zgodny ze standardami systemu Windows.

> [!NOTE]
>  `CPrintDialogEx` Klasa hermetyzuje usługi udostępniane przez arkusz właściwości drukowania systemu Windows. Aby uzyskać więcej informacji, zobacz Omówienie [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .

`CPrintDialog`Funkcja jest zastępowana przez wersję [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), która została zaprojektowana w celu zapewnienia wspólnego okna dialogowego zarówno dla konfiguracji drukowania, jak i ustawień strony.

Możesz polegać na architekturze do obsługi wielu aspektów procesu drukowania aplikacji. W takim przypadku struktura automatycznie wyświetla okno dialogowe typowe systemu Windows do drukowania. Istnieje również możliwość drukowania uchwytu Framework dla aplikacji, ale zastępowanie wspólnego okna dialogowego drukowania przy użyciu własnego okna dialogowego Drukuj. Aby uzyskać więcej informacji o używaniu struktury do obsługi zadań drukowania, zobacz artykuł [Drukowanie](../../mfc/printing.md)artykułu.

Jeśli chcesz, aby aplikacja obsługiwała drukowanie bez zaangażowania platformy, możesz użyć `CPrintDialog` klasy "AS IS" z dostarczonym konstruktorem lub można utworzyć własną klasę dialogową z `CPrintDialog` i napisać konstruktora zgodnie z potrzebami. W obu przypadkach te okna dialogowe będą zachowywać się jak standardowe okna dialogowe MFC, ponieważ pochodzą z klasy `CCommonDialog`.

Aby użyć `CPrintDialog` obiektu, należy najpierw utworzyć obiekt `CPrintDialog` przy użyciu konstruktora. Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować wszystkie wartości w strukturze [m_pd](#m_pd) , aby zainicjować wartości kontrolek okna dialogowego. Struktura jest typu PRINTDLG. [](/windows/win32/api/commdlg/ns-commdlg-printdlga) `m_pd` Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Jeśli nie podasz `m_pd` własnych uchwytów `hDevMode` dla elementów i `hDevNames` , pamiętaj, aby wywołać funkcję `GlobalFree` systemu Windows dla tych dojść po zakończeniu pracy z oknem dialogowym. W przypadku korzystania z implementacji konfiguracji wydruku struktury dostarczonej `CWinApp::OnFilePrintSetup`przez program nie trzeba zwalniać tych dojść. Uchwyty są obsługiwane przez `CWinApp` program i są zwalniane z `CWinApp`destruktora. Jest to konieczne tylko w przypadku korzystania `CPrintDialog` z autonomicznej usługi.

Po zainicjowaniu kontrolek okna dialogowego Wywołaj `DoModal` funkcję członkowską, aby wyświetlić okno dialogowe i umożliwić użytkownikowi wybranie opcji drukowania. `DoModal`Zwraca czy użytkownik zaznaczył przycisk OK (IDOK) lub Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można użyć jednej z `CPrintDialog`funkcji Członkowskich, aby pobrać informacje wprowadzane przez użytkownika.

Funkcja `CPrintDialog::GetDefaults` członkowska jest przydatna do pobierania bieżących wartości domyślnych drukarki bez wyświetlania okna dialogowego. Ta funkcja członkowska nie wymaga interakcji ze strony użytkownika.

Możesz użyć funkcji systemu Windows `CommDlgExtendedError` , aby określić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji, zobacz Windows SDK.

`CPrintDialog`opiera się na COMMDLG. Plik DLL, który jest dostarczany z systemem Windows w wersji 3,1 lub nowszej.

Aby dostosować okno dialogowe, wyprowadzić klasę z `CPrintDialog`, udostępnić niestandardowy szablon okna dialogowego i dodać mapę komunikatów do przetwarzania komunikatów powiadomień z formantów rozszerzonych. Wszystkie nieprzetworzone komunikaty powinny zostać przesłane do klasy podstawowej. Dostosowywanie funkcji Hook nie jest wymagane.

Aby przetwarzać ten sam komunikat w różny sposób, w zależności od tego, czy okno dialogowe jest w trakcie drukowania lub drukowania, należy utworzyć klasę dla każdego okna dialogowego. Należy również zastąpić funkcję systemu Windows `AttachOnSetup` , która obsługuje tworzenie nowego okna dialogowego po wybraniu przycisku Ustawienia wydruku w oknie dialogowym drukowania.

Aby uzyskać więcej informacji na `CPrintDialog`temat korzystania z programu, zobacz [wspólne klasy okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

##  <a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Tworzy obiekt okna dialogowego konfiguracji drukowania lub drukowania systemu Windows.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Określa, czy wyświetlane jest standardowe okno dialogowe drukowania systemu Windows lub ustawienia wydruku. Ustaw ten parametr na wartość TRUE, aby wyświetlić okno dialogowe Standardowa konfiguracja drukowania systemu Windows. Ustaw na wartość FALSE, aby wyświetlić okno dialogowe drukowania systemu Windows. Jeśli *bPrintSetupOnly* ma wartość false, przycisk opcji konfiguracji drukowania jest nadal wyświetlany w oknie dialogowym drukowania.

*flagiDW*<br/>
Jedna lub więcej flag, których można użyć, aby dostosować ustawienia okna dialogowego połączone przy użyciu operatora bitowego or. Na przykład flaga PD_ALLPAGES ustawia domyślny zakres drukowania na wszystkie strony dokumentu. Zapoznaj się ze strukturą [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) w Windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna dialogowego nadrzędnego lub właściciela.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska tylko konstruuje obiekt. Użyj funkcji `DoModal` członkowskiej, aby wyświetlić okno dialogowe.

Należy pamiętać, że po wywołaniu konstruktora z *bPrintSetupOnly* ustawionym na false, flaga PD_RETURNDC jest używana automatycznie. Po wywołaniu `DoModal`, `GetDefaults`lub `GetPrinterDC`, w programie `m_pd.hDC`zostanie zwrócony kontroler domeny. Ten kontroler domeny musi zostać zwolniony z wywołaniem [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) przez obiekt wywołujący `CPrintDialog`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki (DC) dla struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonego kontekstu urządzenia drukarki.

### <a name="remarks"></a>Uwagi

Przyjęto, że kontroler domeny jest bieżącym kontrolerem domeny, a wszystkie inne wcześniej uzyskane kontrolery domeny muszą zostać usunięte przez użytkownika. Ta funkcja może być wywoływana, a wynikający z niego używany kontroler domeny bez wyświetlania okna dialogowego Drukuj.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>CPrintDialog::D oModal

Wyświetla okno dialogowe typowy wydruk systemu Windows i umożliwia użytkownikowi wybranie różnych opcji drukowania, takich jak liczba kopii, zakres stron i czy kopie mają być sortowane.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli IDCANCEL jest zwracany, wywołaj funkcję Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) , aby określić, czy wystąpił błąd.

IDOK i IDCANCEL są stałymi, które wskazują, czy użytkownik zaznaczył przycisk OK lub Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne opcje okna dialogowego drukowania przez ustawienie elementów członkowskich `m_pd` struktury, należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Po wywołaniu `DoModal`można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe użytkownika w oknie dialogowym.

Należy pamiętać, że po wywołaniu konstruktora z *bPrintSetupOnly* ustawionym na false, flaga PD_RETURNDC jest używana automatycznie. Po wywołaniu `DoModal`, `GetDefaults`lub `GetPrinterDC`, w programie `m_pd.hDC`zostanie zwrócony kontroler domeny. Ten kontroler domeny musi zostać zwolniony z wywołaniem [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) przez obiekt wywołujący `CPrintDialog`.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>CPrintDialog:: getkopiującs

Pobiera żądaną liczbę kopii.

```
int GetCopies() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba żądanych kopii.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby pobrać żądaną liczbę kopii.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdefaults"></a>CPrintDialog:: GetDefaults

Pobiera wartości domyślne urządzenia drukarki domyślnej bez wyświetlania okna dialogowego.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobrane wartości są umieszczane w `m_pd` strukturze.

W niektórych przypadkach wywołanie tej funkcji wywoła [Konstruktor](#cprintdialog) dla elementu `CPrintDialog` with *bPrintSetupOnly* o wartości false. W takich przypadkach jest automatycznie przypisywany kontroler `hDevNames` domeny `hDevMode` i i ( `m_pd` dwa uchwyty znajdujące się w składowej danych).

Jeśli Konstruktor `CPrintDialog` dla został wywołany atrybutem *bPrintSetupOnly* o wartości false, ta funkcja nie tylko zwróci `hDevNames` i `hDevMode` znajduje się `m_pd.hDevNames` w `m_pd.hDevMode`i) do obiektu wywołującego, ale zwróci również kontroler domeny drukarki w `m_pd.hDC`. Obiekt wywołujący jest odpowiedzialny za usunięcie kontrolera domeny drukarki i wywołanie funkcji [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) systemu Windows na uchwytach po zakończeniu pracy z `CPrintDialog` obiektem.

### <a name="example"></a>Przykład

Ten fragment kodu pobiera kontekst urządzenia drukarki domyślnej i raportuje użytkownika do rozdzielczości drukarki w punktach na cal. (Ten atrybut funkcji drukarki jest często określany mianem DPI).

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>CPrintDialog:: GetDeviceName

Pobiera nazwę aktualnie wybranego urządzenia drukarki.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie zaznaczonej drukarki.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po wywołaniu [DoModal](#domodal) , aby pobrać nazwę aktualnie wybranej drukarki, lub po wywołaniu metody [GetDefaults](#getdefaults) , aby pobrać bieżące wartości domyślne urządzenia drukarki domyślnej. Użyj wskaźnika do `CString` obiektu zwróconego przez `GetDeviceName` jako wartość `lpszDeviceName` w wywołaniu metody [przechwytywania:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

Ten fragment kodu przedstawia domyślną nazwę drukarki użytkownika i port, z którym jest połączona, wraz z nazwą buforu używaną przez drukarkę. W kodzie może zostać wyświetlone okno komunikatu "drukarka domyślna to HP LaserJet IIIP na \\\server\share przy użyciu winspool".

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>CPrintDialog:: getdevmode

`DEVMODE` Pobiera strukturę.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura danych [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , która zawiera informacje o inicjalizacji i środowisku urządzenia sterownika drukarki. Należy odblokować pamięć wykonywaną przez tę strukturę przy użyciu funkcji [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) systemu Windows, która jest opisana w Windows SDK.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) , aby pobrać informacje o urządzeniu drukującym.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdrivername"></a>CPrintDialog:: GetDriverName

Pobiera nazwę aktualnie wybranego sterownika drukarki.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

`CString` Określanie nazwy sterownika zdefiniowanej przez system.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) , aby pobrać nazwę sterownika urządzenia drukarki zdefiniowanej przez system. Użyj wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu metody [przechwytywania:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>CPrintDialog::GetFromPage

Pobiera stronę początkową zakresu wydruku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer strony początkowej z zakresu stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby pobrać numer strony początkowej z zakresu stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: m_pd](#m_pd).

##  <a name="getportname"></a>CPrintDialog:: GetPortName

Pobiera nazwę aktualnie wybranego portu drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego portu drukarki.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) , aby pobrać nazwę aktualnie wybranego portu drukarki.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Pobiera uchwyt do kontekstu urządzenia drukarki.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia drukarki, jeśli powodzenie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CPrintDialog` parametr *bPrintSetupOnly* konstruktora miał wartość false (wskazuje, że `GetPrinterDC` wyświetlane jest okno dialogowe drukowania), zwraca uchwyt do kontekstu urządzenia drukarki. Należy wywołać funkcję [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) systemu Windows, aby usunąć kontekst urządzenia po jego zakończeniu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>CPrintDialog::GetToPage

Pobiera stronę końcową zakresu wydruku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer strony końcowej z zakresu stron do wydrukowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby pobrać końcowy numer strony z zakresu stron do wydrukowania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: m_pd](#m_pd).

##  <a name="m_pd"></a>CPrintDialog::m_pd

Struktura, której członkowie przechowują charakterystykę obiektu okna dialogowego.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CPrintDialog` obiektu można użyć `m_pd` , aby ustawić różne aspekty okna dialogowego przed wywołaniem funkcji składowej [DoModal](#domodal) . Aby uzyskać więcej informacji na `m_pd` temat struktury, zobacz [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) w Windows SDK.

W `m_pd` przypadku zmodyfikowania elementu członkowskiego danych należy zmienić zachowanie domyślne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>CPrintDialog::P rintAll

Określa, czy wydrukować wszystkie strony dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wszystkie strony w dokumencie mają być drukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby określić, czy wydrukować wszystkie strony w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: m_pd](#m_pd).

##  <a name="printcollate"></a>CPrintDialog::P rintCollate

Określa, czy posortowane kopie są wymagane.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wybierze pole wyboru COLLATE w oknie dialogowym. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby określić, czy drukarka ma sortować wszystkie wydrukowane kopie dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>CPrintDialog::P rintRange

Określa, czy drukować tylko określony zakres stron.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli tylko zakres stron w dokumencie ma być drukowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby określić, czy drukować tylko zakres stron w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: m_pd](#m_pd).

##  <a name="printselection"></a>CPrintDialog::P rintSelection

Określa, czy drukować tylko aktualnie wybrane elementy.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli tylko wybrane elementy mają być drukowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po `DoModal` wywołaniu, aby określić, czy drukować tylko aktualnie wybrane elementy.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPrintDialog:: m_pd](#m_pd).

## <a name="see-also"></a>Zobacz także

[Przykład DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
