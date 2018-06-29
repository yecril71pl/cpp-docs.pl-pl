---
title: Klasa CPageSetupDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
dev_langs:
- C++
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd96f0240f8dd97fdda54fd2d00231db14ae3d47
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079186"
---
# <a name="cpagesetupdialog-class"></a>Klasa CPageSetupDialog
Hermetyzuje usług świadczonych przez okno dialogowe Ustawienia strony OLE wspólne systemu Windows z obsługą dodatkowych ustawień i modyfikowania marginesów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Konstruuje `CPageSetupDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia, aby je wydrukować.|  
|[CPageSetupDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia wybór użytkownika wykonującego.|  
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Zwraca nazwę urządzenia drukarki.|  
|[CPageSetupDialog::GetDevMode](#getdevmode)|Zwraca bieżącą `DEVMODE` drukarki.|  
|[CPageSetupDialog::GetDriverName](#getdrivername)|Zwraca sterownik drukarki.|  
|[CPageSetupDialog::GetMargins](#getmargins)|Zwraca bieżące ustawienia marginesu drukarki.|  
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Zwraca rozmiar papieru drukarki.|  
|[CPageSetupDialog::GetPortName](#getportname)|Zwraca nazwę portu wyjściowego.|  
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Wywoływane przez platformę, by renderować obraz ekranu z wydrukowaną stroną.|  
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Wywoływane przez platformę przed renderowaniem obrazu ekranu z wydrukowaną stroną.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPageSetupDialog::m_psd](#m_psd)|Struktury używane w celu dostosowania `CPageSetupDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa służy do odbywać się w oknie dialogowym Ustawienia wydruku.  
  
 Aby użyć `CPageSetupDialog` obiektów, najpierw utwórz obiekt przy użyciu `CPageSetupDialog` konstruktora. Gdy okno dialogowe zostały utworzone, możesz ustawić lub zmodyfikować wartości w `m_psd` element członkowski danych zainicjować wartości formantów okna dialogowego. [M_psd](#m_psd) struktura jest typu **PAGESETUPDLG**.  
  
 Po inicjowanie formantów okna dialogowego, należy wywołać `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. `DoModal` Zwraca czy użytkownik wybrał OK ( **IDOK**), lub Anuluj ( **IDCANCEL**) przycisku.  
  
 Jeśli `DoModal` zwraca **IDOK**, można użyć kilku `CPageSetupDialog`dla funkcji Członkowskich lub dostęp `m_psd` element członkowski danych, aby pobrać wprowadzania informacji przez użytkownika.  
  
> [!NOTE]
>  Po wspólne okna dialogowe Ustawienia strony OLE jest odrzucane, wszelkie zmiany wprowadzone przez użytkownika nie zostaną zapisane przez platformę. Jest aplikacji zostaną zapisane wszystkie wartości z tego okna dialogowego stałe lokalizacji, takiej jak elementu członkowskiego klasy aplikacji lub aplikacji dokumentu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog  
 Wywołanie tej funkcji w celu utworzenia `CPageSetupDialog` obiektu.  
  
```  
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *wartość elementu dwFlags*  
 Jedną lub więcej flag, które służy do dostosowywania ustawień w oknie dialogowym. Wartości można łączyć, używając operatora bitowego OR. Te wartości mają następujące znaczenie:  
  
- **PSD_DEFAULTMINMARGINS** Ustawia minimalną dozwoloną szerokości marginesy strony, aby być taka sama jak minimów drukarki. Ta flaga jest ignorowana, jeśli **PSD_MARGINS** i **PSD_MINMARGINS** również określonych flag.  
  
- **PSD_INWININIINTLMEASURE** nie jest zaimplementowana.  
  
- **PSD_MINMARGINS** powoduje, że system były używane wartości określone w **rtMinMargin** elementu członkowskiego jako minimalna dopuszczalna szerokości po lewej górnej, prawej i dolnego marginesu. System uniemożliwia wprowadzanie szerokość, która jest mniejsza niż minimalna określona. Jeśli **PSD_MINMARGINS** nie zostanie określony, system Ustawia minimalną dozwoloną szerokości tych dozwoloną drukarki.  
  
- **PSD_MARGINS** aktywuje obszar kontroli margines.  
  
- **PSD_INTHOUSANDTHSOFINCHES** powoduje, że jednostki okna dialogowego mierzony w 1/1000 cala.  
  
- **PSD_INHUNDREDTHSOFMILLIMETERS** powoduje, że jednostki okna dialogowego mierzony w 1-100 milimetra.  
  
- **PSD_DISABLEMARGINS** wyłącza formantów okna dialogowego margines.  
  
- **PSD_DISABLEPRINTER** wyłącza przycisk drukarka.  
  
- **PSD_NOWARNING** komunikat ostrzegawczy zapobiega wyświetlaniu po żadnej drukarki domyślnej.  
  
- **PSD_DISABLEORIENTATION** wyłącza formant okna dialogowego orientacja strony.  
  
- **PSD_RETURNDEFAULT** powoduje, że `CPageSetupDialog` do zwrócenia [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktur, które są inicjowane drukarki domyślnej systemu bez wyświetlania okna dialogowego. Zakłada się, że oba **hDevNames** i **pole hDevMode** są **NULL**; w przeciwnym razie funkcja zwraca błąd. Jeśli system drukarki domyślnej jest obsługiwany przez stary sterownika drukarki (starszych niż system Windows w wersji 3.0 lub nowszej), tylko **hDevNames** jest zwracany; **pole hDevMode** jest **NULL**.  
  
- **PSD_DISABLEPAPER** wyłącza formant wyboru papieru.  
  
- **PSD_SHOWHELP** powoduje, że okno dialogowe, aby wyświetlać przycisk Pomoc. **HwndOwner** element członkowski nie może być **NULL** Jeśli ta flaga jest określona.  
  
- **PSD_ENABLEPAGESETUPHOOK** umożliwia funkcji punktów zaczepienia określonej w **lpfnSetupHook**.  
  
- **PSD_ENABLEPAGESETUPTEMPLATE** powoduje, że system operacyjny, można utworzyć okna dialogowego za pomocą okna dialogowego szablonu identyfikowane przez **wystąpienie hInstance** i **lpSetupTemplateName**.  
  
- **PSD_ENABLEPAGESETUPTEMPLATEHANDLE** oznacza to, że **wystąpienie hInstance** identyfikuje bloku danych, który zawiera szablon — okno dialogowe wstępnie. System zignoruje **lpSetupTemplateName** Jeśli ta flaga jest określona.  
  
- **PSD_ENABLEPAGEPAINTHOOK** umożliwia funkcji punktów zaczepienia określonej w **lpfnPagePaintHook**.  
  
- **PSD_DISABLEPAGEPAINTING** wyłącza obszaru rysowania okna dialogowego.  
  
 *pParentWnd*  
 Wskaźnik do nadrzędnego okna dialogowego lub właściciela.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [DoModal](../../mfc/reference/cdialog-class.md#domodal) funkcji, aby wyświetlić okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC  
 Tworzy kontekstu urządzenia drukarki z [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do nowo utworzonej drukarki kontekstu urządzenia (DC).  
  
##  <a name="domodal"></a>  CPageSetupDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe Ustawienia strony OLE wspólne systemu Windows i Zezwalaj użytkownikowi na wybranie różnych opcji Ustawienia wydruku, takich jak marginesy drukowania, rozmiar i orientację papieru i drukarki docelowej.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **IDOK** lub **IDCANCEL**. Jeśli **IDCANCEL** jest zwracany, wywołanie systemu Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd.  
  
 **IDOK** i **IDCANCEL** są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
### <a name="remarks"></a>Uwagi  
 Ponadto użytkownik ma dostęp opcji ustawienia drukarki, takie jak lokalizacja sieciowa i właściwości specyficzne dla wybranych drukarek.  
  
 Jeśli chcesz zainicjować różne opcje Ustawienia strony w oknie dialogowym ustawiając członkami `m_psd` struktury, należy zrobić przed wywołaniem `DoModal`, i po konstruowania obiektu okna dialogowego. Po wywołaniu `DoModal`, wywołania funkcji, aby pobrać ustawienia lub wprowadzania informacji przez użytkownika w oknie dialogowym innego członka.  
  
 Propagacja ustawień wprowadzonych przez użytkownika, należy wywołanie [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Ta funkcja przyjmuje informacji z `CPageSetupDialog` obiektu i inicjuje i wybiera drukarki nowego kontrolera domeny za pomocą odpowiednich atrybutów.  
  
 [!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName  
 Wywołanie tej funkcji po `DoModal` można pobrać nazwę aktualnie wybrane drukarki.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa urządzenia używane przez `CPageSetupDialog` obiektu.  
  
##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać informacji o kontekście urządzenia drukarki `CPageSetupDialog` obiektu.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury danych, który zawiera informacje dotyczące inicjowania urządzenia i środowiska sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z systemu Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkcji, która jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName  
 Wywołanie tej funkcji po wywołaniu [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) pobrać nazwy sterownika drukarki zdefiniowane przez system.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` określania nazwy sterownika zdefiniowane przez system.  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać marginesy sterownika urządzenia.  
  
```  
void GetMargins(
    LPRECT lpRectMargins,  
    LPRECT lpRectMinMargins) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpRectMargins*  
 Wskaźnik do [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który opisuje (w calach 1/1000 lub mm 1/100) marginesy wydruku dla aktualnie wybranej drukarki. Przekaż **NULL** dla tego parametru, jeśli nie są zainteresowane prostokąta.  
  
 *lpRectMinMargins*  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu, który opisuje (w calach 1/1000 lub mm 1/100) minimalna marginesy wydruku dla aktualnie wybranej drukarki. Przekaż **NULL** dla tego parametru, jeśli nie są zainteresowane prostokąta.  
  
##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize  
 Wywołanie tej funkcji można pobrać rozmiar papieru wybrane do drukowania.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt zawierający rozmiar papieru (w calach 1/1000 lub mm 1/100) wybrane do drukowania.  
  
##  <a name="getportname"></a>  CPageSetupDialog::GetPortName  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać nazwy portu aktualnie wybranej drukarki.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa portu aktualnie wybrane drukarki.  
  
##  <a name="m_psd"></a>  CPageSetupDialog::m_psd  
 Struktura typu **PAGESETUPDLG**, której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
PAGESETUPDLG m_psd;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CPageSetupDialog` obiektu, można użyć `m_psd` można ustawić różne aspekty okna dialogowego przed wywołaniem `DoModal` funkcję elementu członkowskiego.  
  
 Jeśli zmodyfikujesz `m_psd` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.  
  
 Aby uzyskać więcej informacji na temat [PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842) struktury, zobacz zestaw Windows SDK.  
  
 Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage  
 Wywoływane przez platformę, by narysować obrazu ekranu z wydrukowaną stroną.  
  
```  
virtual UINT OnDrawPage(
    CDC* pDC,  
    UINT nMessage,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia drukarki.  
  
 *nkomunikat*  
 Określa komunikat, informujący o obszarze strony obecnie rysowane. Może to być jeden z następujących elementów:  
  
- **WM_PSD_FULLPAGERECT** obszaru całej strony.  
  
- **WM_PSD_MINMARGINRECT** Bieżąca minimalna marginesów.  
  
- **WM_PSD_MARGINRECT** bieżących marginesów.  
  
- **WM_PSD_GREEKTEXTRECT** zawartość strony.  
  
- **WM_PSD_ENVSTAMPRECT** miejsce zarezerwowane do reprezentacji sygnatury wysyłki.  
  
- **WM_PSD_YAFULLPAGERECT** obszaru dla reprezentacji adres zwrotny. Rozszerza ten obszar do krawędzi obszaru przykładowe strony.  
  
 *lprect —*  
 Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) obiekt zawierający współrzędne obszaru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość niezerowa, jeśli obsługiwane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ten obraz jest wyświetlone jako część wspólne okna dialogowe Ustawienia strony OLE. Domyślna implementacja Rysuje obraz strony tekstu.  
  
 Należy przesłonić tę funkcję, aby dostosować rysunku określonego obszaru obrazu lub całego obrazu. Można to zrobić za pomocą **przełącznika** instrukcji z **przypadku** instrukcje wartości *nkomunikat*. Na przykład aby dostosować renderowania zawartości obrazu strony, można użyć Poniższy przykładowy kod:  
  
 [!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]  
  
 Należy pamiętać, że nie należy do obsługi każdego przypadku *nkomunikat*. Można obsługiwać jeden składnik obrazu kilka składników obrazu lub cały obszar.  
  
##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage  
 Wywoływane przez platformę przed narysowaniem obrazu ekranu z wydrukowaną stroną.  
  
```  
virtual UINT PreDrawPage(
    WORD wPaper,  
    WORD wFlags,  
    LPPAGESETUPDLG pPSD);
```  
  
### <a name="parameters"></a>Parametry  
 *wPaper*  
 Określa wartość, która wskazuje rozmiar papieru. Ta wartość może być jedną z **DMPAPER_** wartości wymienionych w opisie [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury.  
  
 *wFlags*  
 Określa orientację papieru lub koperty, oraz czy drukarka jest-Mozaika lub urządzenie HPPCL (Hewlett Packard drukarki kontroli Language). Ten parametr może mieć jedną z następujących wartości:  
  
-   0x001 papier w trybie krajobraz (Mozaika)  
  
-   0x003 papier w trybie krajobraz (HPPCL)  
  
-   0x005 papier w trybie portret (Mozaika)  
  
-   0x007 papier w trybie portret (HPPCL)  
  
-   0x00b koperta w trybie krajobraz (HPPCL)  
  
-   0x00d koperta w trybie portret (Mozaika)  
  
-   0x019 koperta w trybie krajobraz (Mozaika)  
  
-   0x01f koperta w trybie portret (Mozaika)  
  
 *pPSD*  
 Wskaźnik do **PAGESETUPDLG** struktury. Aby uzyskać więcej informacji na temat [PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842), zobacz zestaw Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość niezerowa, jeśli obsługiwane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować rysowania obrazu. Zmiany ustawień tej funkcji i zwracać **TRUE**, należy narysować całego obrazu. Zmiany ustawień tej funkcji i zwracać **FALSE**, cały domyślnego obrazu jest rysowany przez platformę.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC WORDPAD](../../visual-cpp-samples.md)   
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



