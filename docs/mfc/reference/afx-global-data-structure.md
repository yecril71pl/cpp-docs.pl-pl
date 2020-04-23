---
title: AFX_GLOBAL_DATA — Struktura
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 0361d535a31526c5f7b79fdd4eab046dad0435cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752868"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA — Struktura

Struktura `AFX_GLOBAL_DATA` zawiera pola i metody, które są używane do zarządzania strukturą lub dostosować wygląd i zachowanie aplikacji.

## <a name="syntax"></a>Składnia

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Konstruuje `AFX_GLOBAL_DATA` strukturę.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::Oczyszczanie](#cleanup)|Zwalnia zasoby, które są przydzielane przez platformę, takie jak pędzle, czcionki i biblioteki DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Tworzy transformację obrotu, która obraca się o określony kąt wokół określonego punktu.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Rysuje tło nadrzędnego formantu w określonym obszarze.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Rysuje określony tekst w stylu wizualnym określonego motywu.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Usuwa określoną parę znaczników XML z określonego buforu.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Pobiera bieżący kolor określonego elementu interfejsu użytkownika.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Zwraca wskaźnik do `ID2D1Factory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Pobiera wstępnie zdefiniowany kursor, który przypomina rękę i którego `IDC_HAND`identyfikator jest .|
|[AFX_GLOBAL_DATA::GetITaskbarLista](#getitaskbarlist)|Tworzy i przechowuje w danych globalnych wskaźnik do interfejsu ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Tworzy i przechowuje w danych globalnych wskaźnik do interfejsu ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Pobiera metryki skojarzone z obszarem nieklientów niemmializowanych okien.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Określa położenie pasków automatycznego ukrywania powłoki.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Pobiera wysokość znaków tekstowych w bieżącej czcionce.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Zwraca wskaźnik do `IWICImagingFactory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Zwraca wskaźnik do `IDWriteFactory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|`D2D`Inicjuje `DirectWrite`i `WIC` fabrykuje. Wywołanie tej metody przed zainicjowaniem okna głównego.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowe są obsługiwane.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Określa, `D2D` czy został zainicjowany.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Zapewnia prosty sposób wywołania metody Windows [DwmIsCompositionEnabled.](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled)|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Wskazuje, czy obrazy są obecnie wyświetlane w wysokim kontraście.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Wykrywa bieżący stan animacji menu pulpitu i funkcji autohide na pasku zadań.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Rejestruje określoną klasę okna MFC.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Zwalnia interfejsy uzyskane za pośrednictwem metod GetITaskbarList i GetITaskbarList3.|
|[AFX_GLOBAL_DATA::Wznów](#resume)|Ponownie inicjuje wewnętrzne wskaźniki funkcji, które uzyskują dostęp do metod obsługi motywów systemu Windows [i stylów wizualnych](/windows/win32/Controls/visual-styles-overview).|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Zapewnia prosty sposób wywołania metody [Windows SetLayeredWindowAttributes.](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Tworzy określoną czcionkę logiczną.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Tworzy i inicjuje obiekt elementu powłoki z nazwy analizy.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes logiczne czcionki, które są używane przez strukturę.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicjuje kolory, głębię kolorów, pędzle, pióra i obrazy, które są używane przez strukturę.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySport](#enableaccessibilitysupport)|Włącza lub wyłącza obsługę aktywnego dostępu firmy Microsoft. Active Accessibility zapewnia niezawodne metody ujawniania informacji o elementach interfejsu użytkownika.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Wskazuje, czy obsługa aktywnego dostępu firmy Microsoft jest włączona.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportDostępne](#iswindowslayersupportavailable)|Wskazuje, czy system operacyjny obsługuje okna warstwowe.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Wskazuje, czy bieżący system operacyjny obsługuje mieszanie alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Wskazuje, czy aplikacja jest wykonywana w systemie operacyjnym Windows 7 czy wyższym|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Określa kolor gradientu aktywnego podpisu. Zazwyczaj używane do okienek dokowania.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Określa kolor gradientu nieaktywnego podpisu aktywnego. Zazwyczaj używane do okienek dokowania.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Wskazuje, czy struktura używa wstępnie zdefiniowanych ikon kolorów 32-bitowych lub ikon o niższej rozdzielczości.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Wskazuje, czy czcionka systemowa jest używana dla menu, pasków narzędzi i wstążek.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Przechowuje uchwyt dla kursora ręcznego.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Przechowuje uchwyt dla poziomego kursora stretch.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Przechowuje uchwyt dla pionowego kursora stretch.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Przechowuje uchwyt dla ikony narzędzia.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Określa przesunięcie od lewego paska narzędzi autouszudania do lewej strony paska dokowania.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Określa odstęp między paskami narzędzi autouzusku.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Określa grubość ramki przeciągania używanej do komunikowania stanu zadokowanego.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Określa grubość ramki przeciągania używanej do komunikowania stanu przestawnego.|

### <a name="remarks"></a>Uwagi

Większość danych w `AFX_GLOBAL_DATA` strukturze jest inicjowana po uruchomieniu aplikacji.

### <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Wskazuje, czy system operacyjny obsługuje mieszanie alfa.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Uwagi

WARTOŚĆ TRUE oznacza, że obsługiwane jest mieszanie alfa; w przeciwnym razie FALSE.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a>AFX_GLOBAL_DATA::Oczyszczanie

Zwalnia zasoby, które są przydzielane przez platformę, takie jak pędzle, czcionki i biblioteki DLL.

```cpp
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Tworzy transformację obrotu, która obraca się o określony kąt wokół określonego punktu.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parametry

*kąt*<br/>
Kąt obrotu zgodnie z ruchem wskazówek zegara w stopniach.

*Centrum*<br/>
Punkt, o którym ma się obracać.

*Macierzy*<br/>
Gdy ta metoda zwraca, zawiera nową transformację obrotu. Należy przydzielić magazyn dla tego parametru.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli zakończy się pomyślnie, lub wartość błędu w inny sposób.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground

Rysuje tło nadrzędnego formantu w określonym obszarze.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Wskaźnik do okna formantu.

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Lprect*<br/>
[w] Wskaźnik do prostokąta, który ogranicza obszar do rysowania. Wartością domyślną jest NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass

Rysuje określony tekst w stylu wizualnym określonego motywu.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*hTheme*<br/>
[w] Dojem do danych motywu okna lub NULL. Struktura używa określonego motywu do rysowania tekstu, jeśli ten parametr nie jest null i motywy są obsługiwane. W przeciwnym razie ramach nie używa motywu do rysowania tekstu.

Użyj [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) metody, aby utworzyć HTHEME.

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*identyfikator iPartId*<br/>
[w] Część kontrolna, która ma pożądany wygląd tekstu. Aby uzyskać więcej informacji, zobacz kolumnę Części tabeli w [obszarze Części i stany](/windows/win32/controls/parts-and-states). Jeśli ta wartość wynosi 0, tekst jest rysowany czcionką domyślną lub czcionką zaznaczoną w kontekście urządzenia.

*Identyfikator iStateId*<br/>
[w] Stan formantu, który ma pożądany wygląd tekstu. Aby uzyskać więcej informacji, zobacz kolumnę Stany tabeli w [części i stany](/windows/win32/controls/parts-and-states).

*strText (tekst)*<br/>
[w] Tekst do narysowania.

*Rect*<br/>
[w] Obwiednia obszaru, w którym rysowany jest określony tekst.

*Dwflags*<br/>
[w] Bitowa kombinacja (OR) flag określających sposób rysowania określonego tekstu.

Jeśli *hTheme* parametr `NULL` jest lub jeśli motywy nie są obsługiwane i włączone, *nFormat* parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metoda opisuje prawidłowe flagi. Jeśli motywy są obsługiwane, *dwFlags* parametr [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) metody opisuje prawidłowe flagi.

*rozmiar nGlowSize*<br/>
[w] Rozmiar efektu blasku rysowanego na tle przed narysowaniem określonego tekstu. Wartość domyślna to 0.

*clrTekst*<br/>
[w] Kolor, w którym rysowany jest określony tekst. Wartością domyślną jest kolor domyślny.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli motyw jest używany do rysowania określonego tekstu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Motyw definiuje styl wizualny aplikacji. Motyw nie jest używany do rysowania tekstu, jeśli parametr *hTheme* ma wartość NULL lub jeśli metoda [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) nie jest obsługiwana lub jeśli [kompozycja Menedżera okien pulpitu](/windows/win32/dwm/dwm-overview) (DWM) jest wyłączona.

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySport

Włącza lub wyłącza obsługę aktywnego dostępu firmy Microsoft.

```cpp
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] TRUE, aby włączyć obsługę ułatwień dostępu; FALSE, aby wyłączyć obsługę ułatwień dostępu. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Active Accessibility to technologia oparta na technologii COM, która usprawnia współpracę programów i systemu operacyjnego Windows z produktami technologii wspomagających. Zapewnia niezawodne metody ujawniania informacji o elementach interfejsu użytkownika. Jednak nowszy model ułatwień dostępu o nazwie Automatyzacja interfejsu użytkownika firmy Microsoft jest teraz dostępny. Aby zapoznać się z porównaniem tych dwóch technologii, zobacz [Automatyzacja interfejsu użytkownika i aktywna dostępność firmy Microsoft](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Użyj [metody AFX_GLOBAL_DATA::IsAccessibilitySupport,](#isaccessibilitysupport) aby ustalić, czy obsługa aktywnych ułatwień dostępu firmy Microsoft jest włączona.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag

Usuwa określoną parę znaczników XML z określonego buforu.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parametry

*strBuffer (strBuffer)*<br/>
[w] Bufor tekstu.

*lpszTag (lpszTag)*<br/>
[w] Nazwa pary otwierania i zamykania znaczników XML.

*strTag (tag)*<br/>
[na zewnątrz] Gdy ta metoda zwraca, *strTag* parametr zawiera tekst, który znajduje się między otwierania i zamykania tagów XML, które są nazwane przez *lpszTag* parametru. Każdy odstęp wiodący lub końcowy jest przycinany z wyniku.

*bIsCharsList*<br/>
[w] PRAWDA, aby przekonwertować symbole znaków ucieczki w parametrze *strTag* na rzeczywiste znaki ucieczki; FALSE, aby nie przeprowadzać konwersji. Wartością domyślną jest FAŁSZ. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Para znaczników XML składa się z nazwanych znaczników otwierania i zamykania, które wskazują początek i koniec przebiegu tekstu w określonym buforze. Parametr *strBuffer* określa bufor, a parametr *lpszTag* określa nazwę znaczników XML.

Za pomocą symboli w poniższej tabeli należy zakodować zestaw znaków ucieczki w określonym buforze. Określ wartość PRAWDA dla parametru *bIsCharsList,* aby przekonwertować symbole w parametrze *strTag* na rzeczywiste znaki ucieczki. W poniższej tabeli użyto makra [_T()](../../c-runtime-library/data-type-mappings.md) do określenia znaków symbolu i znaków ucieczki.

|Symbol|Znak ucieczki|
|------------|----------------------|
|_T("\\\t")|_T("\t")|
|_T("\\\n")|_T("\n")|
|_T("\\\r")|_T("\r")|
|_T("\\\b")|_T("\b")|
|_T("LT")|_T("\<")|
|_T("GT")|_T(">")|
|_T("AMP")|_T("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor

Pobiera bieżący kolor określonego elementu interfejsu użytkownika.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parametry

*nKolor*<br/>
[w] Wartość określająca element interfejsu użytkownika, którego kolor jest pobierany. Aby uzyskać listę prawidłowych wartości, zobacz *parametr nIndex* [metody GetSysColor.](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB określonego elementu interfejsu użytkownika. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="remarks"></a>Uwagi

Jeśli parametr *nColor* znajduje się poza zakresem, zwracana wartość wynosi zero. Ponieważ zero jest również prawidłową wartością RGB, nie można użyć tej metody, aby określić, czy kolor systemu jest obsługiwany przez bieżący system operacyjny. Zamiast tego należy użyć [GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) metody, która zwraca null, jeśli kolor nie jest obsługiwany.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

Zwraca wskaźnik do interfejsu ID2D1Factory, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Factory, jeśli utworzenie fabryki zakończy się pomyślnie, lub NULL, jeśli tworzenie nie powiedzie się lub bieżącego systemu operacyjnego nie mają obsługi D2D.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

Pobiera wstępnie zdefiniowany kursor, który przypomina rękę i którego identyfikator jest IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora ręcznego.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics

Pobiera metryki skojarzone z obszarem nieklientów niemmializowanych okien.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parametry

*Informacji*<br/>
[w, na zewnątrz] Struktura [NONCLIENTMETRICS zawierająca](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) skalowalne metryki skojarzone z obszarem nieklientalnym niemamionizowanego okna.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

Pobiera wysokość znaków tekstowych w bieżącej czcionce.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Bhorz*<br/>
[w] PRAWDA, aby pobrać wysokość znaków, gdy tekst jest uruchamiany w poziomie; FAŁSZ, aby pobrać wysokość znaków, gdy tekst jest uruchamiany w pionie. Wartością domyślną jest PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Wysokość bieżącej czcionki, która jest mierzona od jej rosnąco do jej malejąco.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

Zwraca wskaźnik do interfejsu IWICImagingFactory, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IWICImagingFactory, jeśli utworzenie fabryki zakończy się pomyślnie, lub NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący system operacyjny nie mają obsługi WIC.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

Zwraca wskaźnik do interfejsu IDWriteFactory, który jest przechowywany w danych globalnych. Jeśli interfejs nie jest inicjowany, jest tworzony i ma parametry domyślne.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteFactory, jeśli utworzenie fabryki zakończy się pomyślnie, lub NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący system operacyjny nie ma obsługi DirectWrite.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

Inicjuje fabryki D2D, DirectWrite i WIC. Wywołanie tej metody przed zainicjowaniem okna głównego.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFaktoryp*<br/>
Model wątków fabryki D2D i zasobów, które tworzy.

*writeFactoryType (Typ danych)*<br/>
Wartość określająca, czy obiekt fabryczny zapisu będzie współużytkowany, czy izolowany

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli fabryki były intilalizrd, FALSE - w przeciwnym razie

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowe są obsługiwane.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obsługiwane są wstępnie zdefiniowane ikony 32-bitowe; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli struktura obsługuje wbudowane ikony 32-bitowe i jeśli system operacyjny obsługuje 16 bitów na piksel lub więcej, a obrazy nie są wyświetlane w wysokim kontraście.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport

Wskazuje, czy obsługa aktywnego dostępu firmy Microsoft jest włączona.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obsługa ułatwień dostępu jest włączona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Microsoft Active Accessibility był wcześniejszym rozwiązaniem do tworzenia aplikacji dostępnych. Automatyzacja interfejsu użytkownika firmy Microsoft to nowy model ułatwień dostępu dla systemu Microsoft Windows, który ma na celu zaspokojenie potrzeb produktów technologii wspomagających i zautomatyzowanych narzędzi testujących.

Użyj [metody AFX_GLOBAL_DATA::EnableAccessibilitySupport,](#enableaccessibilitysupport) aby włączyć lub wyłączyć obsługę aktywnych ułatwień dostępu.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized

Określa, czy D2D został zainicjowany

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli D2D został zainicjowany; w przeciwnym razie FALSE.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Zapewnia prosty sposób wywołania metody Windows [DwmIsCompositionEnabled.](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled)

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli [kompozycja Menedżera okien pulpitu](/windows/win32/dwm/dwm-overview) (DWM) jest włączona; w przeciwnym razie FALSE.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Wskazuje, czy obrazy są obecnie wyświetlane w wysokim kontraście.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obrazy są obecnie wyświetlane w trybie wysokiego kontrastu w czerni lub bieli; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W trybie czarnego wysokiego kontrastu krawędzie skierowane w stronę światła są białe, a tło czarne. W trybie białego wysokiego kontrastu krawędzie skierowane w stronę światła są czarne, a tło białe.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportDostępne

Wskazuje, czy system operacyjny obsługuje okna warstwowe.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obsługiwane są okna warstwowe; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli obsługiwane są okna warstwowe, inteligentne znaczniki *dokowania* używają okien warstwowych.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Wskazuje, czy struktura używa wstępnie zdefiniowanych ikon kolorów 32-bitowych lub ikon o niższej rozdzielczości.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Uwagi

FUNKCJA TRUE określa, że struktura używa ikon kolorów 32-bitowych; FALSE określa ikony niższej rozdzielczości. Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do TRUE.

Ten element członkowski musi być ustawiony podczas uruchamiania aplikacji.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

Wskazuje, czy czcionka systemowa jest używana dla menu, pasków narzędzi i wstążek.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Uwagi

TRUE określa użycie czcionki systemowej; w przeciwnym razie FALSE. Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do FALSE.

Testowanie tego elementu członkowskiego nie jest jedynym sposobem dla struktury, aby określić czcionkę do użycia. Metoda `AFX_GLOBAL_DATA::UpdateFonts` testuje również czcionki domyślne i alternatywne, aby określić, jakie style wizualne są dostępne do zastosowania do menu, pasków narzędzi i wstążek.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

Przechowuje uchwyt dla kursora ręcznego.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

Przechowuje uchwyt dla poziomego kursora stretch.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

Przechowuje uchwyt dla pionowego kursora stretch.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

Przechowuje uchwyt dla ikony narzędzia.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Określa przesunięcie od lewego paska narzędzi autouszudania do lewej strony paska dokowania.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Uwagi

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do 4 pikseli.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Określa odstęp między paskami narzędzi autouzusku.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Uwagi

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do 14 pikseli.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Określa grubość ramki przeciągania używanej do wskazania stanu zadokowanego.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Uwagi

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do 3 pikseli.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Określa grubość ramki przeciągania używanej do wskazania stanu przestawnego.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Uwagi

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicjuje ten element członkowski do 4 pikseli.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange

Wykrywa bieżący stan animacji menu pulpitu i funkcji autohide na pasku zadań.

```cpp
void OnSettingChange();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia zmienne framework do stanu niektórych atrybutów pulpitu użytkownika. Ta metoda wykrywa bieżący stan animacji menu, zanikania menu i funkcji autohide paska zadań.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass

Rejestruje określoną klasę okna MFC.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parametry

*lpszClassNamePrefix*<br/>
[w] Nazwa klasy okna do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

Kwalifikowana nazwa zarejestrowanej klasy, jeśli ta metoda powiedzie się; w przeciwnym razie [wyjątek zasobu](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Uwagi

Zwracana wartość jest listą rozdzielaną dwukropkiem ciągu parametru *lpszClassNamePrefix* oraz reprezentacje tekstu szesnastowego uchwytów bieżącego wystąpienia aplikacji; kursor aplikacji, który jest kursorem strzałki, którego identyfikator jest IDC_ARROW; i pędzel tła. Aby uzyskać więcej informacji na temat rejestrowania klas okien MFC, zobacz [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="afx_global_dataresume"></a><a name="resume"></a>AFX_GLOBAL_DATA::Wznów

Ponownie inicjuje wewnętrzne wskaźniki funkcji, które uzyskują dostęp do metod, które obsługują motywy systemu Windows i style wizualne.

```
BOOL Resume();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE. W trybie debugowania ta metoda potwierdza, jeśli ta metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy struktura odbiera [komunikat WM_POWERBROADCAST.](/windows/win32/Power/wm-powerbroadcast)

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib

Zapewnia prosty sposób wywołania metody [Windows SetLayeredWindowAttributes.](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna warstwowego.

*klawisz crKey*<br/>
[w] Klucz koloru przezroczystości używany przez [Menedżera okien pulpitu](/windows/win32/dwm/dwm-overview) do tworzenia okna warstwowego.

*bAlfa*<br/>
[w] Wartość alfa, która jest używana do opisania krycia okna warstwowego.

*Dwflags*<br/>
[w] Bitowe połączenie (OR) flag, które określają, które parametry metody do użycia. Określ LWA_COLORKEY, aby jako kolor przezroczystości był używany parametr *crKey.* Określ LWA_ALPHA, aby użyć parametru *bAlpha* do określenia krycia okna warstwowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont

Tworzy określoną czcionkę logiczną.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
[w] Wskaźnik do struktury zawierającej atrybuty czcionki.

*Bhorz*<br/>
[w] PRAWDA, aby określić, że tekst jest uruchamiany w poziomie; FAŁSZ, aby określić, że tekst jest uruchamiany w pionie.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE. W trybie debugowania ta metoda potwierdza, jeśli ta metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy poziomą czcionkę regularną, podkreśloną czcionkę i pogrubioną czcionkę używaną w domyślnych elementach menu. Ta metoda opcjonalnie tworzy zwykłą czcionkę pionową. Aby uzyskać więcej informacji na temat czcionek logicznych, zobacz [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts

Reintializes logiczne czcionki, które są używane przez strukturę.

```cpp
void UpdateFonts();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na `CFont::CreateFontIndirect`temat czcionek logicznych, zobacz .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors

Inicjuje kolory, głębię kolorów, pędzle, pióra i obrazy, które są używane przez strukturę.

```cpp
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

Wskazuje, czy aplikacja jest wykonywana w systemie Windows 7 lub nowszym.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient

Określa kolor gradientu aktywnego podpisu. Zazwyczaj używane do okienek dokowania.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Określa kolor gradientu nieaktywnego podpisu. Zazwyczaj używane do okienek dokowania.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarLista

Tworzy i przechowuje w danych `ITaskBarList` globalnych wskaźnik do interfejsu.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `ITaskbarList` interfejsu, jeśli utworzenie obiektu listy paska zadań zakończy się pomyślnie; NULL, jeśli tworzenie nie powiedzie się lub jeśli bieżący system operacyjny jest mniejszy niż Windows 7.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3

Tworzy i przechowuje w danych `ITaskBarList3` globalnych wskaźnik do interfejsu.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `ITaskbarList3` interfejsu, jeśli utworzenie obiektu listy paska zadań zakończy się pomyślnie; NULL, jeśli tworzenie nie powiedzie się lub jeśli bieżący system operacyjny jest mniejszy niż Windows 7.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars

Określa położenie pasków automatycznego ukrywania powłoki.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita z zakodowanymi flagami określającymi pozycje automatycznego ukrywania pasków. Może łączyć następujące wartości: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Zwalnia interfejsy uzyskane `GetITaskbarList` `GetITaskbarList3` za pośrednictwem i metod.

```cpp
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Tworzy i inicjuje obiekt elementu powłoki z nazwy analizy.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parametry

*PSZPath*<br/>
[w] Wskaźnik do nazwy wyświetlanej.

*Pbc*<br/>
Wskaźnik do kontekstu powiązania, który kontroluje operację analizowania.

*Riid*<br/>
Odwołanie do identyfikatora interfejsu.

*Ppv*<br/>
[na zewnątrz] Gdy ta funkcja powróci, zawiera wskaźnik interfejsu żądany w *riid*. Zazwyczaj będzie `IShellItem` to `IShellItem2`lub .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli zakończy się pomyślnie; wartość błędu w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md)<br/>
[Colorref](/windows/win32/gdi/colorref)<br/>
[Części i stany](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawTekst](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx (Edycja ThemeTextEx)](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Menedżer okien pulpitu](/windows/win32/dwm/dwm-overview)<br/>
[Włączanie i sterowanie kompozycją DWM](/windows/win32/dwm/composition-ovw)<br/>
[Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[Funkcja GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[Szczotka GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Struktura NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass ( AfxRegisterClass )](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceEkcepta](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowPrzywujeniewłasie](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
