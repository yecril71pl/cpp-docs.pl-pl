---
title: Klasa CPrintDialogEx
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 79d696f89ca7474220559abbf5464f32b6e684c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543328"
---
# <a name="cprintdialogex-class"></a>Klasa CPrintDialogEx

Hermetyzuje usługi świadczone przez arkusz własności drukowania Windows.

## <a name="syntax"></a>Składnia

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Konstruuje `CPrintDialogEx` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki, bez wyświetlania okna dialogowego drukowania.|
|[CPrintDialogEx::DoModal](#domodal)|Zostanie wyświetlone okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[CPrintDialogEx::GetCopies](#getcopies)|Pobiera liczbę kopii żądanie.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Pobiera ustawienia domyślne urządzenia bez wyświetlania okna dialogowego.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Pobiera nazwę drukarki aktualnie wybranego urządzenia.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Pobiera `DEVMODE` struktury.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Pobiera nazwę sterownika drukarki zdefiniowaną przez system.|
|[CPrintDialogEx::GetPortName](#getportname)|Pobiera nazwę portu aktualnie wybranego drukarki.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Pobiera uchwyt do kontekstu urządzenia drukarki.|
|[CPrintDialogEx::PrintAll](#printall)|Określa, czy umożliwia wydrukowanie wszystkich stron dokumentu.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Określa, czy sortowane są żądane kopii.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Określa, czy należy wydrukować bieżącą stronę dokumentu.|
|[CPrintDialogEx::PrintRange](#printrange)|Określa, czy do drukowania określony zakres stron.|
|[CPrintDialogEx::PrintSelection](#printselection)|Określa, czy drukować tylko aktualnie wybrane elementy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktury używane w celu dostosowania `CPrintDialogEx` obiektu.|

## <a name="remarks"></a>Uwagi

Możesz polegać na platformę, by obsłużyć wiele aspektów proces drukowania dla danej aplikacji. Aby uzyskać więcej informacji o używaniu platformę do obsługi zadań drukowania, zobacz artykuł [drukowania](../../mfc/printing.md).

Jeśli chcesz, aby aplikacja obsługiwała drukowanie bez angażowania struktury, możesz użyć `CPrintDialogEx` klasy "w jakim jest" za pomocą konstruktora przewidzianej lub może pochodzić własne klasy okien dialogowych z `CPrintDialogEx` i zapisywanie konstruktora do własnych potrzeb. W obu przypadkach tych okien dialogowych będą zachowywać się jak standardowego okna dialogowe MFC, ponieważ są pochodnymi klasy `CCommonDialog`.

Aby użyć `CPrintDialogEx` obiektów, najpierw utwórz obiekt przy użyciu `CPrintDialogEx` konstruktora. Gdy okno dialogowe został skonstruowany, można ustawić lub zmodyfikować dowolne wartości na [m_pdex](#m_pdex) strukturę, aby zainicjować wartości formantów w oknie dialogowym. `m_pdex` Struktury jest typu [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa). Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.

Jeśli nie podasz własne dojść w `m_pdex` dla `hDevMode` i `hDevNames` członków, pamiętaj wywołać funkcję Windows `GlobalFree` dla te dojścia, gdy są wykonywane za pomocą okna dialogowego.

Po inicjalizacji formantów okna dialogowego, należy wywołać `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. Gdy `DoModal` zwraca, można określić, czy użytkownik wybrał przycisk OK, Zastosuj lub przycisk Anuluj.

Jeśli użytkownik nacisnął klawisz OK, możesz użyć `CPrintDialogEx`przez funkcje Członkowskie można pobrać informacji o danych wejściowych przez użytkownika.

`CPrintDialogEx::GetDefaults` Funkcja członkowska jest przydatne do pobierania bieżące ustawienia domyślne drukarki bez wyświetlania okna dialogowego. Ta metoda nie wymaga interakcji użytkownika.

Możesz użyć Windows `CommDlgExtendedError` funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i Dowiedz się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji zobacz zestaw Windows SDK.

Aby uzyskać więcej informacji na temat korzystania z `CPrintDialogEx`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

Tworzy arkusz własności drukowania Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Co najmniej jeden flagi, których można użyć, aby dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Na przykład flaga PD_ALLPAGES ustawia domyślny zakres wydruku dla wszystkich stron dokumentu. Zobacz [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) struktury w zestawie Windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego tylko tworzy obiekt. Użyj `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe.

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

Tworzy kontekst urządzenia drukarki (DC) na podstawie [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia nowo utworzoną drukarkę.

### <a name="remarks"></a>Uwagi

Zwrócone kontrolera domeny także są przechowywane w `hDC` członkiem [m_pdex](#m_pdex).

Ten kontroler domeny jest zakłada się, że bieżąca drukarka kontrolera domeny, a inne zostały wcześniej uzyskane drukarki, które kontrolery domeny muszą zostać usunięte. Ta funkcja może zostać wywołana, a wynikowy DC określono, nigdy nie wyświetlania okna dialogowego drukowania.

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

Wywołaj tę funkcję, aby wyświetlić arkusz własności drukowania Windows i Zezwalaj użytkownikowi na wybranie różnych opcji drukowania, takich jak liczba kopii, zakres stron oraz tego, czy mają być sortowane kopii.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

INT_PTR zwracana wartość jest faktycznie HRESULT. Zobacz sekcję zwracają wartości w [PrintDlgEx](https://msdn.microsoft.com/library/windows/desktop/ms646942) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne opcje Okno dialogowe drukowania, ustawiając członkowie `m_pdex` struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Po wywołaniu `DoModal`, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

Jeśli flaga PD_RETURNDC jest używany podczas wywoływania `DoModal`, drukarki kontrolera domeny, które zostaną zwrócone w `hDC` członkiem [m_pdex](#m_pdex). Ten kontroler domeny musi być zwolniona przez wywołanie [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) przez obiekt wywołujący `CPrintDialogEx`.

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

Wywołaj tę funkcję, po wywołaniu `DoModal` można pobrać liczby kopii żądane.

```
int GetCopies() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kopii żądanie.

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

Wywołaj tę funkcję, aby pobrać ustawienia domyślne urządzenia drukarki domyślnej bez wyświetlania okna dialogowego.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie, w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Tworzy kontekst urządzenia drukarki (DC) na podstawie [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.

`GetDefaults` nie są wyświetlane arkusz własności drukowania. Zamiast ustawia `hDevNames` i `hDevMode` członkowie [m_pdex](#m_pdex) do dojścia do [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktur, które są inicjowane dla drukarka domyślna systemu. Zarówno `hDevNames` i `hDevMode` musi mieć wartość NULL, lub `GetDefaults` zakończy się niepowodzeniem.

Jeśli ustawiona jest flaga PD_RETURNDC, ta funkcja nie zwróci jedynie `hDevNames` i `hDevMode` (znajdujący się w `m_pdex.hDevNames` i `m_pdex.hDevMode`) do obiektu wywołującego, ale zwróci drukarkę kontrolera domeny w `m_pdex.hDC`. Jest odpowiedzialny za obiekt wywołujący, aby usunąć drukarki kontrolera domeny, a następnie wywołać Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) funkcja obsługuje po zakończeniu `CPrintDialogEx` obiektu.

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) można pobrać nazwę aktualnie wybranej drukarki lub po wywołaniu [GetDefaults](#getdefaults) pobrać nazwy zostanie użyta drukarka domyślna.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego drukarki.

### <a name="remarks"></a>Uwagi

Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDeviceName` jako wartość `lpszDeviceName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać informacji o urządzeniu drukowania.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury danych, który zawiera informacje na temat inicjowania urządzenia i środowisko sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) funkcji, która jest opisana w zestawie Windows SDK.

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać nazwę sterownika drukarki zdefiniowaną przez system.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określający nazwę sterownika zdefiniowaną przez system.

### <a name="remarks"></a>Uwagi

Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość *lpszDriverName* w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

Wywołaj tę funkcję, po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) pobrać nazwy portu aktualnie wybranego drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa portu aktualnie wybranego drukarki.

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

Zwraca uchwyt do kontekstu urządzenia drukarki.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia drukarki.

### <a name="remarks"></a>Uwagi

Należy wywołać Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) funkcję, aby usunąć kontekst urządzenia, po zakończeniu korzystania z niego.

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Struktura PRINTDLGEX, której członkowie przechowywania właściwości obiektu okna dialogowego.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Uwagi

Po konstruowanie `CPrintDialogEx` obiektu, możesz użyć `m_pdex` można ustawić różne aspekty okno dialogowe przed wywołaniem [DoModal](#domodal) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat `m_pdex` struktury, zobacz [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) w zestawie Windows SDK.

Jeśli zmodyfikujesz `m_pdex` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy umożliwia wydrukowanie wszystkich stron w dokumencie.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli wszystkich stron w dokumencie mają być drukowane; w przeciwnym razie wartość FALSE.

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy drukarka powinna sortować wszystkie kopie dokumentu.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli użytkownik wybierze collate pole wyboru w oknie dialogowym. w przeciwnym razie wartość FALSE.

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

Wywołaj tę funkcję, po wywołaniu `DoModal` do ustalenia, czy należy wydrukować bieżącą stronę w dokumencie.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli **wydrukować bieżącą stronę** jest wybrana w oknie dialogowym drukowania; w przeciwnym razie wartość FALSE.

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy drukowanie szeroką gamę stron w dokumencie.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli tylko zakres stron w dokumencie mają być drukowane; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Zakresy określonej strony można ustalić na podstawie [m_pdex](#m_pdex) (zobacz `nPageRanges`, `nMaxPageRanges`, i `lpPageRanges` w [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) struktury w zestawie Windows SDK).

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

Wywołaj tę funkcję, po wywołaniu `DoModal` do określenia, czy można drukować tylko aktualnie wybrane elementy.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli tylko wybrane elementy mają być drukowane; w przeciwnym razie wartość FALSE.

## <a name="see-also"></a>Zobacz też

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
