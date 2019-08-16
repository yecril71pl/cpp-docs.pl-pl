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
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
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
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507753"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA — Struktura

`AFX_GLOBAL_DATA` Struktura zawiera pola i metody, które są używane do zarządzania strukturą lub dostosowywania wyglądu i zachowania aplikacji.

## <a name="syntax"></a>Składnia

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|`AFX_GLOBAL_DATA` Tworzy strukturę.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA:: CleanUp](#cleanup)|Zwalnia zasoby, które są przydzielone przez platformę, takie jak pędzle, czcionki i biblioteki DLL.|
|[AFX_GLOBAL_DATA::D 2D1MakeRotateMatrix](#d2d1makerotatematrix)|Tworzy transformację rotacji, która obraca się o określony kąt wokół określonego punktu.|
|[AFX_GLOBAL_DATA::D rawParentBackground](#drawparentbackground)|Rysuje tło elementu nadrzędnego kontrolki w określonym obszarze.|
|[AFX_GLOBAL_DATA::D rawTextOnGlass](#drawtextonglass)|Rysuje określony tekst w stylu wizualizacji określonego motywu.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Usuwa określoną parę tagów XML z określonego buforu.|
|[AFX_GLOBAL_DATA:: GetColor](#getcolor)|Pobiera bieżący kolor określonego elementu interfejsu użytkownika.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Zwraca wskaźnik do `ID2D1Factory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Pobiera wstępnie zdefiniowany kursor, który przypomina ręką i którego identyfikator jest `IDC_HAND`.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Tworzy i przechowuje w danych globalnych wskaźnik do interfejsu ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Tworzy i przechowuje w danych globalnych wskaźnik do interfejsu ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Pobiera metryki skojarzone z nieklienckim obszarem niezminimalizowanych okien.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Określa pozycje w obszarze Autoukrywanie pasków powłoki.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Pobiera Wysokość znaków tekstu w bieżącej czcionce.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Zwraca wskaźnik do `IWICImagingFactory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Zwraca wskaźnik do `IDWriteFactory` interfejsu, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicjuje `D2D`, `DirectWrite` i`WIC` fabryki. Wywołaj tę metodę przed zainicjowaniem okna głównego.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Wskazuje, czy są obsługiwane wstępnie zdefiniowane ikony 32-bitowe.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Określa, `D2D` czy został zainicjowany.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Zapewnia prosty sposób wywołania metody [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) systemu Windows.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Wskazuje, czy obrazy są aktualnie wyświetlane z dużym kontrastem.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Wykrywa bieżący stan animacji menu pulpitu i funkcji autoukrywanie paska zadań.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Rejestruje określoną klasę okna MFC.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Zwalnia interfejsy uzyskane za poorednictwem metod GetITaskbarList i GetITaskbarList3.|
|[AFX_GLOBAL_DATA:: Resume](#resume)|Ponownie inicjuje wewnętrzne wskaźniki funkcji, które mają dostęp do metod, które obsługują motywy systemu Windows [i style wizualne](/windows/win32/Controls/visual-styles-overview).|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Zapewnia prosty sposób wywołania metody [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) systemu Windows.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Tworzy określoną czcionkę logiczną.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Tworzy i inicjuje obiekt elementu powłoki na podstawie nazwy analizy.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes czcionki logiczne, które są używane przez strukturę.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicjuje kolory, głębię kolorów, pędzle, pióra i obrazy, które są używane przez platformę.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Włącza lub wyłącza obsługę usługi Microsoft Active Accessibility. Usługa Active Accessibility oferuje niezawodne metody udostępniania informacji o elementach interfejsu użytkownika.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Wskazuje, czy włączono obsługę usługi Microsoft Active Accessibility.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Wskazuje, czy system operacyjny obsługuje okna z warstwami.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Wskazuje, czy bieżący system operacyjny obsługuje mieszanie alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Wskazuje, czy aplikacja jest wykonywana w systemie operacyjnym Windows 7 lub nowszym|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Określa kolor gradientu aktywnego podpisu. Zwykle używany do dokowania okienek.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Określa kolor gradientu nieaktywnego aktywnego podpisu. Zwykle używany do dokowania okienek.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Wskazuje, czy struktura używa wstępnie zdefiniowanych ikon koloru 32-bitowego lub ikon o niższej rozdzielczości.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Wskazuje, czy czcionka systemowa jest używana dla menu, pasków narzędzi i wstążek.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Przechowuje uchwyt dla kursora dłoni.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Przechowuje uchwyt dla pionowego kursora rozciągnięcia.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Przechowuje uchwyt dla pionowego kursora rozciągnięcia.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Przechowuje uchwyt ikony narzędzia.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Określa przesunięcie od lewego paska narzędzi Autoukrywanie do lewej strony paska dokowania.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Określa przerwy między paskami narzędzi do autoukrywania.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Określa grubość ramki przeciągania, która jest używana do przekazywania stanu zadokowanego.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Określa grubość ramki przeciągania, która jest używana do przekazywania stanu zmiennoprzecinkowego.|

### <a name="remarks"></a>Uwagi

Większość danych w `AFX_GLOBAL_DATA` strukturze jest inicjowanych podczas uruchamiania aplikacji.

### <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxglobals. h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Wskazuje, czy system operacyjny obsługuje mieszanie alfa.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE wskazuje, że jest obsługiwana Blend alfa; w przeciwnym razie FALSE.

## <a name="cleanup"></a>AFX_GLOBAL_DATA:: CleanUp

Zwalnia zasoby, które są przydzielone przez platformę, takie jak pędzle, czcionki i biblioteki DLL.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D 2D1MakeRotateMatrix

Tworzy transformację rotacji, która obraca się o określony kąt wokół określonego punktu.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parametry

*kąty*<br/>
Kąt obrotu w prawo (w stopniach).

*Gniazdo*<br/>
Punkt, wokół którego ma zostać obrócony.

*matrix*<br/>
Gdy ta metoda zwraca, zawiera nową transformację obrotu. Należy przydzielić magazyn dla tego parametru.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli się powiedzie, lub wartość błędu w przeciwnym razie.

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::D rawParentBackground

Rysuje tło elementu nadrzędnego kontrolki w określonym obszarze.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do okna kontrolki.

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*lpRect*<br/>
podczas Wskaźnik do prostokąta, który jest powiązany z obszarem do rysowania. Wartość domyślna to NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::D rawTextOnGlass

Rysuje określony tekst w stylu wizualizacji określonego motywu.

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
podczas Dojście do danych motywu okna lub wartości NULL. Struktura używa określonego motywu do rysowania tekstu, jeśli ten parametr nie ma wartości NULL, a motywy są obsługiwane. W przeciwnym razie Struktura nie będzie używać motywu do rysowania tekstu.

Użyj metody [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) , aby utworzyć HTHEME.

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*iPartId*<br/>
podczas Część kontrolki, która ma żądany wygląd tekstu. Aby uzyskać więcej informacji, zobacz kolumnę części tabeli w [części i Stany](/windows/win32/controls/parts-and-states). Jeśli ta wartość jest równa 0, tekst jest rysowany czcionką domyślną lub czcionką wybraną w kontekście urządzenia.

*iStateId*<br/>
podczas Stan formantu, który ma żądany wygląd tekstu. Aby uzyskać więcej informacji, zobacz kolumny Stany tabeli w [części i Stany](/windows/win32/controls/parts-and-states).

*strText*<br/>
podczas Tekst do narysowania.

*cinania*<br/>
podczas Granica obszaru, w którym jest rysowany określony tekst.

*flagiDW*<br/>
podczas Kombinacja bitowa (lub) flag, która określa sposób rysowania określonego tekstu.

Jeśli parametr *hTheme* ma `NULL` wartość lub jeśli motywy nie są obsługiwane i włączone, parametr *nFormat* metody " [przechwytywania::D rawtext](../../mfc/reference/cdc-class.md#drawtext) " opisuje prawidłowe flagi. Jeśli są obsługiwane motywy, parametr *flagiDW* metody [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) opisuje prawidłowe flagi.

*nGlowSize*<br/>
podczas Rozmiar efektu blasku rysowanego w tle przed rysowaniem określonego tekstu. Wartość domyślna to 0.

*clrText*<br/>
podczas Kolor, w którym jest rysowany określony tekst. Wartością domyślną jest kolor domyślny.

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli motyw jest używany do rysowania określonego tekstu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Motyw definiuje styl wizualny aplikacji. Motyw nie jest używany do rysowania tekstu, jeśli parametr *hTheme* ma wartość null lub jeśli metoda [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) nie jest obsługiwana, lub jeśli kompozycja [Menedżer okien pulpitu](/windows/win32/dwm/dwm-overview) (DWM) jest wyłączona.

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport

Włącza lub wyłącza obsługę usługi Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE, aby włączyć obsługę ułatwień dostępu; Wartość FALSE, aby wyłączyć obsługę ułatwień dostępu. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Active Accessibility to technologia oparta na modelu COM, która usprawnia sposób współpracy programów i systemu operacyjnego Windows z produktami technologii pomocniczych. Zapewnia niezawodne metody ujawniania informacji o elementach interfejsu użytkownika. Dostępny jest jednak nowszy model dostępności o nazwie Automatyzacja interfejsu użytkownika firmy Microsoft. Porównanie dwóch technologii można znaleźć w temacie Automatyzacja [interfejsu użytkownika i Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Użyj metody [AFX_GLOBAL_DATA:: IsAccessibilitySupport](#isaccessibilitysupport) , aby określić, czy włączono obsługę usługi Microsoft Active Accessibility.

## <a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag

Usuwa określoną parę tagów XML z określonego buforu.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parametry

*strBuffer*<br/>
podczas Bufor tekstu.

*lpszTag*<br/>
podczas Nazwa pary otwierających i zamykających tagi XML.

*strTag*<br/>
określoną Gdy ta metoda zwraca, parametr *strTag* zawiera tekst między otwierającym i zamykającym tagiem XML, które są nazwane przez parametr *lpszTag* . Wszystkie spacje wiodące i końcowe są obcinane z wyniku.

*bIsCharsList*<br/>
podczas TRUE, aby przekonwertować symbole dla znaków ucieczki w parametrze *strTag* na rzeczywiste znaki ucieczki; Nie można wykonać konwersji. Wartość domyślna to FALSE. Aby uzyskać więcej informacji, zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Para tagów XML składa się z nazwanych tagów otwierających i zamykających, które wskazują początek i koniec przebiegu tekstu w określonym buforze. Parametr *strBuffer* określa bufor, a parametr *lpszTag* określa nazwę tagów XML.

Użyj symboli w poniższej tabeli, aby zakodować zestaw znaków ucieczki w określonym buforze. Określ wartość TRUE dla parametru *bIsCharsList* w celu przekonwertowania symboli w parametrze *strTag* na rzeczywiste znaki ucieczki. W poniższej tabeli za pomocą makra [_T ()](../../c-runtime-library/data-type-mappings.md) można określić symbol i ciągi znaków ucieczki.

|Symbol|Znak ucieczki|
|------------|----------------------|
|_T ("\\\t")|_T ("\t")|
|_T ("\\\n")|_T ("\n")|
|_T ("\\\r")|_T ("\r")|
|_T ("\\\b")|_T ("\b")|
|_T ("LT")|_T ("\<")|
|_T ("GT")|_T(">")|
|_T ("AMP")|_T ("&")|

## <a name="getcolor"></a>AFX_GLOBAL_DATA:: GetColor

Pobiera bieżący kolor określonego elementu interfejsu użytkownika.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parametry

*nColor*<br/>
podczas Wartość określająca element interfejsu użytkownika, którego kolor zostanie pobrany. Aby uzyskać listę prawidłowych wartości, zobacz parametr *nIndex* metody [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) .

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB określonego elementu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Jeśli parametr *nColor* jest poza zakresem, wartość zwracana wynosi zero. Ponieważ zero jest również prawidłową wartością RGB, nie można użyć tej metody do określenia, czy kolor systemu jest obsługiwany przez bieżący system operacyjny. Zamiast tego należy użyć metody [GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) , która zwraca wartość null, jeśli kolor nie jest obsługiwany.

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

Zwraca wskaźnik do interfejsu ID2D1Factory, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Factory, jeśli Tworzenie fabryki powiedzie się, lub wartość NULL, jeśli Tworzenie nie powiedzie się lub bieżący system operacyjny nie obsługuje D2D.

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

Pobiera wstępnie zdefiniowany kursor, który przypomina ręką i którego identyfikator jest IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora dłoni.

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics

Pobiera metryki skojarzone z nieklienckim obszarem niezminimalizowanych okien.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parametry

*informacje*<br/>
[in. out] Struktura [NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) , która zawiera skalowalne metryki skojarzone z nieklienckim obszarem niezminimalizowanego okna.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE.

## <a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

Pobiera Wysokość znaków tekstu w bieżącej czcionce.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
podczas Wartość TRUE, aby pobrać Wysokość znaków, gdy tekst jest uruchamiany w poziomie. Wartość FALSE, aby pobrać Wysokość znaków, gdy tekst jest uruchamiany w pionie. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Wysokość bieżącej czcionki mierzona od jej rosnącej do jej najgórę.

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

Zwraca wskaźnik do interfejsu IWICImagingFactory, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IWICImagingFactory, jeśli Tworzenie fabryki powiedzie się, lub wartość NULL, jeśli Tworzenie nie powiedzie się lub bieżący system operacyjny nie obsługuje WIC.

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

Zwraca wskaźnik do interfejsu IDWriteFactory, który jest przechowywany w danych globalnych. Jeśli interfejs nie zostanie zainicjowany, zostanie utworzony i ma domyślne parametry.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteFactory, jeśli Tworzenie fabryki powiedzie się, lub wartość NULL, jeśli Tworzenie nie powiedzie się lub bieżący system operacyjny nie obsługuje DirectWrite.

## <a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

Inicjuje fabryki D2D, DirectWrite i WIC. Wywołaj tę metodę przed zainicjowaniem okna głównego.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model wątkowości fabryki D2D i tworzonych przez nią zasobów.

*writeFactoryType*<br/>
Wartość określająca, czy obiekt fabryki zapisu będzie współużytkowany, czy izolowany

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli fabryki zostały intilalizrd, FAŁSZ — w przeciwnym razie

## <a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

Wskazuje, czy są obsługiwane wstępnie zdefiniowane ikony 32-bitowe.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli są obsługiwane wstępnie zdefiniowane ikony 32-bitowe; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość PRAWDA, jeśli struktura obsługuje 32-bitowe ikony wbudowane i jeśli system operacyjny obsługuje 16 bitów na piksel lub więcej, a obrazy nie są wyświetlane w dużym kontraście.

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport

Wskazuje, czy włączono obsługę usługi Microsoft Active Accessibility.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli włączono obsługę dostępności; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Usługa Microsoft Active Accessibility była wcześniejszym rozwiązaniem do udostępniania aplikacji. Automatyzacja interfejsu użytkownika firmy Microsoft to nowy model dostępności dla systemu Microsoft Windows i jest przeznaczony do zaspokajania potrzeb produktów technologii pomocniczych i zautomatyzowanych narzędzi do testowania.

Użyj metody [AFX_GLOBAL_DATA:: EnableAccessibilitySupport](#enableaccessibilitysupport) , aby włączyć lub wyłączyć obsługę Active Accessibility.

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized

Określa, czy D2D został zainicjowany

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli D2D został zainicjowany; w przeciwnym razie FALSE.

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Zapewnia prosty sposób wywołania metody [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) systemu Windows.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli kompozycja [Menedżer okien pulpitu](/windows/win32/dwm/dwm-overview) (DWM) jest włączona; w przeciwnym razie FALSE.

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Wskazuje, czy obrazy są aktualnie wyświetlane z dużym kontrastem.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli obrazy są aktualnie wyświetlane w trybie czarno-białym o dużym kontraście; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W trybie czarno-kontrastowym krawędzie są białe, a tło jest czarne. W trybie o małym kontraście krawędzie są czarne, a tło jest białe.

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Wskazuje, czy system operacyjny obsługuje okna z warstwami.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli są obsługiwane okna z warstwami. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli okna z warstwami są obsługiwane, *inteligentne znaczniki dokowania* używają warstwowych okien.

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Wskazuje, czy struktura używa wstępnie zdefiniowanych ikon koloru 32-bitowego lub ikon o niższej rozdzielczości.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Uwagi

TRUE określa, że struktura używa ikon koloru 32-bitowych; FALSE określa ikony mniejszych rozdzielczości. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski jako wartość true.

Ten element członkowski musi być ustawiony podczas uruchamiania aplikacji.

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

Wskazuje, czy czcionka systemowa jest używana dla menu, pasków narzędzi i wstążek.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE oznacza użycie czcionki systemowej. w przeciwnym razie FALSE. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski na wartość false.

Testowanie tego elementu członkowskiego nie jest jedynym sposobem określenia czcionki do użycia. `AFX_GLOBAL_DATA::UpdateFonts` Metoda sprawdza także domyślne i alternatywne czcionki, aby określić, które style wizualne są dostępne do zastosowania do menu, pasków narzędzi i wstążek.

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

Przechowuje uchwyt dla kursora dłoni.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

Przechowuje uchwyt dla pionowego kursora rozciągnięcia.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

Przechowuje uchwyt dla pionowego kursora rozciągnięcia.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

Przechowuje uchwyt ikony narzędzia.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Określa przesunięcie od lewego paska narzędzi Autoukrywanie do lewej strony paska dokowania.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Uwagi

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 4 pikseli.

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Określa przerwy między paskami narzędzi do autoukrywania.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Uwagi

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 14 pikseli.

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Określa grubość ramki przeciągania, która jest używana do wskazania stanu zadokowanego.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Uwagi

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 3 pikseli.

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Określa grubość ramki przeciągania, która jest używana do wskazania stanu zmiennoprzecinkowego.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Uwagi

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 4 pikseli.

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange

Wykrywa bieżący stan animacji menu pulpitu i funkcji autoukrywanie paska zadań.

```
void OnSettingChange();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia zmienne struktury na stan niektórych atrybutów pulpitu użytkownika. Ta metoda wykrywa bieżący stan animacji menu, zanikania menu i ukrywania paska zadań.

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass

Rejestruje określoną klasę okna MFC.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parametry

*lpszClassNamePrefix*<br/>
podczas Nazwa klasy okna do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

Kwalifikowana nazwa zarejestrowanej klasy, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie [wyjątek zasobu](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Uwagi

Wartość zwracana jest rozdzielaną średnikami listą ciągu parametrów *lpszClassNamePrefix* i szesnastkową reprezentacją uchwytów bieżącego wystąpienia aplikacji; kursor aplikacji, który jest kursorem strzałki, którego identyfikator jest IDC_ARROW; i Pędzel tła. Aby uzyskać więcej informacji na temat rejestrowania klas okna MFC, zobacz [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="resume"></a>AFX_GLOBAL_DATA:: Resume

Ponownie inicjuje wewnętrzne wskaźniki funkcji, które mają dostęp do metod, które obsługują motywy systemu Windows i style wizualne.

```
BOOL Resume();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE. W trybie debugowania ta metoda potwierdza, czy ta metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy struktura otrzymuje komunikat [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) .

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib

Zapewnia prosty sposób wywołania metody [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) systemu Windows.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do okna warstwowego.

*crKey*<br/>
podczas Klucz koloru przezroczystości, którego [Menedżer okien pulpitu](/windows/win32/dwm/dwm-overview) używa do redagowania okna warstwowego.

*bAlpha*<br/>
podczas Wartość alfa, która jest używana do opisywania nieprzezroczystości okna warstwowego.

*flagiDW*<br/>
podczas Kombinacja bitowa (lub) flag, które określają parametry metody do użycia. Określ LWA_COLORKEY, aby użyć parametru *crKey* jako koloru przezroczystości. Określ LWA_ALPHA, aby użyć parametru *bAlpha* w celu określenia nieprzejrzystości okna warstwowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE.

## <a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont

Tworzy określoną czcionkę logiczną.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
podczas Wskaźnik do struktury zawierającej atrybuty czcionki.

*bHorz*<br/>
podczas PRAWDA, aby określić, że tekst jest uruchamiany w poziomie. Wartość FALSE, aby określić, że tekst jest uruchamiany pionowo.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE. W trybie debugowania ta metoda potwierdza, czy ta metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda służy do tworzenia standardowej czcionki w poziomie, czcionki podkreślonej i czcionki pogrubionej, która jest używana w domyślnych elementach menu. Ta metoda opcjonalnie tworzy zwykłą czcionkę pionową. Aby uzyskać więcej informacji na temat czcionek logicznych, zobacz [CFont:: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts

Reintializes czcionki logiczne, które są używane przez strukturę.

```
void UpdateFonts();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat czcionek logicznych `CFont::CreateFontIndirect`, zobacz.

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors

Inicjuje kolory, głębię kolorów, pędzle, pióra i obrazy, które są używane przez platformę.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

Wskazuje, czy aplikacja jest wykonywana w systemie Windows 7 lub nowszym.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient

Określa kolor gradientu aktywnego podpisu. Zwykle używany do dokowania okienek.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Określa kolor gradientu nieaktywnego podpisu. Zwykle używany do dokowania okienek.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList

Tworzy i przechowuje w danych globalnych wskaźnik do `ITaskBarList` interfejsu.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, `ITaskbarList` Jeśli Tworzenie obiektu listy paska zadań powiedzie się; Wartość NULL, jeśli Tworzenie nie powiedzie się lub jeśli bieżący system operacyjny jest mniejszy niż Windows 7.

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3

Tworzy i przechowuje w danych globalnych wskaźnik do `ITaskBarList3` interfejsu.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, `ITaskbarList3` Jeśli Tworzenie obiektu listy paska zadań powiedzie się; Wartość NULL, jeśli Tworzenie nie powiedzie się lub jeśli bieżący system operacyjny jest mniejszy niż Windows 7.

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars

Określa pozycje w obszarze Autoukrywanie pasków powłoki.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita z zakodowanymi flagami, które określają położenia pasków z autoukrywaniem. Może łączyć następujące wartości: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Zwalnia interfejsy uzyskane za pomocą `GetITaskbarList` metod `GetITaskbarList3` i.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Tworzy i inicjuje obiekt elementu powłoki na podstawie nazwy analizy.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
podczas Wskaźnik do nazwy wyświetlanej.

*pbc*<br/>
Wskaźnik do kontekstu powiązania, który kontroluje operację analizowania.

*riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppv*<br/>
określoną Gdy ta funkcja zwraca, zawiera wskaźnik interfejsu żądany w *riid*. Zwykle jest `IShellItem` to lub `IShellItem2`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli pomyślne; w przeciwnym razie wartość błędu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Części i Stany](/windows/win32/controls/parts-and-states)<br/>
[Przechwytywanie zmian::D rawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Menedżer okien pulpitu](/windows/win32/dwm/dwm-overview)<br/>
[Włącz i kontroluj kompozycję menedżera DWM](/windows/win32/dwm/composition-ovw)<br/>
[Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor Function](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS, struktura](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
