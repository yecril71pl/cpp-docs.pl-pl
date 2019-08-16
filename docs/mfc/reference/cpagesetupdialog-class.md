---
title: Klasa CPageSetupDialog
ms.date: 11/04/2016
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
ms.openlocfilehash: 18b17d0f40aaab6ba2a018a568950549eda23016
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503012"
---
# <a name="cpagesetupdialog-class"></a>Klasa CPageSetupDialog

Hermetyzuje usługi zapewniane przez wspólne okno dialogowe Ustawienia strony OLE systemu Windows z dodatkową obsługą ustawiania i modyfikowania marginesów wydruku.

## <a name="syntax"></a>Składnia

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Konstruuje `CPageSetupDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia do drukowania.|
|[CPageSetupDialog::D oModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi wybranie.|
|[CPageSetupDialog:: GetDeviceName](#getdevicename)|Zwraca nazwę urządzenia drukarki.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Zwraca bieżący DEVMODE drukarki.|
|[CPageSetupDialog:: GetDriverName](#getdrivername)|Zwraca sterownik używany przez drukarkę.|
|[CPageSetupDialog:: GetMargins](#getmargins)|Zwraca ustawienia bieżącego marginesu drukarki.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Zwraca rozmiar papieru drukarki.|
|[CPageSetupDialog:: GetPortName](#getportname)|Zwraca nazwę portu wyjściowego.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Wywoływane przez platformę, by renderować obraz ekranu drukowanej strony.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Wywoływane przez platformę przed renderowaniem obrazu ekranu drukowanej strony.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Struktura używana do dostosowywania `CPageSetupDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa została zaprojektowana w celu przełączenia okna dialogowego Ustawienia wydruku.

Aby użyć `CPageSetupDialog` obiektu, należy najpierw utworzyć obiekt `CPageSetupDialog` przy użyciu konstruktora. Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować wszystkie wartości w `m_psd` składowej danych, aby zainicjować wartości kontrolek okna dialogowego. Struktura [m_psd](#m_psd) jest typu PAGESETUPDLG.

Po zainicjowaniu kontrolek okna dialogowego Wywołaj `DoModal` funkcję członkowską, aby wyświetlić okno dialogowe i umożliwić użytkownikowi wybranie opcji drukowania. `DoModal`Zwraca czy użytkownik zaznaczył przycisk OK (IDOK) lub Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można użyć `CPageSetupDialog`kilku `m_psd` funkcji Członkowskich lub uzyskać dostęp do elementu członkowskiego danych, aby pobrać dane wejściowe przez użytkownika.

> [!NOTE]
>  Po odrzuceniu okna dialogowego typowe ustawienia strony OLE, wszelkie zmiany wprowadzone przez użytkownika nie zostaną zapisane przez strukturę. W celu zapisania dowolnych wartości z tego okna dialogowego do trwałej lokalizacji, takiej jak członek dokumentu lub klasy aplikacji aplikacji, jest do niej zapisana sama aplikacja.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

##  <a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Wywołaj tę funkcję, aby `CPageSetupDialog` skonstruować obiekt.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Jedna lub więcej flag, których można użyć, aby dostosować ustawienia okna dialogowego. Wartości można łączyć za pomocą operatora bitowego lub. Te wartości mają następujące znaczenie:

- PSD_DEFAULTMINMARGINS ustawia minimalną dozwoloną szerokość marginesów strony, która będzie taka sama jak minimalna wartość drukarki. Ta flaga jest ignorowana, jeśli określono również flagi PSD_MARGINS i PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE nie została zaimplementowana.

- PSD_MINMARGINS powoduje, że system używa wartości określonych w `rtMinMargin` elemencie członkowskim jako minimalnej dozwolonej szerokości marginesu lewego, górnego, prawego i dolnego. System uniemożliwia użytkownikowi wprowadzenie szerokości, która jest mniejsza niż określona wartość minimalna. Jeśli PSD_MINMARGINS nie jest określony, System ustawia minimalną dozwoloną szerokość dla dozwolonych przez drukarkę.

- PSD_MARGINS aktywuje obszar sterowania marginesem.

- PSD_INTHOUSANDTHSOFINCHES powoduje, że jednostki okna dialogowego mają być mierzone w 1/1000 cala.

- PSD_INHUNDREDTHSOFMILLIMETERS powoduje, że jednostki okna dialogowego mają być mierzone w 1/100 milimetra.

- PSD_DISABLEMARGINS wyłącza kontrolki okna dialogowego margines.

- PSD_DISABLEPRINTER wyłącza przycisk drukarki.

- PSD_NOWARNING uniemożliwia wyświetlenie komunikatu ostrzegawczego, gdy nie ma domyślnej drukarki.

- PSD_DISABLEORIENTATION wyłącza formant okna dialogowego orientacja strony.

- PSD_RETURNDEFAULT powoduje `CPageSetupDialog` zwrócenie struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) , które są inicjowane dla domyślnej drukarki systemowej bez wyświetlania okna dialogowego. Przyjęto założenie, że `hDevNames` oba `hDevMode` i są równe null; w przeciwnym razie funkcja zwraca błąd. Jeśli domyślna drukarka systemowa jest obsługiwana przez stary sterownik drukarki (starsza niż wersja 3,0), zwracany jest `hDevNames` tylko system Windows. `hDevMode` ma wartość null.

