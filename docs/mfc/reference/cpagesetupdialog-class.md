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
ms.openlocfilehash: 218ed24ccf56854622e20936299fcc2e8a3d0fa9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374789"
---
# <a name="cpagesetupdialog-class"></a>Klasa CPageSetupDialog

Hermetyzuje usługi świadczone przez okno dialogowe Typowe ustawienia strony OLE systemu Windows z dodatkową obsługą ustawiania i modyfikowania marginesów wydruku.

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
|[CPageSetupDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Zwraca nazwę urządzenia drukarki.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Zwraca bieżący DEVMODE drukarki.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Zwraca sterownik używany przez drukarkę.|
|[CPageSetupDialog::GetMargins](#getmargins)|Zwraca bieżące ustawienia marginesu drukarki.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Zwraca rozmiar papieru drukarki.|
|[CPageSetupDialog::GetPortName](#getportname)|Zwraca nazwę portu wyjściowego.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Wywoływane przez strukturę do renderowania obrazu ekranu drukowanej strony.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Wywoływane przez strukturę przed renderowaniem obrazu ekranu drukowanej strony.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Struktura używana do dostosowywania `CPageSetupDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa jest przeznaczona do miejsca okna dialogowego Ustawienia drukowania.

Aby użyć `CPageSetupDialog` obiektu, należy najpierw `CPageSetupDialog` utworzyć obiekt przy użyciu konstruktora. Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować `m_psd` dowolne wartości w członku danych, aby zainicjować wartości formantów okna dialogowego. Struktura [m_psd](#m_psd) jest typu PAGESETUPDLG.

Po zainicjowaniu kontrolek okna `DoModal` dialogowego należy wywołać funkcję elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na wybranie opcji drukowania. `DoModal`zwraca, czy użytkownik wybrał przycisk OK (IDOK) czy Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można `CPageSetupDialog`użyć kilku funkcji członkowskich `m_psd` lub uzyskać dostęp do elementu członkowskiego danych, aby pobrać informacje wprowadzone przez użytkownika.

> [!NOTE]
> Po odrzuceniu wspólnego okna dialogowego Ustawienia strony OLE wszelkie zmiany wprowadzone przez użytkownika nie zostaną zapisane przez strukturę. Do samej aplikacji należy zapisanie dowolnych wartości z tego okna dialogowego w stałej lokalizacji, takiej jak członek dokumentu lub klasy aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Wywołanie tej funkcji, aby skonstruować `CPageSetupDialog` obiekt.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Co najmniej jedna flaga umożliwia dostosowanie ustawień okna dialogowego. Wartości można łączyć za pomocą operatora bitowego OR. Wartości te mają następujące znaczenie:

- PSD_DEFAULTMINMARGINS Ustawia minimalne dopuszczalne szerokości marginesów strony na takie same, jak minimalne wartości drukarki. Ta flaga jest ignorowana, jeśli określono również flagi PSD_MARGINS i PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE Nie jest zaimplementowana.

- PSD_MINMARGINS Powoduje, że system używa wartości określonych `rtMinMargin` w członu jako minimalnej dopuszczalnej szerokości dla marginesów po lewej, górnej, prawej i dolnej. System uniemożliwia użytkownikowi wprowadzenie szerokości mniejszej niż określone minimum. Jeśli PSD_MINMARGINS nie jest określony, system ustawia minimalne dopuszczalne szerokości na dozwolone przez drukarkę.

- PSD_MARGINS Aktywuje obszar kontroli marginesu.

- PSD_INTHOUSANDTHSOFINCHES Powoduje, że jednostki okna dialogowego mają być mierzone w 1/1000 cala.

- PSD_INHUNDREDTHSOFMILLIMETERS Powoduje, że jednostki okna dialogowego mają być mierzone w 1/100 milimetra.

- PSD_DISABLEMARGINS Wyłącza kontrolki okna dialogowego marginesu.

- PSD_DISABLEPRINTER Wyłącza przycisk Drukarka.

- PSD_NOWARNING Zapobiega wyświetlaniu komunikatu ostrzegawczego, gdy nie ma drukarki domyślnej.

- PSD_DISABLEORIENTATION Wyłącza kontrolka okna dialogowego orientacji strony.

- PSD_RETURNDEFAULT Powoduje `CPageSetupDialog` zwracanie struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES,](/windows/win32/api/commdlg/ns-commdlg-devnames) które są inicjowane dla domyślnej drukarki systemowej bez wyświetlania okna dialogowego. Zakłada się, `hDevNames` że `hDevMode` oba i są NULL; w przeciwnym razie funkcja zwraca błąd. Jeśli domyślna drukarka systemowa jest obsługiwana przez stary sterownik drukarki (wcześniejszy niż Windows w wersji 3.0), zwracany jest tylko `hDevNames` systemowy sterownik; `hDevMode` ma wartość NULL.

- PSD_DISABLEPAPER Wyłącza kontrolka wyboru papieru.

- PSD_SHOWHELP Powoduje, że w oknie dialogowym jest pokazywanie przycisku Pomoc. Element `hwndOwner` członkowski nie może być null, jeśli ta flaga jest określona.

- PSD_ENABLEPAGESETUPHOOK Włącza funkcję haka określoną w . `lpfnSetupHook`

- PSD_ENABLEPAGESETUPTEMPLATE Powoduje, że system operacyjny tworzy okno dialogowe przy użyciu `hInstance` `lpSetupTemplateName`okna dialogowego z identyfikowanym przez i .

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE Wskazuje, że `hInstance` identyfikuje blok danych zawierający wstępnie załadowany szablon okna dialogowego. System ignoruje, `lpSetupTemplateName` jeśli ta flaga jest określona.

- PSD_ENABLEPAGEPAINTHOOK Włącza funkcję haka określoną w . `lpfnPagePaintHook`

- PSD_DISABLEPAGEPAINTING Wyłącza obszar rysowania w oknie dialogowym.

*pParentWnd*<br/>
Wskaźnik do obiektu nadrzędnego lub właściciela okna dialogowego.

### <a name="remarks"></a>Uwagi

Użyj funkcji [DoModal,](../../mfc/reference/cdialog-class.md#domodal) aby wyświetlić okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) i [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Obsługa nowo utworzonego kontekstu urządzenia drukarki (DC).

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog::DoModal

Wywołanie tej funkcji powoduje wyświetlenie okna dialogowego Typowe okno dialogowe Ustawienia strony OLE systemu Windows i umożliwienie użytkownikowi wybrania różnych opcji konfiguracji drukowania, takich jak marginesy drukowania, rozmiar i orientacja papieru oraz drukarka docelowa.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli funkcja IDCANCEL jest zwracana, należy wywołać funkcję Programu Windows [CommDlgExtendedError,](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL to stałe wskazujące, czy użytkownik wybrał przycisk OK, czy Anuluj.

### <a name="remarks"></a>Uwagi

Ponadto użytkownik może uzyskać dostęp do opcji konfiguracji drukarki, takich jak lokalizacja sieciowa i właściwości specyficzne dla wybranej drukarki.

Aby zainicjować różne opcje okna dialogowego Ustawienia strony, ustawiając elementy `m_psd` członkowskie `DoModal`struktury, należy to zrobić przed wywołaniem i po skonstruowaniu obiektu okna dialogowego. Po `DoModal`wywołaniu , wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje wprowadzone przez użytkownika w oknie dialogowym.

Jeśli chcesz propagować bieżące ustawienia wprowadzone przez użytkownika, nawiąż połączenie z [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Ta funkcja pobiera informacje `CPageSetupDialog` z obiektu i inicjuje i wybiera nową drukarkę DC z odpowiednimi atrybutami.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Przykład

  Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

Wywołanie tej `DoModal` funkcji po, aby pobrać nazwę aktualnie wybranej drukarki.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa urządzenia używana `CPageSetupDialog` przez obiekt.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać `CPageSetupDialog` informacje o kontekście urządzenia drukarki obiektu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura danych [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) która zawiera informacje o inicjowaniu urządzenia i środowisku sterownika wydruku. Należy odblokować pamięć pobraną przez tę strukturę za pomocą funkcji Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) która jest opisana w sdk systemu Windows.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog::GetDriverName

Wywołanie tej funkcji po wywołaniu [DoModal,](../../mfc/reference/cprintdialog-class.md#domodal) aby pobrać nazwę sterownika urządzenia drukarki zdefiniowanej przez system.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określanie nazwy sterownika zdefiniowanej przez system.

### <a name="remarks"></a>Uwagi

Użyj wskaźnika `CString` do obiektu `GetDriverName` zwróconego `lpszDriverName` jako wartość w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

Wywołanie tej funkcji `DoModal` po wywołaniu, aby pobrać marginesy sterownika urządzenia drukarki.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parametry

*lpRectMargins*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) lub [obiektu CRect,](../../atl-mfc-shared/reference/crect-class.md) który opisuje (w 1/1000 cali lub 1/100 mm) marginesy drukowania dla aktualnie wybranej drukarki. Przekaż null dla tego parametru, jeśli nie jesteś zainteresowany tym prostokątem.

*lpRectMinMargins*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który opisuje (w 1/1000 cali lub 1/100 mm) minimalne marginesy wydruku dla aktualnie wybranej drukarki. Przekaż null dla tego parametru, jeśli nie jesteś zainteresowany tym prostokątem.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Wywołanie tej funkcji powoduje pobranie rozmiaru papieru wybranego do drukowania.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) zawierający rozmiar papieru (w 1/1000 cali lub 1/100 mm) wybrany do drukowania.

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać nazwę aktualnie wybranego portu drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa aktualnie wybranego portu drukarki.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog::m_psd

Struktura typu PAGESETUPDLG, którego członkowie przechowują właściwości obiektu okna dialogowego.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CPageSetupDialog` obiektu, można `m_psd` użyć, aby ustawić różne aspekty `DoModal` okna dialogowego przed wywołaniem funkcji elementu członkowskiego.

Jeśli zmodyfikujesz `m_psd` element członkowski danych bezpośrednio, należy zastąpić wszelkie domyślne zachowanie.

Aby uzyskać więcej informacji na temat struktury [PAGESETUPDLG,](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) zobacz SDK systemu Windows.

Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

Wywoływana przez strukturę do rysowania obrazu ekranu drukowanej strony.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*nMessage (właswoić)*<br/>
Określa komunikat wskazujący obszar aktualnie rysowanej strony. Może być jedną z następujących czynności:

- WM_PSD_FULLPAGERECT Cały obszar strony.

- WM_PSD_MINMARGINRECT Bieżące minimalne marginesy.

- WM_PSD_MARGINRECT Bieżące marże.

- WM_PSD_GREEKTEXTRECT Zawartość strony.

- WM_PSD_ENVSTAMPRECT Obszar zarezerwowany dla reprezentacji znaczków pocztowych.

- WM_PSD_YAFULLPAGERECT obszar reprezentacji adresu zwrotnego. Ten obszar rozciąga się na krawędzie przykładowego obszaru strony.

*Lprect*<br/>
Wskaźnik do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [RECT](/windows/win32/api/windef/ns-windef-rect) zawierającego współrzędne obszaru rysunku.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli jest obsługiwana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten obraz jest następnie wyświetlany jako część wspólnego okna dialogowego Ustawienia strony OLE. Domyślna implementacja rysuje obraz strony tekstu.

Zastąd w tej funkcji należy dostosować rysunek określonego obszaru obrazu lub całego obrazu. Można to zrobić za pomocą **instrukcji switch** z **case** statements sprawdzanie wartości *nMessage*. Na przykład, aby dostosować renderowanie zawartości obrazu strony, można użyć następującego przykładowego kodu:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Należy pamiętać, że nie trzeba obsługiwać każdy przypadek *nMessage*. Można obsługiwać jeden składnik obrazu, kilka komponentów obrazu lub cały obszar.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog::PreDrawPage

Wywoływana przez strukturę przed narysowaniem obrazu ekranu drukowanej strony.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parametry

*wPaper*<br/>
Określa wartość wskazującą rozmiar papieru. Ta wartość może być jedną z **wartości DMPAPER_** wymienionych w opisie [devmode](/windows/win32/api/wingdi/ns-wingdi-devmodea) struktury.

*wFlags*<br/>
Wskazuje orientację papieru lub koperty oraz to, czy drukarka jest matrycą punktową, czy urządzeniem HPPCL (Hewlett Packard Printer Control Language). Ten parametr może mieć jedną z następujących wartości:

- 0x001 Papier w trybie poziomym (matryca punktowa)

- 0x003 Papier w trybie poziomym (HPPCL)

- 0x005 Papier w trybie pionowym (matryca punktowa)

- 0x007 Papier w trybie pionowym (HPPCL)

- Koperta 0x00b w trybie poziomym (HPPCL)

- Koperta 0x00d w trybie pionowym (matryca punktowa)

- 0x019 Koperta w trybie poziomym (matryca punktowa)

- 0x01f Koperta w trybie pionowym (matryca punktowa)

*pPSD*<br/>
Wskaźnik do `PAGESETUPDLG` struktury. Aby uzyskać więcej informacji na temat [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw), zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli jest obsługiwana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy dostosować rysunek obrazu. Jeśli zastąpisz tę funkcję i zwrócisz wartość PRAWDA, należy narysować cały obraz. Jeśli zastąpisz tę funkcję i zwrócisz FAŁSZ, cały obraz domyślny jest rysowany przez platformę.

## <a name="see-also"></a>Zobacz też

[Przykładowy program WORDPAD mfc](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
