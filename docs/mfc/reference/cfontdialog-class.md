---
title: Klasa CFontDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
dev_langs:
- C++
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d64ec306f77174b72c130c3afc14a732464c43be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cfontdialog-class"></a>Klasa CFontDialog
Umożliwia włączenie okno dialogowe Wybór czcionki do aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontDialog::CFontDialog](#cfontdialog)|Konstruuje `CFontDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|  
|[CFontDialog::GetCharFormat](#getcharformat)|Pobiera formatowanie znaków wybranej czcionki.|  
|[CFontDialog::GetColor](#getcolor)|Zwraca kolor wybranej czcionki.|  
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Przypisuje właściwości aktualnie wybranej czcionki do `LOGFONT` struktury.|  
|[CFontDialog::GetFaceName](#getfacename)|Zwraca nazwę krój wybranej czcionki.|  
|[CFontDialog::GetSize](#getsize)|Zwraca wybranej czcionki w punktach.|  
|[CFontDialog::GetStyleName](#getstylename)|Zwraca nazwę stylu wybranej czcionki.|  
|[CFontDialog::GetWeight](#getweight)|Zwraca wagę wybranej czcionki.|  
|[CFontDialog::IsBold](#isbold)|Określa, czy czcionka jest pogrubiona.|  
|[CFontDialog::IsItalic](#isitalic)|Określa, czy czcionka jest kursywą.|  
|[CFontDialog::IsStrikeOut](#isstrikeout)|Określa, czy czcionka jest wyświetlana z przekreślenia.|  
|[CFontDialog::IsUnderline](#isunderline)|Określa, czy czcionka jest podkreślona.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontDialog::m_cf](#m_cf)|Struktury używane w celu dostosowania `CFontDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 A `CFontDialog` obiekt jest okno dialogowe z listy czcionek, które są aktualnie zainstalowane w systemie. Użytkownik może wybrać określonej czcionki z listy, a ten wybór jest następnie zgłaszana z powrotem do aplikacji.  
  
 Aby utworzyć `CFontDialog` obiektów, użyj dostarczonego konstruktora lub pobrać nową podklasę i używanie własnych niestandardowych konstruktora.  
  
 Raz `CFontDialog` obiekt został skonstruowany, możesz użyć `m_cf` struktury zainicjować wartości lub stany formantów w oknie dialogowym. [M_cf](#m_cf) struktura jest typu [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832). Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
 Po podczas inicjowania obiektu okna dialogowego formantów, należy wywołać `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie czcionki. `DoModal` Zwraca czy użytkownik wybrał OK ( **IDOK**), lub Anuluj ( **IDCANCEL**) przycisku.  
  
 Jeśli `DoModal` zwraca **IDOK**, można użyć jednej z `CFontDialog`w funkcji elementów członkowskich do pobrania informacji o danych wejściowych przez użytkownika.  
  
 Można użyć Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i aby dowiedzieć się więcej o tym błędzie. Aby uzyskać więcej informacji dotyczących tej funkcji zobacz zestaw Windows SDK.  
  
 `CFontDialog` zależy od pliku COMMDLG. Plik DLL, która jest dostarczana z systemem Windows w wersji 3.1 lub nowszej.  
  
 Aby dostosować okno dialogowe, pochodzi z klasy `CFontDialog`, podaj szablon niestandardowe okno dialogowe i dodać mapy wiadomości do przetwarzania komunikatów powiadomień od formantów rozszerzonego. Komunikaty nieprzetworzone powinny zostać przekazane do klasy podstawowej.  
  
 Dostosowywanie funkcji punktów zaczepienia nie jest wymagane.  
  
 Aby uzyskać więcej informacji na temat używania `CFontDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog  
 Konstruuje `CFontDialog` obiektu.  
  
```  
CFontDialog(
    LPLOGFONT lplfInitial = NULL,  
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,  
    DWORD dwFlags = CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 l `plfInitial`  
 Wskaźnik do [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury danych, które można ustawić niektórych właściwości czcionki.  
  
 `charFormat`  
 Wskaźnik do [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura danych, którą można ustawić niektórych właściwości czcionki w zaawansowanej edycji.  
  
 `dwFlags`  
 Określa jedną lub więcej flag wybierz czcionkę. Co najmniej jeden wstępnie zdefiniowane wartości można łączyć przy użyciu bitowego operatora OR. Jeśli zmodyfikujesz `m_cf.Flag`s elementu członkowskiego struktury, należy użyć bitowy operator OR zmiany do zachowane zachowanie domyślne. Aby uzyskać szczegółowe informacje na każdym z tych flag, zobacz opis [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) struktury w zestawie Windows SDK.  
  
 pdcPrinter  
 Wskaźnik do kontekstu urządzenia drukarki. Jeśli podany, ten parametr wskazuje kontekstu urządzenia drukarki dla drukarki, na którym można wybrać czcionki.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe czcionki.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że Konstruktor automatycznie wypełnia członków `CHOOSEFONT` struktury. Tylko należy je zmienić, gdy okno dialogowe czcionki mają innych niż domyślne.  
  
> [!NOTE]
>  Pierwszą wersję tej funkcji istnieje tylko w przypadku, gdy ma nie zaawansowanej edycji obsługi formantów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CFontDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe czcionki wspólne systemu Windows i Zezwalaj użytkownikowi na wybranie czcionki z.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **IDOK** lub **IDCANCEL**. Jeśli **IDCANCEL** jest zwracany, wywołanie systemu Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd.  
  
 **IDOK** i **IDCANCEL** są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego czcionki przez ustawienie członkami [m_cf](#m_cf) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, innego członka można wywołać funkcji można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.  
  
### <a name="example"></a>Przykład  
  Przykłady dla [CFontDialog::CFontDialog](#cfontdialog) i [CFontDialog::GetColor](#getcolor).  
  
##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat  
 Pobiera formatowanie znaków wybranej czcionki.  
  
```  
void GetCharFormat(CHARFORMAT& cf) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 A [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktury zawierającej informacje o formatowanie znaków wybranej czcionki.  
  
##  <a name="getcolor"></a>  CFontDialog::GetColor  
 Wywołanie tej funkcji można pobrać kolorów wybranej czcionki.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor wybranej czcionki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]  
  
##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont  
 Wywołanie tej funkcji można przypisać właściwości aktualnie wybranej czcionki do elementów członkowskich [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
```  
void GetCurrentFont(LPLOGFONT lplf);
```  
  
### <a name="parameters"></a>Parametry  
 *lplf*  
 Wskaźnik do `LOGFONT` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Inne `CFontDialog` funkcji elementów członkowskich są dostarczane do dostępu cech bieżącej czcionki.  
  
 Jeśli ta funkcja jest wywoływana podczas wywoływania [DoModal](#domodal), zwraca bieżące zaznaczenie w czasie (co użytkownik będzie widział lub ma zmienić w oknie dialogowym). Jeśli ta funkcja jest wywoływana po wywołaniu `DoModal` (tylko wtedy, gdy `DoModal` zwraca **IDOK**), zwraca jakie faktycznie wybrany przez użytkownika.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]  
  
##  <a name="getfacename"></a>  CFontDialog::GetFaceName  
 Wywołanie tej funkcji można pobrać nazwa czcionki wybranej czcionki.  
  
```  
CString GetFaceName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa czcionki czcionki wybrane w `CFontDialog` okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]  
  
##  <a name="getsize"></a>  CFontDialog::GetSize  
 Wywołanie tej funkcji można pobrać rozmiaru wybranej czcionki.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar czcionki w dziesiąte części punktu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]  
  
##  <a name="getstylename"></a>  CFontDialog::GetStyleName  
 Wywołaj tę funkcję, aby pobrać nazwę stylu wybranej czcionki.  
  
```  
CString GetStyleName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa stylu czcionki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]  
  
##  <a name="getweight"></a>  CFontDialog::GetWeight  
 Wywołanie tej funkcji można pobrać wagę wybranej czcionki.  
  
```  
int GetWeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Waga wybranej czcionki.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na wagę czcionki, zobacz [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]  
  
##  <a name="isbold"></a>  CFontDialog::IsBold  
 Wywołanie tej funkcji, aby określić, czy wybrana czcionka jest pogrubiona.  
  
```  
BOOL IsBold() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wybrana czcionka charakteryzuje się tym Bold włączony; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]  
  
##  <a name="isitalic"></a>  CFontDialog::IsItalic  
 Wywołanie tej funkcji, aby określić, czy wybrana czcionka jest kursywą.  
  
```  
BOOL IsItalic() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wybrana czcionka charakteryzuje się tym kursywą włączony; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]  
  
##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut  
 Wywołanie tej funkcji, aby określić, gdy wybrana czcionka zostanie wyświetlony z przekreślenia.  
  
```  
BOOL IsStrikeOut() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wybrana czcionka charakteryzuje się tym przekreślenia włączony; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]  
  
##  <a name="isunderline"></a>  CFontDialog::IsUnderline  
 Wywołanie tej funkcji w celu ustalenia, czy wybrana czcionka jest podkreślona.  
  
```  
BOOL IsUnderline() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wybrana czcionka charakteryzuje się tym Podkreślenie włączone; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]  
  
##  <a name="m_cf"></a>  CFontDialog::m_cf  
 Struktura, której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
CHOOSEFONT m_cf;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CFontDialog` obiektu, można użyć `m_cf` do modyfikowania różnych aspektów okno dialogowe przed wywołaniem `DoModal` funkcję elementu członkowskiego. Aby uzyskać więcej informacji na tej struktury, zobacz [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



