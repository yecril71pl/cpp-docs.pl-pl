---
title: Klasa CPrintDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d72b96e0be786aab18903e95f346eccd5364dd4b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079658"
---
# <a name="cprintdialog-class"></a>Klasa CPrintDialog
Hermetyzuje usług świadczonych przez okno dialogowe wspólne systemu Windows do drukowania.  
  
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
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekstu urządzenia drukarki bez wyświetlania okna dialogowego drukowania.|  
|[CPrintDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|  
|[CPrintDialog::GetCopies](#getcopies)|Pobiera liczbę kopii żądanie.|  
|[CPrintDialog::GetDefaults](#getdefaults)|Pobiera domyślne ustawienia urządzenia bez wyświetlania okna dialogowego.|  
|[CPrintDialog::GetDeviceName](#getdevicename)|Pobiera nazwę urządzenia aktualnie wybranej drukarki.|  
|[CPrintDialog::GetDevMode](#getdevmode)|Pobiera `DEVMODE` struktury.|  
|[CPrintDialog::GetDriverName](#getdrivername)|Pobiera nazwę aktualnie wybranego sterownika.|  
|[CPrintDialog::GetFromPage](#getfrompage)|Pobiera stronę początkową zakresu wydruku.|  
|[CPrintDialog::GetPortName](#getportname)|Pobiera nazwę portu aktualnie wybrane drukarki.|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Pobiera dojścia do kontekstu urządzenia drukarki.|  
|[CPrintDialog::GetToPage](#gettopage)|Pobiera stronie końcową zakresu wydruku.|  
|[CPrintDialog::PrintAll](#printall)|Określa, czy do drukowania wszystkich stron dokumentu.|  
|[CPrintDialog::PrintCollate](#printcollate)|Określa, czy sortowane kopie są wymagane.|  
|[CPrintDialog::PrintRange](#printrange)|Określa, czy do określonego zakresu stron drukowania.|  
|[CPrintDialog::PrintSelection](#printselection)|Określa, czy do drukowania aktualnie wybrane elementy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|Struktury używane w celu dostosowania `CPrintDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Wspólnych okien dialogowych wydruku umożliwiają łatwe do zaimplementowania wydruku i ustawienia wydruku okien dialogowych w sposób zgodny ze standardami systemu Windows.  
  
> [!NOTE]
>  `CPrintDialogEx` Klasa hermetyzuje usług świadczonych przez arkusz właściwości wydruku systemu Windows. Aby uzyskać więcej informacji, zobacz [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) omówienie.  
  
 `CPrintDialog`w funkcji jest zastąpiona z [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), który zaprojektowano w celu zapewnienia wspólnego okna dialogowego dla obu wydruku ustawienia i ustawienia strony.  
  
 Użytkownik może polegać na platformę, by obsłużyć wiele aspektów proces drukowania w aplikacji. W takim przypadku platformę automatycznie wyświetla wspólnego okna dialogowego systemu Windows do drukowania. Można również ma uchwyt framework Drukowanie aplikacji jednak zastąpić wspólne okno dialogowe drukowania własne okna dialogowego drukowania. Aby uzyskać więcej informacji na temat za pomocą środowiska do obsługi zadań drukowania, zobacz artykuł [drukowania](../../mfc/printing.md).  
  
 Jeśli ma być aplikację do drukowania bez udziału framework, możesz użyć `CPrintDialog` klasy "w jakim jest" przy użyciu konstruktora, pod warunkiem, lub mogą pochodzić własne klasy okien dialogowych z `CPrintDialog` i zapisywanie konstruktora w zależności od potrzeb. W obu przypadkach tych okien dialogowych będą zachowywać się jak standardowe okna dialogowe MFC ponieważ pochodzą z klasy `CCommonDialog`.  
  
 Aby użyć `CPrintDialog` obiektów, najpierw utwórz obiekt przy użyciu `CPrintDialog` konstruktora. Gdy okno dialogowe zostały utworzone, możesz ustawić lub zmodyfikować wartości w [m_pd](#m_pd) struktury zainicjować wartości formantów okna dialogowego. `m_pd` Struktura jest typu [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843). Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
 Jeśli nie podasz własne dojść w `m_pd` dla **pole hDevMode** i **hDevNames** członków, należy wywołać funkcję Windows **GlobalFree** dla tych uchwytów Gdy wszystko będzie gotowe, z okna dialogowego. Gdy dostarczone przez implementację ustawienia wydruku w ramach `CWinApp::OnFilePrintSetup`, nie trzeba zwolnić uchwyty. Uchwyty są obsługiwane przez `CWinApp` i są zwalniane w `CWinApp`przez destruktor. Jest tylko do zwolnienia uchwyty, korzystając z `CPrintDialog` autonomicznej.  
  
 Po inicjowanie formantów okna dialogowego, należy wywołać `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. `DoModal` Zwraca czy użytkownik wybrał OK ( **IDOK**), lub Anuluj ( **IDCANCEL**) przycisku.  
  
 Jeśli `DoModal` zwraca **IDOK**, można użyć jednej z `CPrintDialog`w funkcji elementów członkowskich do pobrania informacji o danych wejściowych przez użytkownika.  
  
 `CPrintDialog::GetDefaults` Funkcja członkowska jest przydatne do pobierania bieżące ustawienia domyślne drukarki bez wyświetlania okna dialogowego. Ta funkcja członkowska nie wymaga interakcji użytkownika.  
  
 Można użyć Windows **CommDlgExtendedError** funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i aby dowiedzieć się więcej o tym błędzie. Aby uzyskać więcej informacji dotyczących tej funkcji zobacz zestaw Windows SDK.  
  
 `CPrintDialog` zależy od pliku COMMDLG. Plik DLL, która jest dostarczana z systemem Windows w wersji 3.1 lub nowszej.  
  
 Aby dostosować okno dialogowe, pochodzi z klasy `CPrintDialog`, podaj szablon niestandardowe okno dialogowe i dodać mapy komunikatów do przetwarzania komunikatów powiadomień od formantów rozszerzonego. Komunikaty nieprzetworzone powinny być przekazywane do klasy podstawowej. Dostosowywanie funkcji punktów zaczepienia nie jest wymagane.  
  
 Aby przetwarzać ten sam komunikat inaczej w zależności od tego, czy jest okno dialogowe Ustawienia drukarki, musi pochodzić klasy dla każdego — okno dialogowe. Systemu Windows musi także zastępować **AttachOnSetup** funkcji, która obsługuje tworzenie nowego okna dialogowego, gdy przycisk Ustawienia wydruku jest wybrany w oknie dialogowym drukowania.  
  
 Aby uzyskać więcej informacji na temat używania `CPrintDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).  
  
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
 Tworzy obiekt okna dialogowego drukowania systemu Windows albo ustawienia wydruku.  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *bPrintSetupOnly*  
 Określa, czy jest wyświetlany standardowe okno dialogowe Drukuj lub okno dialogowe Ustawienia wydruku. Ustaw ten parametr, **TRUE** do wyświetlenia standardowe okno dialogowe Ustawienia wydruku systemu Windows. Ustaw ją na **FALSE** Aby wyświetlić okno dialogowe drukowania w systemie Windows. Jeśli *bPrintSetupOnly* jest **FALSE**, przycisk opcji Ustawienia wydruku jest nadal wyświetlany w oknie dialogowym drukowania.  
  
 *wartość elementu dwFlags*  
 Jedną lub więcej flag, które można dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Na przykład **PD_ALLPAGES** flagi ustawia domyślny zakres drukowania do wszystkich stron dokumentu. Zobacz [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktury w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tych flag.  
  
 *pParentWnd*  
 Wskaźnik do okna nadrzędnego lub właściciela okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska tylko konstruuje obiekt. Użyj `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe.  
  
 Należy pamiętać, że podczas wywoływania konstruktora z `bPrintSetupOnly` ustawioną **FALSE**, **PD_RETURNDC** Flaga służy automatycznie. Po wywołaniu `DoModal`, `GetDefaults`, lub `GetPrinterDC`, drukarki kontrolera domeny, które zostaną zwrócone w `m_pd.hDC`. Ten kontroler domeny musi zostać zwolniony z wywołaniem do [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) przez obiekt wywołujący `CPrintDialog`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC  
 Tworzy drukarki kontekstu urządzenia (DC) na podstawie [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do kontekstu urządzenia nowo utworzony drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Ten kontroler domeny zakłada, że bieżąca drukarka kontrolera domeny, a inne uzyskany wcześniej drukarki, kontrolery domeny muszą zostać usunięte przez użytkownika. Ta funkcja może zostać wywołana, a wynikowy kontrolera domeny używane, bez kiedykolwiek wyświetlania okna dialogowego drukowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>  CPrintDialog::DoModal  
 Wyświetla okno dialogowe drukowania wspólne systemu Windows i umożliwia użytkownikowi wybranie różnych opcji drukowania, takie jak liczba kopii, zakres stron, oraz czy mają być sortowane kopie.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **IDOK** lub **IDCANCEL**. Jeśli **IDCANCEL** jest zwracany, wywołanie systemu Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd.  
  
 **IDOK** i **IDCANCEL** są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych opcji okna dialogowego drukowania przez ustawienie członkami `m_pd` struktury, należy to zrobić przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Po wywołaniu `DoModal`, innego członka można wywołać funkcji można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.  
  
 Należy pamiętać, że podczas wywoływania konstruktora z *bPrintSetupOnly* ustawioną **FALSE**, **PD_RETURNDC** Flaga służy automatycznie. Po wywołaniu `DoModal`, `GetDefaults`, lub `GetPrinterDC`, drukarki kontrolera domeny, które zostaną zwrócone w `m_pd.hDC`. Ten kontroler domeny musi zostać zwolniony z wywołaniem do [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) przez obiekt wywołujący `CPrintDialog`.  
  
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
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać liczby kopii żądanie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults  
 Pobiera domyślne ustawienia urządzenia domyślnej drukarki bez wyświetlania okna dialogowego.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pobrane wartości są umieszczane w `m_pd` struktury.  
  
 W niektórych przypadkach wywoła wywołanie tej funkcji [Konstruktor](#cprintdialog) dla `CPrintDialog` z *bPrintSetupOnly* ustawioną **FALSE**. W takich przypadkach drukarki kontrolera domeny i **hDevNames** i **pole hDevMode** (dojść do dwóch znajduje się w `m_pd` elementu członkowskiego danych) są przydzielane automatycznie.  
  
 Jeśli Konstruktor `CPrintDialog` została wywołana z `bPrintSetupOnly` ustawioną **FALSE**, ta funkcja nie będzie zwracać tylko **hDevNames** i **pole hDevMode** (znajdujący się w **m_pd.hDevNames** i **m_pd.hDevMode**) do obiektu wywołującego, ale również zwróci drukarki kontrolera domeny w **m_pd.hDC**. Jest odpowiedzialny za obiekt wywołujący, aby usunąć drukarki kontrolera domeny i wywołań systemu Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funkcja na dojściach po zakończeniu pracy z `CPrintDialog` obiektu.  
  
### <a name="example"></a>Przykład  
 Fragmentu kodu pobiera kontekst urządzenia używają domyślnej drukarki i raporty do użytkownika rozdzielczość drukarki w punktach na cal. (Ten atrybut możliwości drukarki jest często określany jako wartość DPI.)  
  
 [!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName  
 Pobiera nazwę urządzenia aktualnie wybranej drukarki.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa aktualnie zaznaczonej drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) pobrać aktualnie wybrane drukarki lub po wywołaniu nazwy [GetDefaults](#getdefaults) można pobrać bieżącego ustawienia domyślne urządzenia drukarki domyślnej. Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDeviceName` jako wartość `lpszDeviceName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Przykład  
 Fragmentu kodu pokazuje nazwa drukarki domyślnej użytkownika oraz port, który jest połączony, wraz z nazwą buforu, używanych do drukarki. Kod wyświetli komunikat, który jest wyświetlany komunikat "drukarki domyślnej jest HP LaserJet IIIP na \\\server\share przy użyciu winspool.", na przykład.  
  
 [!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode  
 Pobiera `DEVMODE` struktury.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury danych, który zawiera informacje dotyczące inicjowania urządzenia i środowiska sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z systemu Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkcji, która jest opisany w zestawie SDK systemu Windows.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać informacji o urządzeniu drukowania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName  
 Pobiera nazwę aktualnie wybranego sterownika.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` określania nazwy sterownika zdefiniowane przez system.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) pobrać nazwy sterownika drukarki zdefiniowane przez system. Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage  
 Pobiera stronę początkową zakresu wydruku.  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer strony początkowej w zakresie stron do drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać numer strony początkowej w zakresie stron do drukowania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="getportname"></a>  CPrintDialog::GetPortName  
 Pobiera nazwę portu aktualnie wybrane drukarki.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa portu aktualnie wybrane drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać nazwy portu aktualnie wybranej drukarki.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC  
 Pobiera dojścia do kontekstu urządzenia drukarki.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do kontekstu urządzenia drukarki w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bPrintSetupOnly* parametr `CPrintDialog` konstruktor został **FALSE** (co oznacza, że zostanie wyświetlone okno dialogowe drukowania), następnie `GetPrinterDC` Zwraca dojście do urządzenia drukarki kontekst. Należy wywołać systemu Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funkcji, aby usunąć kontekst urządzenia, po zakończeniu korzystania z niego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>  CPrintDialog::GetToPage  
 Pobiera stronie końcową zakresu wydruku.  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Końcowy numer strony w zakresie stron do drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać końcowy numer strony w zakresie stron, które mają być drukowane.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="m_pd"></a>  CPrintDialog::m_pd  
 Struktura, której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CPrintDialog` obiektu, można użyć `m_pd` można ustawić różne aspekty okna dialogowego przed wywołaniem [DoModal](#domodal) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na temat `m_pd` struktury, zobacz [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) w zestawie Windows SDK.  
  
 Jeśli zmodyfikujesz `m_pd` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>  CPrintDialog::PrintAll  
 Określa, czy do drukowania wszystkich stron dokumentu.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wszystkie strony w dokumencie mają być drukowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` do określenia, czy drukowanie wszystkich stron w dokumencie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printcollate"></a>  CPrintDialog::PrintCollate  
 Określa, czy sortowane kopie są wymagane.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik wybierze pole wyboru collate w oknie dialogowym. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` ustalenie, czy drukarka powinna sortować wszystkie kopie dokumentu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>  CPrintDialog::PrintRange  
 Określa, czy do określonego zakresu stron drukowania.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli tylko zakres stron w dokumencie mają być drukowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` do ustalenia, czy można drukować tylko zakres stron w dokumencie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printselection"></a>  CPrintDialog::PrintSelection  
 Określa, czy do drukowania aktualnie wybrane elementy.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli tylko wybrane elementy mają być drukowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu `DoModal` do ustalenia, czy do drukowania aktualnie wybrane elementy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPrintDialog::m_pd](#m_pd).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
