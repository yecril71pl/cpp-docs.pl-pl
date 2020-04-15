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
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364040"
---
# <a name="cprintdialogex-class"></a>Klasa CPrintDialogEx

Hermetyzuje usługi świadczone przez arkusz właściwości Windows Print.

## <a name="syntax"></a>Składnia

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Konstruuje `CPrintDialogEx` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki bez wyświetlania okna dialogowego Drukowanie.|
|[CPrintDialogEx::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonywanie wyborów.|
|[CPrintDialogEx::GetCopies](#getcopies)|Pobiera liczbę żądanych kopii.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Pobiera ustawienia domyślne urządzenia bez wyświetlania okna dialogowego.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Pobiera nazwę aktualnie wybranego urządzenia drukarki.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Pobiera strukturę. `DEVMODE`|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Pobiera nazwę sterownika urządzenia drukarki zdefiniowanej przez system.|
|[CPrintDialogEx::GetPortName](#getportname)|Pobiera nazwę aktualnie wybranego portu drukarki.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Pobiera dojście do kontekstu urządzenia drukarki.|
|[CPrintDialogEx::PrintAll](#printall)|Określa, czy mają być drukowane wszystkie strony dokumentu.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Określa, czy wymagane są posortowane kopie.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Określa, czy ma być drukowana bieżąca strona dokumentu.|
|[CPrintDialogEx::PrintRange](#printrange)|Określa, czy mają być drukowane tylko określony zakres stron.|
|[CPrintDialogEx::PrintSelection](#printselection)|Określa, czy mają być drukowane tylko aktualnie zaznaczone elementy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktura używana do dostosowywania `CPrintDialogEx` obiektu.|

## <a name="remarks"></a>Uwagi

Można polegać na platformie do obsługi wielu aspektów procesu drukowania dla aplikacji. Aby uzyskać więcej informacji na temat używania struktury do obsługi zadań drukowania, zobacz artykuł [Drukowanie](../../mfc/printing.md).

Jeśli chcesz, aby aplikacja do obsługi drukowania bez zaangażowania `CPrintDialogEx` struktury, można użyć klasy "tak, jak jest" z `CPrintDialogEx` konstruktora pod warunkiem, lub można wyprowadzić własną klasę okna dialogowego z i napisać konstruktora do własnych potrzeb. W obu przypadkach te okna dialogowe będą zachowywać się jak standardowe `CCommonDialog`okna dialogowe MFC, ponieważ pochodzą z klasy .

Aby użyć `CPrintDialogEx` obiektu, należy najpierw `CPrintDialogEx` utworzyć obiekt przy użyciu konstruktora. Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować dowolne wartości w strukturze [m_pdex,](#m_pdex) aby zainicjować wartości formantów okna dialogowego. Struktura `m_pdex` jest typu [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Jeśli nie podasz własnych uchwytów `m_pdex` `hDevMode` dla `hDevNames` i członków, należy wywołać funkcję `GlobalFree` systemu Windows dla tych uchwytów, gdy skończysz z okna dialogowego.

Po zainicjowaniu kontrolek okna `DoModal` dialogowego należy wywołać funkcję elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na wybranie opcji drukowania. Po `DoModal` zwróceniu można określić, czy użytkownik wybrał przycisk OK, Zastosuj lub Anuluj.

Jeśli użytkownik naciśnięty przycisk `CPrintDialogEx`OK, można użyć funkcji członkowskich do pobierania informacji wprowadzanych przez użytkownika.

Funkcja `CPrintDialogEx::GetDefaults` elementu członkowskiego jest przydatna do pobierania bieżących ustawień domyślnych drukarki bez wyświetlania okna dialogowego. Ta metoda nie wymaga interakcji z użytkownikiem.

Za pomocą funkcji `CommDlgExtendedError` Systemu Windows można określić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji, zobacz SDK systemu Windows.

Aby uzyskać więcej `CPrintDialogEx`informacji na temat używania programu , zobacz [Typowe klasy dialogów dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Konstruuje arkusz właściwości Drukowanie systemu Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Co najmniej jedna flaga służy do dostosowywania ustawień okna dialogowego w połączeniu z operatorem or bitowym. Na przykład flaga PD_ALLPAGES ustawia domyślny zakres wydruku na wszystkie strony dokumentu. Zobacz [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) struktury w windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub okna właściciela okna okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego tylko konstruuje obiekt. Użyj `DoModal` funkcji elementu członkowskiego, aby wyświetlić okno dialogowe.

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialogEx::CreatePrinterDC

Tworzy kontekst urządzenia drukarki (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Obsługa nowo utworzonego kontekstu urządzenia drukarki.

### <a name="remarks"></a>Uwagi

Zwrócony kontroler domeny jest `hDC` również przechowywany w [m_pdex](#m_pdex).

Przyjmuje się, że ten kontroler domeny drukarki jest bieżącym kontrolerem domeny drukarki, a wszystkie inne wcześniej uzyskane kontrolery domeny drukarki muszą zostać usunięte. Tę funkcję można wywołać, a wynikowy kontroler domeny był używany bez wyświetlania okna dialogowego Drukowanie.

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::DoModal

Wywołanie tej funkcji, aby wyświetlić arkusz właściwości Drukowanie systemu Windows i zezwolić użytkownikowi na wybranie różnych opcji drukowania, takich jak liczba kopii, zakres stron i to, czy kopie powinny być sortowane.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zwrotu INT_PTR jest w rzeczywistości HRESULT. Zobacz sekcję Wartości zwracane w [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) w programie Windows SDK.

### <a name="remarks"></a>Uwagi

Aby zainicjować różne opcje okna dialogowego drukowania, ustawiając elementy `m_pdex` członkowskie `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Po `DoModal`wywołaniu programu można wywołać inne funkcje członkowskie w celu pobrania ustawień lub informacji wprowadzonych przez użytkownika w oknie dialogowym.

Jeśli podczas wywoływania `DoModal`używana jest flaga PD_RETURNDC, kontroler `hDC` domeny drukarki zostanie [zwrócony](#m_pdex)w m_pdex . Ten kontroler domeny musi zostać zwolniony za pomocą `CPrintDialogEx`wywołania [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) przez wywołującego .

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrintDialogEx::GetCopies

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać liczbę żądanych kopii.

```
int GetCopies() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba żądanych kopii.

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrintDialogEx::GetDefaults

Wywołanie tej funkcji, aby pobrać domyślne ustawienia domyślne urządzenia drukarki domyślnej bez wyświetlania okna dialogowego.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tworzy kontekst urządzenia drukarki (DC) ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

`GetDefaults`nie wyświetla arkusza właściwości Drukuj. Zamiast tego ustawia `hDevNames` i `hDevMode` członków [m_pdex](#m_pdex) do obsługi [devmode](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) struktur, które są inicjowane dla domyślnej drukarki systemu. Zarówno `hDevNames` `hDevMode` i musi być `GetDefaults` null lub kończy się niepowodzeniem.

Jeśli ustawiona jest flaga PD_RETURNDC, ta `hDevNames` funkcja `hDevMode` nie `m_pdex.hDevNames` tylko `m_pdex.hDevMode`powróci i (znajduje się w i) `m_pdex.hDC`do osoby dzwoniącej, ale także zwróci kontroler prądu stałego drukarki w . Jest odpowiedzialny za obiekt wywołujący, aby usunąć kontroler domeny drukarki i wywołać funkcję Windows `CPrintDialogEx` [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na uchwytach po zakończeniu z obiektem.

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrintDialogEx::GetDeviceName

Wywołanie tej funkcji po wywołaniu [DoModal,](#domodal) aby pobrać nazwę aktualnie wybranej drukarki lub po wywołaniu [GetDefaults,](#getdefaults) aby pobrać nazwę drukarki domyślnej.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranej drukarki.

### <a name="remarks"></a>Uwagi

Użyj wskaźnika `CString` do obiektu `GetDeviceName` zwróconego `lpszDeviceName` jako wartość w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrintDialogEx::GetDevMode

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać informacje o urządzeniu drukującym.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura danych [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) która zawiera informacje o inicjowaniu urządzenia i środowisku sterownika wydruku. Należy odblokować pamięć pobraną przez tę strukturę za pomocą funkcji Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) która jest opisana w sdk systemu Windows.

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrintDialogEx::GetDriverName

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać nazwę sterownika urządzenia drukarki zdefiniowanej przez system.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określanie nazwy sterownika zdefiniowanej przez system.

### <a name="remarks"></a>Uwagi

Użyj wskaźnika `CString` do obiektu `GetDriverName` zwróconego jako wartość *lpszDriverName* w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrintDialogEx::GetPortName

Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults,](#getdefaults) aby pobrać nazwę aktualnie wybranego portu drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego portu drukarki.

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Zwraca dojście do kontekstu urządzenia drukarki.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia drukarki.

### <a name="remarks"></a>Uwagi

Należy wywołać funkcję [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) systemu Windows, aby usunąć kontekst urządzenia po zakończeniu korzystania z niego.

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrintDialogEx::m_pdex

Struktura PRINTDLGEX, której członkowie przechowują właściwości obiektu okna dialogowego.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CPrintDialogEx` obiektu, można `m_pdex` użyć, aby ustawić różne aspekty okna dialogowego przed wywołaniem Funkcji elementu członkowskiego [DoModal.](#domodal) Aby uzyskać więcej `m_pdex` informacji na temat struktury, zobacz [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) w windows SDK.

Jeśli zmodyfikujesz `m_pdex` element członkowski danych bezpośrednio, należy zastąpić wszelkie domyślne zachowanie.

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy mają być drukowane wszystkie strony w dokumencie.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wszystkie strony w dokumencie mają być wydrukowane; w przeciwnym razie FALSE.

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::PrintCollate

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy drukarka powinna zestawić wszystkie drukowane kopie dokumentu.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli użytkownik wybierze pole wyboru sortowania w oknie dialogowym; w przeciwnym razie FALSE.

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy wydrukować bieżącą stronę w dokumencie.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli w oknie dialogowym drukowania zaznaczono opcję **Drukuj bieżącą stronę;** w przeciwnym razie FALSE.

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy wydrukować tylko zakres stron w dokumencie.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli mają być drukowane tylko różne strony w dokumencie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Określone zakresy stron można określić na `nPageRanges`podstawie `nMaxPageRanges` `lpPageRanges` [m_pdex](#m_pdex) (patrz , i w strukturze [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) w windows SDK).

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::PrintSelection

Wywołanie tej `DoModal` funkcji po wywołaniu, aby ustalić, czy drukować tylko aktualnie wybrane elementy.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli mają być drukowane tylko wybrane elementy; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz też

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
