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
ms.openlocfilehash: 721dd285760027c35ae93d89ec5bb3fde6e9ba11
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413454"
---
# <a name="cpagesetupdialog-class"></a>Klasa CPageSetupDialog

Hermetyzuje usługi świadczone przez wspólne okno dialogowe Ustawienia strony OLE Windows z obsługą dodatkowgoe ustawienie i modyfikowania marginesów wydruku.

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
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia do drukowania.|
|[CPageSetupDialog::DoModal](#domodal)|Zostanie wyświetlone okno dialogowe i umożliwia wybór użytkownika wykonującego.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Zwraca nazwę drukarki.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Zwraca bieżący DEVMODE drukarki.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Zwraca sterownik drukarki.|
|[CPageSetupDialog::GetMargins](#getmargins)|Zwraca bieżące ustawienia marginesów drukarki.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Zwraca rozmiar papieru drukarki.|
|[CPageSetupDialog::GetPortName](#getportname)|Zwraca nazwę portu wyjściowego.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Metoda wywoływana przez platformę, by renderować obraz ekranu z wydrukowaną stroną.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Wywoływane przez platformę przed renderowaniem obrazu ekranu z wydrukowaną stroną.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Struktury używane w celu dostosowania `CPageSetupDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa jest przeznaczona do miejsce w oknie dialogowym Ustawienia wydruku.

Aby użyć `CPageSetupDialog` obiektów, najpierw utwórz obiekt przy użyciu `CPageSetupDialog` konstruktora. Gdy okno dialogowe został skonstruowany, można ustawić lub zmodyfikować dowolne wartości na `m_psd` element członkowski danych można zainicjować wartości formantów w oknie dialogowym. [M_psd](#m_psd) struktury jest typu PAGESETUPDLG.

Po inicjalizacji formantów okna dialogowego, należy wywołać `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie opcji drukowania. `DoModal` Zwraca, czy użytkownik wybrał przycisk OK (IDOK) lub anulować (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można użyć kilku `CPageSetupDialog`dla funkcji składowych lub dostępu `m_psd` element członkowski danych, aby pobrać wprowadzania informacji przez użytkownika.

> [!NOTE]
>  Po odrzuceniu wspólne okno dialogowe Ustawienia strony OLE wszelkie zmiany wprowadzone przez użytkownika nie zostaną zapisane przez platformę. Jest aplikacji zostaną zapisane wszystkie wartości z tego okna dialogowego stałe lokalizacji, na przykład element członkowski dokumentu aplikacji lub klasy aplikacji.

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

Wywołaj tę funkcję, aby skonstruować `CPageSetupDialog` obiektu.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Co najmniej jeden flagi używane do dostosowywania ustawień w oknie dialogowym. Wartości można łączyć, używając operatora bitowego OR. Te wartości mają następujące znaczenie:

- PSD_DEFAULTMINMARGINS określa minimalne szerokości dozwoloną dla marginesy strony, aby być taka sama jak minimalnych drukarki. Ta flaga jest ignorowana, jeśli określono też flagi PSD_MARGINS i PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE nie, zaimplementowane.

- PSD_MINMARGINS powoduje, że system ma używać wartości określone w `rtMinMargin` składową jako minimalne szerokości dozwolone po lewej stronie, górnej, prawej strony i dolny marginesy. System uniemożliwia użytkownikowi wprowadzanie szerokości, która jest mniejsza niż określona wartość minimalna. Jeśli nie określono PSD_MINMARGINS, system ustawia minimalne szerokości dopuszczalny rozmiar te dozwolone przez drukarki.

- PSD_MARGINS aktywuje obszar kontroli marginesu.

- PSD_INTHOUSANDTHSOFINCHES powoduje, że jednostki okna dialogowego mierzony w 1/1000 cala.

- PSD_INHUNDREDTHSOFMILLIMETERS powoduje, że jednostki okna dialogowego mierzony w 1/100 milimetra.

- PSD_DISABLEMARGINS wyłącza formantów okna dialogowego margines.

- PSD_DISABLEPRINTER wyłącza przycisk drukarki.

- PSD_NOWARNING zapobiega wyświetlaniu po drukarka domyślna komunikat ostrzegawczy.

- PSD_DISABLEORIENTATION wyłącza formantu okna dialogowego orientacja strony.

- Powoduje, że PSD_RETURNDEFAULT `CPageSetupDialog` do zwrócenia [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktur, które są inicjowane dla domyślną drukarkę systemu bez wyświetlania okna dialogowego. Zakłada się, że oba `hDevNames` i `hDevMode` mają wartość NULL; w przeciwnym razie funkcja zwraca błąd. Jeśli zostanie użyta drukarka domyślna systemu jest obsługiwany przez stary sterownika drukarki (starszych niż Windows w wersji 3.0 lub nowszej), tylko `hDevNames` jest zwracana; `hDevMode` ma wartość NULL.

- PSD_DISABLEPAPER wyłącza kontrolkę wyboru papieru.

- PSD_SHOWHELP powoduje, że okno dialogowe, aby wyświetlać przycisk Pomoc. `hwndOwner` Element członkowski nie może być NULL, jeśli ta flaga jest określony.

- PSD_ENABLEPAGESETUPHOOK włącza funkcję podłączania określone w `lpfnSetupHook`.

- PSD_ENABLEPAGESETUPTEMPLATE powoduje, że system operacyjny do utworzenia okna dialogowego za pomocą szablonu dialogowego identyfikowane przez `hInstance` i `lpSetupTemplateName`.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE wskazuje, że `hInstance` identyfikuje zawierający szablonu okna dialogowego załadowanych bloku danych. System zignoruje `lpSetupTemplateName` Jeśli ta flaga jest określony.

- PSD_ENABLEPAGEPAINTHOOK włącza funkcję podłączania określone w `lpfnPagePaintHook`.

- PSD_DISABLEPAGEPAINTING wyłącza obszaru rysowania przedstawiający okno dialogowe.

*pParentWnd*<br/>
Wskaźnik do nadrzędnej lub właściciela okno dialogowe.

### <a name="remarks"></a>Uwagi

Użyj [DoModal](../../mfc/reference/cdialog-class.md#domodal) funkcję, aby wyświetlić okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Tworzy kontekst urządzenia drukarki z [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) i [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonego drukarki kontekstu urządzenia (DC).

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Wywołaj tę funkcję, aby wyświetlić wspólne okno dialogowe Ustawienia strony OLE Windows i Zezwalaj użytkownikowi na wybranie różne opcje konfiguracji wydruku, takich jak marginesy drukowania, rozmiar i orientację papieru i drukarkę docelową.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli zwracana jest IDCANCEL, wywołaj Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcję, aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.

### <a name="remarks"></a>Uwagi

Ponadto użytkownik ma dostęp opcje instalacji drukarki, takie jak lokalizacja sieciowa i właściwości specyficzne dla wybranych drukarek.

Jeśli chcesz zainicjować różne opcje Ustawienia strony w oknie dialogowym, ustawiając członkowie `m_psd` struktury, należy to zrobić przed wywołaniem `DoModal`, i po jest konstruowany obiektu okna dialogowego. Po wywołaniu `DoModal`, wywoływanie innego członka funkcji, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

Propagacja bieżące ustawienia wprowadzone przez użytkownika, należy po wywołaniu [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Ta funkcja przyjmuje informacje z `CPageSetupDialog` obiektu i inicjuje i wybiera nowej drukarki kontrolera domeny przy użyciu odpowiednich atrybutów.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Przykład

  Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

Wywołaj tę funkcję, po `DoModal` można pobrać nazwę aktualnie wybrane drukarki.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa urządzenia używane przez `CPageSetupDialog` obiektu.

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

Wywołaj tę funkcję, po wywołaniu `DoModal` można pobrać informacji o kontekście urządzenie drukarki `CPageSetupDialog` obiektu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Wartość zwracana

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury danych, który zawiera informacje na temat inicjowania urządzenia i środowisko sterownika drukarki. Musisz odblokować pamięć podjęte przez tę strukturę z Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) funkcji, która jest opisana w zestawie Windows SDK.

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

Wywołaj tę funkcję, po wywołaniu [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) można pobrać nazwę sterownika drukarki zdefiniowaną przez system.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` określający nazwę sterownika zdefiniowaną przez system.

### <a name="remarks"></a>Uwagi

Za pomocą wskaźnika do `CString` obiektu zwróconego przez `GetDriverName` jako wartość `lpszDriverName` w wywołaniu [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

Wywołaj tę funkcję, po wywołaniu `DoModal` można pobrać marginesy sterownika urządzenia.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parametry

*lpRectMargins*<br/>
Wskaźnik do [Prostokąt](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który opisuje (w calach 1/1000 lub mm 1/100) marginesów wydruku dla aktualnie wybranej drukarki. Przekaż wartość NULL dla tego parametru, jeśli nie jesteś zainteresowany prostokąta.

*lpRectMinMargins*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt, który opisuje (w calach 1/1000 lub mm 1/100), minimalna marginesów wydruku dla aktualnie wybranej drukarki. Przekaż wartość NULL dla tego parametru, jeśli nie jesteś zainteresowany prostokąta.

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

Wywołaj tę funkcję, by pobrać rozmiar papieru wybrane do drukowania.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt zawierający rozmiar papieru (w calach 1/1000 lub mm 1/100) wybrane do drukowania.

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

Wywołaj tę funkcję, po wywołaniu `DoModal` pobrać nazwy portu aktualnie wybranego drukarki.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa portu aktualnie wybranego drukarki.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Struktura typu PAGESETUPDLG, której członkowie przechowywania właściwości obiektu okna dialogowego.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Uwagi

Po konstruowanie `CPageSetupDialog` obiektu, możesz użyć `m_psd` można ustawić różne aspekty okno dialogowe przed wywołaniem `DoModal` funkcja elementu członkowskiego.

Jeśli zmodyfikujesz `m_psd` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.

Aby uzyskać więcej informacji na temat [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda) struktury, zobacz zestaw Windows SDK.

Zobacz przykład [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

Metoda wywoływana przez platformę, by narysować obrazu ekranu z wydrukowaną stroną.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*nkomunikat*<br/>
Określa komunikat, wskazujący obszarze strony obecnie rysowania. Może to być jeden z następujących elementów:

- WM_PSD_FULLPAGERECT obszaru całej strony.

- Bieżący WM_PSD_MINMARGINRECT marginesy minimalnej.

- Marginesy WM_PSD_MARGINRECT bieżącego.

- WM_PSD_GREEKTEXTRECT zawartość strony.

- Obszar WM_PSD_ENVSTAMPRECT zarezerwowane dla reprezentacji znaczka.

- Obszar WM_PSD_YAFULLPAGERECT dla reprezentacji adres zwrotny. Rozszerza ten obszar do krawędzi obszaru przykładowej strony.

*lprect —*<br/>
Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [Prostokąt](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) obiekt, który zawiera współrzędne obszaru.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obsługiwane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten obraz zostanie wyświetlona jako część wspólne okno dialogowe Ustawienia strony OLE. Domyślna implementacja Rysuje obraz strony tekstu.

Należy przesłonić tę funkcję, aby dostosować rysunku określonym obszarze obraz lub całego obrazu. Można to zrobić za pomocą **Przełącz** instrukcję, określając **przypadek** instrukcji, sprawdzając wartość *nkomunikat*. Na przykład: Aby dostosować renderowania zawartości obraz strony, należy użyć poniższy przykład kodu:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Należy pamiętać, że nie trzeba do obsługi każdego przypadku *nkomunikat*. Można obsługiwać jeden składnik obrazu kilka składników, obrazu lub całego obszaru.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Wywoływane przez platformę przed narysowaniem obrazu ekranu z wydrukowaną stroną.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parametry

*wPaper*<br/>
Określa wartość, która wskazuje rozmiar papieru. Ta wartość może być jednym z **DMPAPER_** wartości wymienionych w opisie [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury.

*wFlags*<br/>
Określa orientację papieru lub koperty, oraz czy drukarka jest-Mozaika lub urządzenie HPPCL (Hewlett Packard drukarki kontroli Language). Ten parametr może mieć jedną z następujących wartości:

- 0x001 papier w trybie poziomym (Mozaika)

- 0x003 papier w trybie poziomym (HPPCL)

- 0x005 papier w trybie portret (Mozaika)

- 0x007 papier w trybie portret (HPPCL)

- 0x00b koperta w trybie krajobraz (HPPCL)

- 0x00d koperta w trybie portret (Mozaika)

- 0x019 koperta w trybie krajobraz (Mozaika)

- 0x01f koperta w trybie portret (Mozaika)

*pPSD*<br/>
Wskaźnik do `PAGESETUPDLG` struktury. Aby uzyskać więcej informacji na temat [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda), zobacz dokumentację Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obsługiwane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować rysowania obrazu. Jeśli możesz przesłonić tę funkcję i zwraca wartość TRUE, należy narysować całego obrazu. Jeśli przesłonić tę funkcję i zwraca wartość FALSE, cały domyślnego obrazu jest rysowana przez platformę.

## <a name="see-also"></a>Zobacz też

[Próbki MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)



