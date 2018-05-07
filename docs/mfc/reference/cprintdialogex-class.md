---
title: Klasa CPrintDialogEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f511eb1414a5cd5e22b9a3e05f81caef15b908e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cprintdialogex-class"></a>Klasa CPrintDialogEx
Hermetyzuje usług świadczonych przez arkusz właściwości wydruku systemu Windows.  
  
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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Tworzy kontekstu urządzenia drukarki bez wyświetlania okna dialogowego drukowania.|  
|[CPrintDialogEx::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi wybierz odpowiednie opcje.|  
|[CPrintDialogEx::GetCopies](#getcopies)|Pobiera liczbę kopii żądanie.|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|Pobiera domyślne ustawienia urządzenia bez wyświetlania okna dialogowego.|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Pobiera nazwę urządzenia aktualnie wybranej drukarki.|  
|[CPrintDialogEx::GetDevMode](#getdevmode)|Pobiera `DEVMODE` struktury.|  
|[CPrintDialogEx::GetDriverName](#getdrivername)|Pobiera nazwę sterownika drukarki zdefiniowane przez system.|  
|[CPrintDialogEx::GetPortName](#getportname)|Pobiera nazwę portu aktualnie wybrane drukarki.|  
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Pobiera dojścia do kontekstu urządzenia drukarki.|  
|[CPrintDialogEx::PrintAll](#printall)|Określa, czy do drukowania wszystkich stron dokumentu.|  
|[CPrintDialogEx::PrintCollate](#printcollate)|Określa, czy sortowane kopie są wymagane.|  
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Określa, czy wydrukować bieżącą stronę dokumentu.|  
|[CPrintDialogEx::PrintRange](#printrange)|Określa, czy do określonego zakresu stron drukowania.|  
|[CPrintDialogEx::PrintSelection](#printselection)|Określa, czy do drukowania aktualnie wybrane elementy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktury używane w celu dostosowania `CPrintDialogEx` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Użytkownik może polegać na platformę, by obsłużyć wiele aspektów proces drukowania w aplikacji. Aby uzyskać więcej informacji na temat za pomocą środowiska do obsługi zadań drukowania, zobacz artykuł [drukowania](../../mfc/printing.md).  
  
 Jeśli ma być aplikację do drukowania bez udziału framework, możesz użyć `CPrintDialogEx` klasy "w jakim jest" przy użyciu konstruktora, pod warunkiem, lub mogą pochodzić własne klasy okien dialogowych z `CPrintDialogEx` i zapisywanie konstruktora w zależności od potrzeb. W obu przypadkach tych okien dialogowych będą zachowywać się jak standardowe okna dialogowe MFC ponieważ pochodzą z klasy `CCommonDialog`.  
  
 Aby użyć `CPrintDialogEx` obiektów, najpierw utwórz obiekt przy użyciu `CPrintDialogEx` konstruktora. Gdy okno dialogowe zostały utworzone, możesz ustawić lub zmodyfikować wartości w [m_pdex](#m_pdex) struktury zainicjować wartości formantów okna dialogowego. `m_pdex` Struktura jest typu [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844). Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
 Jeśli nie podasz własne dojść w `m_pdex` dla **pole hDevMode** i **hDevNames** członków, należy wywołać funkcję Windows **GlobalFree** dla tych uchwytów Gdy wszystko będzie gotowe, z okna dialogowego.  
  
 Po inicjowanie formantów okna dialogowego, należy wywołać `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. Gdy `DoModal` zwraca, można określić, czy użytkownik wybrał przycisk OK, Zastosuj lub przycisk Anuluj.  
  
 Jeśli użytkownik kliknął przycisk OK, możesz użyć `CPrintDialogEx`w funkcji elementów członkowskich do pobrania informacji o danych wejściowych przez użytkownika.  
  
 `CPrintDialogEx::GetDefaults` Funkcja członkowska jest przydatne do pobierania bieżące ustawienia domyślne drukarki bez wyświetlania okna dialogowego. Ta metoda nie wymaga interakcji użytkownika.  
  
 Można użyć Windows **CommDlgExtendedError** funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i aby dowiedzieć się więcej o tym błędzie. Aby uzyskać więcej informacji dotyczących tej funkcji zobacz zestaw Windows SDK.  
  
 Aby uzyskać więcej informacji na temat używania `CPrintDialogEx`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).  
  
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
 Tworzy arkusz właściwości wydruku systemu Windows.  
  
```  
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Jedną lub więcej flag, które można dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Na przykład **PD_ALLPAGES** flagi ustawia domyślny zakres drukowania do wszystkich stron dokumentu. Zobacz [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktury w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tych flag.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego lub właściciela okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska tylko konstruuje obiekt. Użyj `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe.  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 Tworzy drukarki kontekstu urządzenia (DC) na podstawie [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do kontekstu urządzenia nowo utworzony drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócony kontrolera domeny także jest przechowywany w **elementu hDC** członkiem [m_pdex](#m_pdex).  
  
 Ten kontroler domeny zakłada, że bieżąca drukarka kontrolera domeny, a inne uzyskany wcześniej drukarki, kontrolery domeny muszą zostać usunięte. Ta funkcja może zostać wywołana, a wynikowy kontrolera domeny używane, bez kiedykolwiek wyświetlania okna dialogowego drukowania.  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 Wywołanie tej funkcji, aby wyświetlić arkusz właściwości wydruku systemu Windows i Zezwalaj użytkownikowi na wybranie różnych opcji drukowania, takie jak liczba kopii, zakres stron, oraz czy mają być sortowane kopie.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 INT_PTR zwracać wartość jest rzeczywiście HRESULT. Zobacz sekcję zwracać wartości w [PrintDlgEx](http://msdn.microsoft.com/library/windows/desktop/ms646942) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych opcji okna dialogowego drukowania przez ustawienie członkami `m_pdex` struktury, należy to zrobić przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Po wywołaniu `DoModal`, innego członka można wywołać funkcji można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.  
  
 Jeśli **PD_RETURNDC** flaga jest używana przy wywoływaniu `DoModal`, drukarki kontrolera domeny, które zostaną zwrócone w **elementu hDC** członkiem [m_pdex](#m_pdex). Ten kontroler domeny musi zostać zwolniony z wywołaniem do [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) przez obiekt wywołujący `CPrintDialogEx`.  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać liczby kopii żądanie.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba kopii żądanie.  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 Wywołanie tej funkcji można pobrać ustawień domyślnych urządzenia domyślnej drukarki bez wyświetlania okna dialogowego.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** w przypadku powodzenia, w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy drukarki kontekstu urządzenia (DC) na podstawie [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
 `GetDefaults` nie są wyświetlane drukowania arkusza właściwości. Zamiast ustawia **hDevNames** i **pole hDevMode** członkami [m_pdex](#m_pdex) do uchwytów do [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES ](../../mfc/reference/devnames-structure.md) struktur, które są inicjowane systemu drukarki domyślnej. Zarówno **hDevNames** i **pole hDevMode** musi mieć wartość NULL, lub `GetDefaults` nie powiedzie się.  
  
 Jeśli **PD_RETURNDC** flaga jest ustawiona, ta funkcja nie tylko zwróci **hDevNames** i **pole hDevMode** (znajdujące się w **m_pdex.hDevNames** i **m_pdex.hDevMode**) do obiektu wywołującego, ale również zwróci drukarki kontrolera domeny w **m_pdex.hDC**. Jest odpowiedzialny za obiekt wywołujący, aby usunąć drukarki kontrolera domeny i wywołań systemu Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funkcja na dojściach po zakończeniu pracy z `CPrintDialogEx` obiektu.  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) pobrać aktualnie wybrane drukarki lub po wywołaniu nazwy [GetDefaults](#getdefaults) pobrać nazwy drukarki domyślnej.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa aktualnie zaznaczonej drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDeviceName` jako wartość `lpszDeviceName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać informacji o urządzeniu drukowania.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury danych, który zawiera informacje dotyczące inicjowania urządzenia i środowiska sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z systemu Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkcji, która jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) pobrać nazwy sterownika drukarki zdefiniowane przez system.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` określania nazwy sterownika zdefiniowane przez system.  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 Wywołanie tej funkcji po wywołaniu [DoModal](#domodal) lub [GetDefaults](#getdefaults) można pobrać nazwy portu aktualnie wybranej drukarki.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa portu aktualnie wybrane drukarki.  
  
##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC  
 Zwraca dojście do kontekstu urządzenia drukarki.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do kontekstu urządzenia drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać systemu Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funkcji, aby usunąć kontekst urządzenia, po zakończeniu korzystania z niego.  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 Struktura PRINTDLGEX, której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CPrintDialogEx` obiektu, można użyć `m_pdex` można ustawić różne aspekty okna dialogowego przed wywołaniem [DoModal](#domodal) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na temat `m_pdex` struktury, zobacz [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) w zestawie Windows SDK.  
  
 Jeśli zmodyfikujesz `m_pdex` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 Wywołanie tej funkcji po wywołaniu `DoModal` do określenia, czy drukowanie wszystkich stron w dokumencie.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** wszystkich stron w dokumencie mają być drukowane; w przeciwnym razie **FALSE**.  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 Wywołanie tej funkcji po wywołaniu `DoModal` ustalenie, czy drukarka powinna sortować wszystkie kopie dokumentu.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli użytkownik wybierze pole wyboru collate w oknie dialogowym; w przeciwnym razie **FALSE**.  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 Wywołanie tej funkcji po wywołaniu `DoModal` do ustalenia, czy należy wydrukować bieżącą stronę w dokumencie.  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli **wydrukować bieżącą stronę** jest wybrana w oknie dialogowym drukowania; w przeciwnym razie **FALSE**.  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 Wywołanie tej funkcji po wywołaniu `DoModal` do ustalenia, czy można drukować tylko zakres stron w dokumencie.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** jeśli tylko zakresu stron w dokumencie mają być drukowane; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Określona strona zakresów można ustalić na podstawie [m_pdex](#m_pdex) (zobacz **nPageRanges**, **nMaxPageRanges**, i **lpPageRanges** w [ PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktury w zestawie Windows SDK).  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 Wywołanie tej funkcji po wywołaniu `DoModal` do ustalenia, czy do drukowania aktualnie wybrane elementy.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** jeśli tylko wybrane elementy mają być drukowane; w przeciwnym razie **FALSE**.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
