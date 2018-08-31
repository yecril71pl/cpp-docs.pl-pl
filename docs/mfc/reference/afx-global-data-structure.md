---
title: Afx_global_data — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d762aef0dd48f3eac8eaeeddee558c4f237b29f
ms.sourcegitcommit: 220fd4fda829f810e15fc1a1d98ab43c46201b47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43352742"
---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA — Struktura
`AFX_GLOBAL_DATA` Struktura zawiera pola i metody, które są używane do zarządzania w ramach lub dostosować wygląd i działanie aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct AFX_GLOBAL_DATA  
```  

## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Konstruuje `AFX_GLOBAL_DATA` struktury.|  
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Zwalnia zasoby, które są przydzielane przez platformę, takie jak pędzle, czcionki i bibliotek DLL.|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Tworzy transformacji obrotu, która obraca się o określony kąt wokół punktu określonego.|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Rysuje tło elementu nadrzędnego formantu w podanym obszarze.|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Rysuje określony tekst w stylu wizualnego określony motyw.|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Usuwa określoną parę znaczników XML z określonego bufora.|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Pobiera bieżący kolor elementu interfejsu użytkownika.|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Zwraca wskaźnik do `ID2D1Factory` interfejsu, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Pobiera kursor wstępnie zdefiniowanych, podobny dłoni i których identyfikator jest `IDC_HAND`.|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Tworzy i przechowuje danych globalnych wskaźnik do interfejsu ITaskBarList.|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Tworzy i przechowuje danych globalnych wskaźnik do interfejsu ITaskBarList3.|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Pobiera metryki skojarzone z nieklienckim obszarze nonminimized systemu windows.|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Określa, że pozycji powłoki automatyczne ukrywanie pasków.|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Pobiera wysokość znaki tekstowe w bieżącej czcionki.|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Zwraca wskaźnik do `IWICImagingFactory` interfejsu, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Zwraca wskaźnik do `IDWriteFactory` interfejsu, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicjuje `D2D`, `DirectWrite`, i `WIC` fabryk. Wywołaj tę metodę, zanim okno główne jest zainicjowany.|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowe są obsługiwane.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Określa, czy `D2D` został zainicjowany.|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Zapewnia prostą metodę do wywołania Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) metody.|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Wskazuje, czy obrazy są obecnie wyświetlane o wysokim kontraście.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Wykrywa bieżący stan animacji menu i funkcji automatycznie ukrywaj paska zadań pulpitu.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Rejestruje określoną klasę MFC w oknie.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Zwalnia interfejsy uzyskane za pośrednictwem metody GetITaskbarList i GetITaskbarList3.|  
|[AFX_GLOBAL_DATA::Resume](#resume)|Ponownie inicjuje wskaźniki funkcji wewnętrznej, uzyskujących dostęp do metody, które obsługują Windows [kompozycje i style wizualne](/windows/desktop/Controls/visual-styles-overview).|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Zapewnia prostą metodę do wywołania Windows [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540) metody.|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Tworzy logiczną czcionki.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Tworzy i inicjuje obiekt elementu powłoki, na podstawie nazwy podczas analizowania.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes logiczne czcionek, które są używane przez platformę.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicjuje kolorów, głębi kolorów, pędzle, pióra i obrazów, które są używane przez platformę.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Włącza lub wyłącza obsługę Microsoft Active Accessibility. Active Accessibility zapewnia niezawodne metody ujawnienia informacji na temat elementów interfejsu użytkownika.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Wskazuje, czy jest włączona obsługa Microsoft Active Accessibility.|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Wskazuje, czy system operacyjny obsługuje warstwowej systemu windows.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Wskazuje, czy bieżący system operacyjny obsługuje przenikaniem alfa.|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Wskazuje, czy aplikacja jest wykonywana w ramach systemu operacyjnego programu Windows 7 lub nowszy|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Określa kolor gradientu podpis aktywny. Zazwyczaj jest używane dla okienka dokowania.|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Określa kolor gradientu nieaktywnym nagłówku active. Zazwyczaj jest używane dla okienka dokowania.|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Wskazuje, czy środowisko wykorzystuje ikony wstępnie zdefiniowany kolor 32-bitowych lub ikony niższej rozdzielczości.|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Wskazuje, czy czcionka jest używany do menu, paski narzędzi i Wstążki.|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Przechowuje dojście do kursora ręcznie.|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Przechowuje dojście poziomy stretch kursora.|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Przechowuje dojście pionowy stretch kursora.|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Przechowuje dojście ikony narzędzia.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Określa przesunięcie z paska narzędzi skrajnie po lewej stronie automatycznie ukrywaj po lewej stronie pasek dokowania.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Określa luki między autoukrywania pasków narzędzi.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Określa grubość ramki przeciągania, w której jest używany do komunikacji z zadokowanych stanu.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Określa grubość ramki przeciągania, który jest używany do komunikacji stanu zmiennoprzecinkowego.|  
  
### <a name="remarks"></a>Uwagi  
 Większość danych w `AFX_GLOBAL_DATA` struktury jest inicjowany podczas uruchamiania aplikacji.  
  
### <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxglobals.h  
  
### <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Wskazuje, czy system operacyjny obsługuje przenikaniem alfa.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość TRUE wskazuje, że przenikaniem alfa jest obsługiwana; w przeciwnym razie wartość FALSE.  
  

## <a name="cleanup"></a> AFX_GLOBAL_DATA::CleanUp
Zwalnia zasoby, które są przydzielane przez platformę, takie jak pędzle, czcionki i bibliotek DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Tworzy transformacji obrotu, która obraca się o określony kąt wokół punktu określonego.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Parametry   
 *kąt*  
 Kąt obrotu w prawo w stopniach.  
  
 *Centrum*  
 Punkt o tym, które wymiany.  
  
 *Macierz*  
 Po powrocie z tej metody zawiera nowe przekształcenie obrotu. Należy przydzielić pamięci masowej dla tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przeciwnym razie zwraca wartość S_OK w przypadku powodzenia lub wartość błędu.  
  
## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground
Rysuje tło elementu nadrzędnego formantu w podanym obszarze.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *pWnd*  
 Wskaźnik do kontrolki okna.  
  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *lprect —*  
 Wskaźnik do granic obszaru, aby narysować prostokąt. Wartością domyślną jest NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass
Rysuje określony tekst w stylu wizualnego określony motyw.  
  
  
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
 [in] *hTheme*  
 Dojście do danych motyw okna, lub wartość NULL. Środowisko wykorzystuje określony motyw ma zostać narysowany tekst, jeśli ten parametr nie ma wartości NULL i motywów są obsługiwane. W przeciwnym razie ramach nie używa motyw ma zostać narysowany tekst.  
  
 Użyj [OpenThemeData](/windows/desktop/api/uxtheme/nf-uxtheme-openthemedata) metodę w celu utworzenia HTHEME.  
  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *iPartId*  
 Część kontroli, która ma wygląd odpowiedni tekst. Aby uzyskać więcej informacji, zobacz części kolumny tabeli w [części i Stany](https://msdn.microsoft.com/library/windows/desktop/bb773210). Jeśli ta wartość wynosi 0, tekstu jest rysowana w domyślnej czcionki lub czcionki, zaznaczone w kontekście urządzenia.  
  
 [in] *iStateId*  
 Stan kontrolki, która ma wygląd odpowiedni tekst. Aby uzyskać więcej informacji, zobacz kolumnę stany w tabeli w [części i Stany](https://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
 [in] *strText*  
 Tekst do rysowania.  
  
 [in] *rect*  
 Granica obszaru, w którym jest rysowana określony tekst.  
  
 [in] *Flagidw*  
 Bitowa kombinacja (lub) flagi określające, jak jest rysowana określony tekst.  
  
 Jeśli *hTheme* parametr jest `NULL` czy motywy nie są obsługiwane i włączony, *nFormat* parametru [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metoda opisuje prawidłowe flagi. Jeśli są obsługiwane motywy, *Flagidw* parametru [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) metoda opisuje prawidłowe flagi.  
  
 [in] *nGlowSize*  
 Rozmiar wpływ poświata, jaki jest rysowana na tle przed narysowaniem określony tekst. Wartość domyślna to 0.  
  
 [in] *clrText*  
 Kolor, w którym jest rysowana określony tekst. Wartość domyślna to domyślny kolor.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motywu jest używany do rysowania określonego tekstu. w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Motyw definiuje stylu wizualnego w aplikacji. Motyw nie jest używany do rysowania tekstu, jeśli *hTheme* parametr ma wartość NULL, lub jeśli [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) metoda nie jest obsługiwana, lub jeśli [Menedżera okien pulpitu](/windows/desktop/dwm/dwm-overview) składu (DWM) jest wyłączona.  
  
### <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [Części i Stany](https://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex)   
 [Menedżer okien pulpitu](/windows/desktop/dwm/dwm-overview)   
 [Włącz i kontroluj skład Menedżera okien pulpitu](/windows/desktop/dwm/composition-ovw)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport
Włącza lub wyłącza obsługę Microsoft Active Accessibility.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *bWłączenie*  
 Wartość TRUE, aby włączyć obsługę ułatwień dostępu; Wartość FALSE, aby wyłączyć funkcję ułatwień dostępu pomocy technicznej. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Active Accessibility jest technologii opartych na modelu COM, zwiększający programy sposób i pracy systemu operacyjnego Windows wraz z produktów technologii pomocniczej. Zapewnia niezawodne metody do ujawnienia informacji na temat elementów interfejsu użytkownika. Jednakże nowy model dostępności o nazwie automatyzacji interfejsu użytkownika firmy Microsoft jest teraz dostępna. Dla porównania dwóch technologii, zobacz [automatyzacji interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Użyj [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) metodę pozwala ustalić, czy jest włączona obsługa Microsoft Active Accessibility.  
  
 
### <a name="see-also"></a>Zobacz też  
 [Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag
Usuwa określoną parę znaczników XML z określonego bufora.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *strBuffer*  
 Bufor tekstowy.  
  
 [in] *lpszTag*  
 Nazwa pary otwierające i zamykające znaczniki XML.  
  
 [out] *strTag*  
 Po powrocie z tej metody *strTag* parametr zawiera tekst, który jest między otwierającym i zamykającym XML tagi, które są reprezentowane przez *lpszTag* parametru. Żadnych spacji wiodących i końcowych jest usuwane z wynikiem.  
  
 [in] *bIsCharsList*  
 Wartość PRAWDA, aby przekonwertować symboli dla znaków ucieczki w *strTag* parametru na znaki ucieczki rzeczywiste; Wartość FALSE nie w celu wykonania konwersji. Wartość domyślna to FALSE. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Pary znaczników XML składa się z o nazwie otwierające i zamykające znaczniki, które wskazują początek i koniec okresu przebiegu tekstu w buforze określony. *StrBuffer* parametr określa buforu, a *lpszTag* parametr określa nazwę tagów XML.  
  
 Kodowanie zestawu znaków ucieczki w buforze określony za pomocą tych symboli w poniższej tabeli. Określ wartość PRAWDA dla *bIsCharsList* parametr można przekonwertować symboli w *strTag* parametru na znaki ucieczki rzeczywistych. W poniższej tabeli używa [_T()](../../c-runtime-library/data-type-mappings.md) makra, aby określić symbol i ciągi znaków ucieczki.  
  
|Symbol|Znak ucieczki|  
|------------|----------------------|  
|_T ("\\\t")|_T("\t")|  
|_T ("\\\n")|_T("\n")|  
|_T ("\\\r")|_T("\r")|  
|_T ("\\\b")|_T("\b")|  
|_T("LT")|_T ("\<")|  
|_T("GT")|_T("&GT;")|  
|_T("AMP")|_T("&AMP;")|  
  
## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor
Pobiera bieżący kolor elementu interfejsu użytkownika.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *nColor*  
 Wartość, która określa element interfejsu użytkownika, którego kolor są pobierane. Aby uzyskać listę prawidłowych wartości, zobacz *nIndex* parametru [GetSysColor](https://msdn.microsoft.com/library/windows/desktop/ms724371) metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość koloru RGB element interfejsu użytkownika. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *nColor* parametr znajduje się poza zakresem, wartość zwracana wynosi zero. Ponieważ zero jest również prawidłowej wartości RGB, nie można użyć tej metody, aby ustalić, czy kolor, który system jest obsługiwana przez bieżący system operacyjny. Zamiast tego należy użyć [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush) metody, która zwraca wartość NULL, jeśli kolor nie jest obsługiwana.  
  
### <a name="see-also"></a>Zobacz też  

 [GetSysColor — funkcja](https://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory
 Zwraca wskaźnik do interfejsu ID2D1Factory, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Factory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie ma obsługi D2D.  
  
## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor
Pobiera wstępnie zdefiniowanych kursor, który przypomina dłoni i których identyfikator jest IDC_HAND.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt kursora ręcznie.  

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics
Pobiera metryki skojarzone z nieklienckim obszarze nonminimized systemu windows.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parametry   
 [out w] *informacji*  
 A [NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175) strukturę, która zawiera metryki skalowalne, skojarzone z nieklienckim obszarze okna nonminimized.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE.  
 
  
### <a name="see-also"></a>Zobacz też   
 [Struktura NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight
 Pobiera wysokość znaki tekstowe w bieżącej czcionki.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *bHorz*  
 Wartość TRUE, aby pobrać wysokość znaków, gdy tekst działa jedynie w pionie. Wartość FALSE, aby pobrać wysokość znaków, gdy tekst jest uruchamiany w pionie. Wartość domyślna to TRUE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość bieżącej czcionki jest mierzony od jego Wydłużenie górne do jej w dół.  
  
## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory
Zwraca wskaźnik do interfejsu IWICImagingFactory, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IWICImagingFactory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie ma WIC pomocy technicznej.  
  
## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory
Zwraca wskaźnik do interfejsu IDWriteFactory, która jest przechowywana w danych globalnych. Jeśli interfejs nie został zainicjowany, zostanie utworzony i ma następujące parametry domyślne.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteFactory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie ma obsługi DirectWrite.  
 
## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D
Inicjuje D2D DirectWrite i WIC fabryk. Wywołaj tę metodę, zanim okno główne jest zainicjowany.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parametry   
 *d2dFactoryType*  
 Model wątkowości fabryki D2D i zasoby, które tworzy.  
  
 *writeFactoryType*  
 Wartość, która określa, czy obiekt fabryki zapisu zostaną udostępnione lub izolowany  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli fabryk były intilalizrd, wartość FALSE — w przeciwnym razie  
  
## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons
Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowe są obsługiwane.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli wstępnie zdefiniowane ikony 32-bitowe są obsługiwane; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość TRUE, jeśli platforma obsługuje wbudowanej ikony 32-bitowych i jeśli system operacyjny obsługuje 16 bitów na piksel lub więcej, a obrazy nie są wyświetlane o wysokim kontraście.  
  
## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport
Wskazuje, czy jest włączona obsługa Microsoft Active Accessibility.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli jest włączona Obsługa dostępności; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Active Accessibility była wcześniej umożliwiająca ułatwianie dostępu do aplikacji. Microsoft UI Automation — jest to nowy model ułatwień dostępu dla Microsoft Windows ma spełniać potrzeby produktów technologii pomocniczej i automatyczne narzędzia do testowania.   
  
 Użyj [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) metodę, aby włączyć lub wyłączyć obsługę Active Accessibility.  
  

### <a name="see-also"></a>Zobacz też  
 [Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized
 Określa, czy D2D został zainicjowany.  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli został zainicjowany D2D; w przeciwnym razie wartość FALSE.  
  
## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Zapewnia prostą metodę do wywołania Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) metody.  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli [Menedżera okien pulpitu](/windows/desktop/dwm/dwm-overview) składu (DWM) jest włączone; w przeciwnym razie wartość FALSE.  
  
### <a name="see-also"></a>Zobacz też    
 [Menedżer okien pulpitu](/windows/desktop/dwm/dwm-overview)   
 [Włącz i kontroluj skład Menedżera okien pulpitu](/windows/desktop/dwm/composition-ovw)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode
 Wskazuje, czy obrazy są obecnie wyświetlane o wysokim kontraście.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli obrazy są obecnie wyświetlane w trybie dużego kontrastu czarne lub białe; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 W trybie czarne dużego kontrastu krawędzie skierowane światła są białe i tło jest czarny. W trybie białe dużego kontrastu krawędzie skierowane światła są czarne i tło jest białe.  
  
## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Wskazuje, czy system operacyjny obsługuje warstwowej systemu windows.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli warstwowej systemu windows są obsługiwane; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli warstwowej systemu windows są obsługiwane, *inteligentnego dokowania* znaczniki używanie okien warstwowej.  
  
## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Wskazuje, czy środowisko wykorzystuje ikony wstępnie zdefiniowany kolor 32-bitowych lub ikony niższej rozdzielczości.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość TRUE Określa, że struktura używa ikon koloru 32-bitowy; FALSE określa ikony niższych rozdzielczości. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby wartość TRUE.  
  
 Ten element członkowski, należy ustawić podczas uruchamiania aplikacji.  
  
## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont
Wskazuje, czy czcionka jest używany do menu, paski narzędzi i Wstążki.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Uwagi  
 Określa wartość TRUE, użyj czcionki systemowej; w przeciwnym razie wartość FALSE. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby wartość FALSE.  
  
 Testowanie tego elementu członkowskiego nie jest jedynym sposobem na platformę, aby określić czcionki do użycia. `AFX_GLOBAL_DATA::UpdateFonts` Metoda sprawdza również domyślne i alternatywne czcionki, aby ustalić, jakie stylów wizualnych dostępnych mają być stosowane do menu, paski narzędzi i Wstążki.  
  
## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand
Przechowuje dojście do kursora ręcznie.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch
Przechowuje dojście poziomy stretch kursora.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert
Przechowuje dojście pionowy stretch kursora.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool
Przechowuje dojście ikony narzędzia.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Określa przesunięcie z skrajnie po lewej stronie automatycznie ukrywaj paska narzędzi po lewej stronie na pasku dokowania.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby 4 pikseli.  
  
## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Określa luki między autoukrywania pasków narzędzi.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby 14 pikseli.  
  
## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Określa grubość ramkę przeciągania, która służy do wskazywania stanu zadokowany.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby 3 pikseli.  
  
## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Określa grubość ramki przeciągania, który służy do wskazywania stanu zmiennoprzecinkowego.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje tą składową, aby 4 pikseli.  
  
## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange
Wykrywa bieżący stan animacji menu i funkcji automatycznie ukrywaj paska zadań pulpitu.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia zmienne framework stan niektórych atrybutów z komputera użytkownika. Ta metoda wykrywa bieżący stan menu animacji, menu fade i pasku funkcji autoukrywania zadań.  
  
## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass
Rejestruje określoną klasę MFC w oknie.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *lpszClassNamePrefix*  
 Nazwa klasy okna do zarejestrowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kwalifikowana nazwa klasy zarejestrowane, jeśli ta metoda zakończy się powodzeniem; w przeciwnym razie [wyjątek zasobu](https://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest listę rozdzielonych średnikami *lpszClassNamePrefix* ciąg parametru i reprezentacje szesnastkowym uchwytów bieżącego wystąpienia aplikacji; kursora aplikacji, czyli strzałkę kursor, którego identyfikator jest IDC_ARROW; i Pędzel tła. Aby uzyskać więcej informacji na temat rejestrowanie klas okien MFC, zobacz [afxregisterclass —](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Zobacz też    
 [Afxregisterclass —](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [Afxthrowresourceexception —](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume
 Ponownie inicjuje wskaźniki funkcji wewnętrznej, uzyskujących dostęp do metody, które obsługują Windows kompozycje i style wizualne. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE. W trybie debugowania ta metoda potwierdza, jeśli ta metoda zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy otrzyma w ramach [WM_POWERBROADCAST](/windows/desktop/Power/wm-powerbroadcast) wiadomości.  
  
## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib
Zapewnia prostą metodę do wywołania Windows [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540) metody.  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *hwnd*  
 Dojście do okna warstwowej.  
  
 [in] *crKey*  
 Przezroczysty kolor klucza [Menedżera okien pulpitu](/windows/desktop/dwm/dwm-overview) używa do tworzenia warstwowych okna.  
  
 [in] *bAlpha*  
 Wartość alfa używany do opisania nieprzezroczystość warstwowej okna.  
  
 [in] *Flagidw*  
 Bitowa kombinacja (lub) flagi określające, które parametry metody do użycia. Określ LWA_COLORKEY używać *crKey* parametru jako przezroczysty kolor. Określ LWA_ALPHA używać *bAlpha* parametru do określenia nieprzezroczystość warstwowej okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE.   
 
### <a name="see-also"></a>Zobacz też   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont
Tworzy logiczną czcionki.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *lpLogFont*  
 Wskaźnik do struktury, która zawiera atrybuty czcionki.  
  
 [in] *bHorz*  
 Wartość TRUE, aby określić, czy tekst ma być ułożony; Wartość FALSE, aby określić, że tekst jest uruchamiany w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE. W trybie debugowania ta metoda potwierdza, jeśli ta metoda zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy poziomy czcionki regularne podkreśleniem i pogrubioną czcionką, który jest używany w domyślnych elementów menu. Ta metoda tworzy opcjonalnie regularne czcionki pionowej. Aby uzyskać więcej informacji na temat logiczne czcionek, zobacz [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts
Reintializes logiczne czcionek, które są używane przez platformę.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat logiczne czcionek, zobacz `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors
Inicjuje kolorów, głębi kolorów, pędzle, pióra i obrazów, które są używane przez platformę.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7
Wskazuje, czy aplikacja jest wykonywana w obszarze Windows 7 lub nowszej.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient
Określa kolor gradientu aktywny podpis. Zazwyczaj jest używane dla okienka dokowania.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Określa kolor gradientu nieaktywnym nagłówku. Zazwyczaj jest używane dla okienka dokowania.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList
Tworzy i przechowuje danych globalnych wskaźnik do `ITaskBarList` interfejsu.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `ITaskbarList` interfejsu, jeśli zadanie paska obiekt listy zakończy się pomyślnie; Wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny jest mniejsza niż Windows 7.  
  
## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3
Tworzy i przechowuje danych globalnych wskaźnik do `ITaskBarList3` interfejsu.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `ITaskbarList3` interfejsu, jeśli zadanie paska obiekt listy zakończy się pomyślnie; Wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny jest mniejsza niż Windows 7.  
  
## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars
Określa, że pozycji powłoki automatyczne ukrywanie pasków.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość całkowitą z użyciem flag zakodowany, które określają położenie automatyczne ukrywanie pasków. Może on połączyć następujące wartości: AFX_AUTOHIDE_BOTTOM AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Zwalnia interfejsy uzyskane za pośrednictwem `GetITaskbarList` i `GetITaskbarList3` metody.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Tworzy i inicjuje obiekt elementu powłoki, na podstawie nazwy podczas analizowania.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Parametry   
 *pszPath*  
 [in] Wskaźnik do nazwy wyświetlanej.  
  
 *pbc*  
 Wskaźnik do kontekstu powiązania, który kontroluje operacji analizowania.  
  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu.  
  
 *ppv*  
 [out] Po powrocie z tej funkcji zawiera wskaźnik interfejsu w *riid*. Są to zazwyczaj `IShellItem` lub `IShellItem2`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia; w przeciwnym razie wartość błędu.  