- PSD_DISABLEPAPER wyłącza kontrolkę wyboru papieru.

- PSD_SHOWHELP powoduje, że okno dialogowe wyświetla przycisk Pomoc. Jeśli `hwndOwner` ta flaga jest określona, element członkowski nie może mieć wartości null.

- PSD_ENABLEPAGESETUPHOOK włącza funkcję Hook określoną w `lpfnSetupHook`elemencie.

- PSD_ENABLEPAGESETUPTEMPLATE powoduje, że system operacyjny tworzy okno dialogowe przy użyciu pola szablon okna dialogowego identyfikowanego przez `hInstance` i `lpSetupTemplateName`.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE wskazuje, `hInstance` że identyfikuje blok danych zawierający wstępnie załadowany szablon okna dialogowego. System ignoruje `lpSetupTemplateName` , czy ta flaga jest określona.

- PSD_ENABLEPAGEPAINTHOOK włącza funkcję Hook określoną w `lpfnPagePaintHook`elemencie.

- PSD_DISABLEPAGEPAINTING wyłącza obszar rysowania okna dialogowego.

*pParentWnd*<br/>
Wskaźnik do elementu nadrzędnego lub właściciela okna dialogowego.

### <a name="remarks"></a>Uwagi

Użyj funkcji [DoModal](../../mfc/reference/cdialog-class.md#domodal) , aby wyświetlić okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki na podstawie struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonego kontekstu urządzenia drukarki (DC).

##  <a name="domodal"></a>CPageSetupDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe Ustawienia typowej strony OLE systemu Windows i zezwolić użytkownikowi na wybór różnych opcji konfiguracji drukowania, takich jak marginesy drukowania, rozmiar i Orientacja papieru i drukarki docelowej.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli IDCANCEL jest zwracany, wywołaj funkcję Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) , aby określić, czy wystąpił błąd.

IDOK i IDCANCEL są stałymi, które wskazują, czy użytkownik zaznaczył przycisk OK lub Anuluj.

### <a name="remarks"></a>Uwagi

Ponadto użytkownik może uzyskać dostęp do opcji konfiguracji drukarki, takich jak lokalizacja sieciowa i właściwości specyficzne dla wybranej drukarki.

Jeśli chcesz zainicjować różne opcje okna dialogowego Ustawienia strony, ustawiając elementy członkowskie `m_psd` struktury, należy to zrobić przed wywołaniem `DoModal`i po skonstruowaniu obiektu okna dialogowego. Po wywołaniu `DoModal`należy wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe użytkownika w oknie dialogowym.

Jeśli chcesz propagować bieżące ustawienia wprowadzone przez użytkownika, wykonaj wywołanie [CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Ta funkcja pobiera informacje z `CPageSetupDialog` obiektu i inicjuje i wybiera nowy kontroler domeny z odpowiednimi atrybutami.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>CPageSetupDialog:: GetDeviceName

Wywołaj tę funkcję `DoModal` po pobraniu nazwy aktualnie wybranej drukarki.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa urządzenia używana przez `CPageSetupDialog` obiekt.

##  <a name="getdevmode"></a>CPageSetupDialog:: getdevmode

Wywołaj tę funkcję po `DoModal` wywołaniu, aby pobrać informacje o kontekście `CPageSetupDialog` urządzenia drukarki.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura danych [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , która zawiera informacje o inicjalizacji i środowisku urządzenia sterownika drukarki. Należy odblokować pamięć wykonywaną przez tę strukturę przy użyciu funkcji [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) systemu Windows, która jest opisana w Windows SDK.

##  <a name="getdrivername"></a>CPageSetupDialog:: GetDriverName

Wywołaj tę funkcję po wywołaniu [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) , aby pobrać nazwę sterownika urządzenia drukarki zdefiniowanej przez system.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

`CString` Określanie nazwy sterownika zdefiniowanej przez system.

### <a name="remarks"></a>Uwagi

Użyj wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu metody [przechwytywania:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>CPageSetupDialog:: GetMargins

Wywołaj tę funkcję po wywołaniu `DoModal` , aby pobrać marginesy sterownika urządzenia drukarki.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parametry

*lpRectMargins*<br/>
Wskaźnik do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) , który opisuje (w 1/1000 cala lub 1/100 mm) marginesy wydruku dla aktualnie wybranej drukarki. Przekaż wartość NULL dla tego parametru, jeśli nie jesteś zainteresowanym tym prostokątem.

*lpRectMinMargins*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiektu, który opisuje (w 1/1000 cala lub 1/100 mm) minimalne marginesy wydruku dla aktualnie wybranej drukarki. Przekaż wartość NULL dla tego parametru, jeśli nie jesteś zainteresowanym tym prostokątem.

##  <a name="getpapersize"></a>CPageSetupDialog:: GetPaperSize

Wywołaj tę funkcję, aby pobrać rozmiar papieru wybranego do drukowania.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) zawierający rozmiar papieru (w 1/1000 cala lub 1/100 mm) wybrany do drukowania.

##  <a name="getportname"></a>CPageSetupDialog:: GetPortName

Wywołaj tę funkcję po `DoModal` wywołaniu, aby pobrać nazwę aktualnie wybranego portu drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego portu drukarki.

##  <a name="m_psd"></a>CPageSetupDialog::m_psd

Struktura typu PAGESETUPDLG, której członkowie przechowują cechy obiektu okna dialogowego.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CPageSetupDialog` obiektu można użyć `m_psd` , aby ustawić różne aspekty okna `DoModal` dialogowego przed wywołaniem funkcji składowej.

W `m_psd` przypadku zmodyfikowania elementu członkowskiego danych należy zmienić zachowanie domyślne.

Aby uzyskać więcej informacji na temat struktury [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw) , zobacz Windows SDK.

Zobacz przykład dla [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

Wywoływane przez platformę, by narysować obraz ekranu drukowanej strony.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*nkomunikat*<br/>
Określa komunikat wskazujący obszar aktualnie rysowanej strony. Może to być jeden z następujących elementów:

- WM_PSD_FULLPAGERECT cały obszar strony.

- WM_PSD_MINMARGINRECT bieżące minimalne marginesy.

- WM_PSD_MARGINRECT bieżące marginesy.

- WM_PSD_GREEKTEXTRECT zawartość strony.

- Obszar WM_PSD_ENVSTAMPRECT zastrzeżony dla reprezentacji sygnatury pocztowej.

- Obszar WM_PSD_YAFULLPAGERECT dla reprezentacji adresu zwrotnego. Ten obszar rozciąga się na krawędzie przykładowego obszaru strony.

*lpRect*<br/>
Wskaźnik do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [Rect](/windows/win32/api/windef/ns-windef-rect) zawierającego współrzędne obszaru rysowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli jest obsługiwana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten obraz jest następnie wyświetlany jako część typowej konfiguracji strony OLE okno dialogowe. Domyślna implementacja rysuje obraz strony tekstu.

Zastąp tę funkcję, aby dostosować rysowanie określonego obszaru obrazu lub całego obrazu. Można to zrobić za pomocą instrukcji **Switch** z instrukcją **Case** sprawdzającą wartość *nkomunikat*. Na przykład, aby dostosować renderowanie zawartości obrazu strony, można użyć następującego przykładowego kodu:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Należy pamiętać, że nie trzeba obsługiwać każdego przypadku *nkomunikat*. Można wybrać obsługę jednego składnika obrazu, kilku składników obrazu lub całego obszaru.

##  <a name="predrawpage"></a>CPageSetupDialog::P reDrawPage

Wywoływane przez platformę przed rysowaniem obrazu ekranu drukowanej strony.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parametry

*wPaper*<br/>
Określa wartość wskazującą rozmiar papieru. Ta wartość może być jedną z wartości **DMPAPER_** wymienionych w opisie struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) .

*wFlags*<br/>
Określa orientację papieru lub koperty oraz określa, czy drukarka jest urządzeniem typu "Matrix" lub "HPPCL" (drukarka Hewlett Packard Printer Control Language). Ten parametr może mieć jedną z następujących wartości:

- Papier 0x001 w trybie poziomym (macierz mozaikowa)

- Papier 0x003 w trybie poziomym (HPPCL)

- Papier 0x005 w trybie pionowym (Matrix)

- Papier 0x007 w trybie pionowym (HPPCL)

- Koperta 0x00b w trybie poziomym (HPPCL)

- Koperta w trybie pionowym (Matrix)

- Koperta 0x019 w trybie poziomym (macierz mozaikowa)

- Koperta 0x01f w trybie pionowym (Matrix)

*pPSD*<br/>
Wskaźnik do `PAGESETUPDLG` struktury. Aby uzyskać więcej informacji na temat [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw), zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli jest obsługiwana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować Rysowanie obrazu. Jeśli zastąpisz tę funkcję i zwrócisz wartość TRUE, należy narysować cały obraz. Jeśli zastąpisz tę funkcję i zwrócisz wartość FALSE, cały obraz domyślny zostanie narysowany przez platformę.

## <a name="see-also"></a>Zobacz także

[Przykładowy program WORDPAD dla MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
