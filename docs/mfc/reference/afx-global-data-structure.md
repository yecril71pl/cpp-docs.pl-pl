---
title: "Afx_global_data — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_GLOBAL_DATA
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68b4a5ba27d4fcb6fcaac7c80662d778c7cbbca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Zwalnia zasoby, które są przydzielane przez platformę, na przykład pędzle, czcionki i bibliotek DLL.|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Tworzy transformację obracanie, którego obraca się o określony kąt wokół punktu określonego.|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Rysuje tła formantu nadrzędnego w określonym obszarze.|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Rysuje określony tekst w stylu określony motyw.|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Usuwa określoną parę tagu XML z określonego bufora.|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Pobiera bieżący kolor elementu interfejsu użytkownika.|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Zwraca wskaźnik do `ID2D1Factory` interfejs, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Pobiera kursor wstępnie zdefiniowanych podobny dłoni i których identyfikator jest `IDC_HAND`.|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Tworzy i przechowuje danych globalnych wskaźnik do interfejsu ITaskBarList.|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Tworzy i przechowuje danych globalnych wskaźnik do interfejsu ITaskBarList3.|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Pobiera metryki skojarzone z obszar niekliencki nonminimized systemu Windows.|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Określa pozycje automatycznie powłoki ukryć paski.|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Pobiera wysokość znaki tekstu w bieżącej czcionki.|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Zwraca wskaźnik do `IWICImagingFactory` interfejs, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Zwraca wskaźnik do `IDWriteFactory` interfejs, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicjuje `D2D`, `DirectWrite`, i `WIC` fabryki. Tę metodę należy wywołać przed zainicjowaniem głównego okna.|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowych są obsługiwane.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Określa, czy `D2D` został zainicjowany.|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Zapewnia prostą metodę do wywołania systemu Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) metody.|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Wskazuje, czy obrazy są aktualnie wyświetlane dużego kontrastu.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Wykrywa bieżący stan animacji menu i paska zadań autohide — funkcje pulpitu.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Rejestruje klasę okna określony MFC.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Wydanie interfejsy uzyskanymi za pośrednictwem metody GetITaskbarList i GetITaskbarList3.|  
|[AFX_GLOBAL_DATA::Resume](#resume)|Ponownie inicjuje wskaźników funkcji wewnętrznej, które uzyskują dostęp do metod, które obsługują system Windows [kompozycje i style wizualne](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx).|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Zapewnia prostą metodę do wywołania systemu Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) metody.|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Tworzy logiczną czcionki.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Tworzy i inicjuje obiekt elementu powłoki, na podstawie nazwy podczas analizowania.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes czcionki logiczne, które są używane przez platformę.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicjuje kolorów, głębi kolorów, pędzle, pióra i obrazów, które są używane przez platformę.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Włącza lub wyłącza obsługę modułu Active Accessibility firmy Microsoft. Active Accessibility zapewnia niezawodne metody udostępnianie informacji na temat elementów interfejsu użytkownika.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Wskazuje, czy jest włączona obsługa Microsoft Active Accessibility.|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Wskazuje, czy system operacyjny obsługuje warstwowego systemu windows.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Wskazuje, czy bieżący system operacyjny obsługuje przenikanie alfa.|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Wskazuje, czy aplikacja jest wykonywana w ramach systemu operacyjnego Windows 7 lub nowszy|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Określa kolor gradientu active podpisu. Zazwyczaj używane w przypadku Dokowanie okienka.|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Określa kolor gradientu nieaktywnym nagłówku aktywne. Zazwyczaj używane w przypadku Dokowanie okienka.|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Wskazuje, czy platformę używa ikon koloru 32-bitowych wstępnie zdefiniowanych lub ikony niższej rozdzielczości.|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Wskazuje, czy czcionki systemowej jest używany do menu i pasków narzędzi oraz taśmy.|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Przechowuje dojście do kursora ręcznie.|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Przechowuje dojście do poziomych stretch kursora.|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Przechowuje dojście do pionowego stretch kursora.|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Przechowuje dojście ikony narzędzia.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Określa przesunięcie z lewej strony autohide — paska narzędzi po lewej stronie dokowania paska.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Określa odstęp między autohide — pasków narzędzi.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Określa grubość ramki przeciągania, w której jest używany do komunikacji zadokowanych stanu.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Określa grubość ramki przeciągania, w której jest używany do komunikacji przestawne stanu.|  
  
### <a name="remarks"></a>Uwagi  
 Większość danych w `AFX_GLOBAL_DATA` struktury jest inicjowana po uruchomieniu aplikacji.  
  
### <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxglobals.h  
  
### <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Wskazuje, czy system operacyjny obsługuje przenikanie alfa.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Wskazuje, że przenikanie alfa jest obsługiwany; w przeciwnym razie `FALSE`.  
  

## <a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp
Zwalnia zasoby, które są przydzielane przez platformę, na przykład pędzle, czcionki i bibliotek DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Tworzy transformację obracanie, którego obraca się o określony kąt wokół punktu określonego.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Parametry   
 `angle`  
 Kąt obrót w prawo w stopniach.  
  
 `center`  
 Punkt o tym, które można obracać.  
  
 `matrix`  
 Gdy metoda zwróci wartość, zawiera nowe przekształcania obrotu. Należy przydzielić magazynu dla tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przeciwnym razie zwraca wartość S_OK w przypadku powodzenia lub wartość błędu.  
  
## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground
Rysuje tła formantu nadrzędnego w określonym obszarze.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`pWnd`  
 Wskaźnik do okna formantu.  
  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`lpRect`  
 Wskaźnik do prostokąt zakresem powierzchni do rysowania. Wartość domyślna to `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass
Rysuje określony tekst w stylu określony motyw.  
  
  
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
 [in]`hTheme`  
 Dojście do danych motywu okna, lub `NULL`. Platforma korzysta określony motyw pisania tekstu, jeśli ten parametr nie jest `NULL` i kompozycji są obsługiwane. W przeciwnym razie platformę nie używa motyw pisania tekstu.  
  
 Użyj [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) metodę w celu utworzenia `HTHEME`.  
  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`iPartId`  
 Element formantu, który ma wygląd odpowiedni tekst. Aby uzyskać więcej informacji, zobacz części kolumny tabeli w [części i stanów](http://msdn.microsoft.com/library/windows/desktop/bb773210). Jeśli ta wartość wynosi 0, tekstu jest rysowana w domyślnej czcionki lub Czcionka zaznaczona w kontekście urządzenia.  
  
 [in]`iStateId`  
 Stan formantu ma wygląd odpowiedni tekst. Aby uzyskać więcej informacji, zobacz stany kolumna tabeli określonej w [części i stanów](http://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
 [in]`strText`  
 Tekst do rysowania.  
  
 [in]`rect`  
 Granica obszaru, w którym zostanie narysowana określony tekst.  
  
 [in]`dwFlags`  
 Bitowe połączenie (lub) flagi określające, jak określony tekst jest rysowane.  
  
 Jeśli `hTheme` parametr jest `NULL` lub jeśli kompozycji nie są obsługiwane i włączone, `nFormat` parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metoda opisuje prawidłowe flagi. Jeśli są obsługiwane kompozycje, `dwFlags` parametr [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) metoda opisuje prawidłowe flagi.  
  
 [in]`nGlowSize`  
 Rozmiar efekt blask, który jest rysowana na tle przed narysowaniem określony tekst. Wartość domyślna to 0.  
  
 [in]`clrText`  
 Kolor, w którym zostanie narysowana określony tekst. Wartość domyślna to domyślny kolor.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli motyw jest używany do rysowania określonego tekstu. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Motyw definiuje styl wizualny aplikacji. Motyw nie jest używana do pisania tekstu, jeśli `hTheme` parametr jest `NULL`, lub jeśli [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) metoda nie jest obsługiwana, lub jeśli [Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969540) kompozycji (DWM) jest wyłączona .  
  
### <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [Części i Stanów](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Włącz i kontroli kompozycji Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport
Włącza lub wyłącza obsługę modułu Active Accessibility firmy Microsoft.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`bEnable`  
 `TRUE`Aby włączyć obsługę ułatwień dostępu; `FALSE` do wyłączenia ułatwień dostępu pomocy technicznej. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Active Accessibility to technologia oparte na modelu COM poprawia programy sposób i pracy systemu operacyjnego Windows oraz produktów technologii pomocniczej. Zapewnia niezawodne metod publikowania informacji na temat elementów interfejsu użytkownika. Jednak nowszej modelu dostępności o nazwie automatyzacji interfejsu użytkownika firmy Microsoft jest teraz dostępna. Porównanie dwóch technologii, zobacz [Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Użyj [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) metodę, aby określić, czy jest włączona obsługa Microsoft Active Accessibility.  
  
 
### <a name="see-also"></a>Zobacz też  
 [Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag
Usuwa określoną parę tagu XML z określonego bufora.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`strBuffer`  
 Buforu tekstu.  
  
 [in]`lpszTag`  
 Nazwa pary otwierające i zamykające znaczniki XML.  
  
 [out]`strTag`  
 Gdy metoda zwróci wartość, `strTag` parametr zawiera tekst, który jest między otwarcia i zamknięcia XML tagi, które są reprezentowane przez `lpszTag` parametru. Żadnych spacji wiodących lub końcowych jest usuwane z wyników.  
  
 [in]`bIsCharsList`  
 `TRUE`Aby przekonwertować symboli dla znaki specjalne w `strTag` parametru na znaki ucieczki rzeczywiste; `FALSE` nie można dokonać konwersji. Wartość domyślna to `FALSE`. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Para tagu XML składa się z o nazwie otwierające i zamykające znaczniki, które wskazują początek i koniec uruchom tekstu w buforze określona. `strBuffer` Parametr określa buforu i `lpszTag` parametr określa nazwę tagów XML.  
  
 Kodowanie zestawu znaków ucieczki w buforze określona za pomocą tych symboli w poniższej tabeli. Określ `TRUE` dla `bIsCharsList` parametr można przekonwertować symbole w `strTag` parametru na znaki ucieczki rzeczywistych. W poniższej tabeli używa [_T()](../../c-runtime-library/data-type-mappings.md) makra, aby określić symbol i ciągi znaków ucieczki.  
  
|Symbol|Znak ucieczki|  
|------------|----------------------|  
|_T — ("\\\t")|_T("\t")|  
|_T — ("\\\n")|_T("\n")|  
|_T — ("\\\r")|_T("\r")|  
|_T — ("\\\b")|_T("\b")|  
|_T("LT")|_T — ("\<")|  
|_T("GT")|_T(">")|  
|_T("AMP")|_T("&")|  
  
## <a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor
Pobiera bieżący kolor elementu interfejsu użytkownika.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`nColor`  
 Wartość określająca element interfejsu użytkownika, którego kolor są pobierane. Aby uzyskać listę prawidłowych wartości, zobacz `nIndex` parametr [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości kolorów RGB elementu interfejsu użytkownika. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nColor` parametru jest spoza zakresu, zwracana wartość wynosi zero. Ponieważ zero jest również prawidłowe wartości RGB, nie możesz użyć tej metody do ustalenia, czy kolorem systemowym jest obsługiwana przez bieżący system operacyjny. Zamiast tego należy użyć [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927) metody, która zwraca `NULL` Jeśli kolor nie jest obsługiwana.  
  
### <a name="see-also"></a>Zobacz też  

 [Funkcja GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory
 Zwraca wskaźnik do interfejsu ID2D1Factory, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Factory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie obsługują D2D.  
  
## <a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor
Pobiera kursor wstępnie zdefiniowanych podobny dłoni i których identyfikator jest `IDC_HAND`.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście kursora ręcznie.  

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics
Pobiera metryki skojarzone z obszar niekliencki nonminimized systemu Windows.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parametry   
 [w, out]`info`  
 A [NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175) strukturę, która zawiera metryki skalowalne, skojarzone z obszar niekliencki okna nonminimized.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
 
  
### <a name="see-also"></a>Zobacz też   
 [Struktura NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight
 Pobiera wysokość znaki tekstu w bieżącej czcionki.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`bHorz`  
 `TRUE`Aby pobrać wysokość znaków, gdy tekst działa jedynie w pionie. `FALSE` można pobrać wysokość znaków uruchomienie tekstu w pionie. Wartość domyślna to `TRUE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość bieżącej czcionki jest mierzony z jego Wydłużenie górne do jej w dół.  
  
## <a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory
Zwraca wskaźnik do interfejsu IWICImagingFactory, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IWICImagingFactory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie ma WIC pomocy technicznej.  
  
## <a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory
Zwraca wskaźnik do interfejsu IDWriteFactory, który jest przechowywany w danych globalnych. Jeśli nie zainicjowano interfejsu, jest tworzony i ma następujące parametry domyślne.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteFactory, jeśli tworzenie fabryki zakończy się pomyślnie, lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny nie obsługują DirectWrite.  
 
## <a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D
Inicjuje D2D DirectWrite i WIC fabryki. Tę metodę należy wywołać przed zainicjowaniem głównego okna.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parametry   
 `d2dFactoryType`  
 Model wątkowości fabryki D2D i zasoby, które tworzy.  
  
 `writeFactoryType`  
 Wartość określająca, czy obiekt fabryki zapisu zostaną udostępnione lub samodzielnie  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli fabryk zostały intilalizrd, wartość FALSE — w przeciwnym razie  
  
## <a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons
Wskazuje, czy wstępnie zdefiniowane ikony 32-bitowych są obsługiwane.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli wstępnie zdefiniowane 32-bitowych ikony są obsługiwane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `TRUE` Jeśli platforma obsługuje ikony wbudowanych 32-bitowych i jeśli system operacyjny obsługuje 16 bitów na piksel lub więcej i obrazy nie są wyświetlane w dużego kontrastu.  
  
## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport
Wskazuje, czy jest włączona obsługa Microsoft Active Accessibility.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączona jest obsługa ułatwień dostępu; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Active Accessibility został wcześniej rozwiązania na udostępnienie aplikacji. Automatyzacji interfejsu użytkownika firmy Microsoft jest nowy model ułatwień dostępu systemu Microsoft Windows i jest przeznaczona do zaspokoić potrzeby produktów technologii pomocniczej i automatycznego narzędzia do testowania.   
  
 Użyj [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) metody, aby włączyć lub wyłączyć obsługę modułu Active Accessibility.  
  

### <a name="see-also"></a>Zobacz też  
 [Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized
 Określa, czy D2D został zainicjowany  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli został zainicjowany D2D; w przeciwnym razie wartość FALSE.  
  
## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Zapewnia prostą metodę do wywołania systemu Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) metody.  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli [Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969540) kompozycji (DWM) jest włączone; w przeciwnym razie `FALSE`.  
  
### <a name="see-also"></a>Zobacz też    
 [Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Włącz i kontroli kompozycji Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode
 Wskazuje, czy obrazy są aktualnie wyświetlane dużego kontrastu.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli obrazy są aktualnie wyświetlane w trybie dużego kontrastu biały lub czarny; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 W trybie dużego kontrastu czarne krawędzie skierowane światła są białe, i tła jest czarny. W trybie dużego kontrastu białe krawędzie skierowane światła są czarne i tło jest białe.  
  
## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Wskazuje, czy system operacyjny obsługuje warstwowego systemu windows.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli warstwowego systemu windows są obsługiwane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli warstwowego systemu windows są obsługiwane, *inteligentne dokowanie* znaczników Użyj warstwowego systemu windows.  
  
## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Wskazuje, czy platformę używa ikon koloru 32-bitowych wstępnie zdefiniowanych lub ikony niższej rozdzielczości.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Określa, że platformę używać ikon koloru 32-bitowy; `FALSE` określa niższe rozdzielczość ikony. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do `TRUE`.  
  
 Ten element członkowski musi zostać ustawione podczas uruchamiania aplikacji.  
  
## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont
Wskazuje, czy czcionki systemowej jest używany do menu i pasków narzędzi oraz taśmy.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Określa czcionkę systemu; w przeciwnym razie `FALSE`. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do `FALSE`.  
  
 Testowanie ten element członkowski nie jest jedynym sposobem na platformę, aby określić czcionki do użycia. `AFX_GLOBAL_DATA::UpdateFonts` Metoda sprawdza również domyślne i alternatywne czcionki do określenia, jakie style wizualne są dostępne do zastosowania wstążek, menu i pasków narzędzi.  
  
## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand
Przechowuje dojście do kursora ręcznie.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch
Przechowuje dojście do poziomych stretch kursora.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert
Przechowuje dojście do pionowego stretch kursora.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool
Przechowuje dojście ikony narzędzia.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Określa przesunięcie z lewej strony autohide — paska narzędzi po lewej stronie paska dokowania.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 4 pikseli.  
  
## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Określa odstęp między autohide — pasków narzędzi.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 14 pikseli.  
  
## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Określa grubość ramki przeciągania, która służy do wskazywania stanu dokowanych.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 3 pikseli.  
  
## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Określa grubość ramki przeciągania, która służy do wskazywania stanu zmiennoprzecinkowych.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Uwagi  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicjuje ten element członkowski do 4 pikseli.  
  
## <a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange
Wykrywa bieżący stan animacji menu i paska zadań autohide — funkcje pulpitu.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia zmienne framework do stanu niektóre atrybuty komputera użytkownika. Ta metoda wykrywa bieżący stan animacji menu zanikania menu i pasku autohide — funkcje zadań.  
  
## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass
Rejestruje klasę okna określony MFC.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`lpszClassNamePrefix`  
 Nazwa klasy okna do zarejestrowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kwalifikowana nazwa klasy zarejestrowane, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie [wyjątek zasobów](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest rozdzielana średnikami lista `lpszClassNamePrefix` ciąg parametru i reprezentacje szesnastkowym dojść bieżącego wystąpienia aplikacji; kursor aplikacji jest kursor strzałkę, którego identyfikator jest IDC_ARROW; i Pędzel tła. Aby uzyskać więcej informacji na temat rejestrowanie klas okien MFC, zobacz [afxregisterclass —](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Zobacz też    
 [Afxregisterclass —](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [Afxthrowresourceexception —](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a>AFX_GLOBAL_DATA::Resume
 Ponownie inicjuje wskaźników funkcji wewnętrznej, które uzyskują dostęp do metod, które obsługują Windows kompozycje i style wizualne. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`. W trybie debugowania ta metoda potwierdza, czy ta metoda zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po otrzymaniu w ramach [WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247) wiadomości.  
  
## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib
Zapewnia prostą metodę do wywołania systemu Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) metody.  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`hwnd`  
 Dojście do okna warstwowego.  
  
 [in]`crKey`  
 Przezroczysty kolor klucza [Menedżera okien pulpitu](http://msdn.microsoft.com/library/windows/desktop/aa969540) używa się utworzenie okna warstwowego.  
  
 [in]`bAlpha`  
 Wartość alfa używany do opisania nieprzezroczystość okna warstwowego.  
  
 [in]`dwFlags`  
 Bitowe połączenie (lub) flagi określające, które parametry metody do użycia. Określ LWA_COLORKEY do użycia `crKey` parametr jako przezroczysty kolor. Określ LWA_ALPHA do użycia `bAlpha` parametr, aby określić przezroczystość okna warstwowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.   
 
### <a name="see-also"></a>Zobacz też   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont
Tworzy logiczną czcionki.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry   
 [in]`lpLogFont`  
 Wskaźnik do struktury, która zawiera atrybuty czcionki.  
  
 [in]`bHorz`  
 `TRUE`Aby określić, czy tekst jest uruchomiony na poziomie; `FALSE` do określenia, czy tekst jest uruchomiony w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`. W trybie debugowania ta metoda potwierdza, czy ta metoda zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy poziomy czcionki regularne podkreśleniem i pogrubioną czcionką, który jest używany w domyślnych elementów menu. Ta metoda tworzy opcjonalnie regularne czcionki pionowe. Aby uzyskać więcej informacji na temat logicznej czcionek, zobacz [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts
Reintializes czcionki logiczne, które są używane przez platformę.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat logicznej czcionek, zobacz `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors
Inicjuje kolorów, głębi kolorów, pędzle, pióra i obrazów, które są używane przez platformę.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7
Wskazuje, czy aplikacja jest wykonywana w systemie Windows 7 lub nowszej.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient
Określa kolor gradientu active podpisu. Zazwyczaj używane w przypadku Dokowanie okienka.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Określa kolor gradientu nieaktywnym nagłówku. Zazwyczaj używane w przypadku Dokowanie okienka.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList
Tworzy i przechowuje danych globalnych wskaźnik do `ITaskBarList` interfejsu.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `ITaskbarList` interfejsu, jeśli zadanie paska obiekt listy zakończy się pomyślnie; `NULL` Jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny jest mniejsza niż Windows 7.  
  
## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3
Tworzy i przechowuje danych globalnych wskaźnik do `ITaskBarList3` interfejsu.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `ITaskbarList3` interfejsu, jeśli zadanie paska obiekt listy zakończy się pomyślnie; `NULL` Jeśli tworzenie zakończy się niepowodzeniem lub bieżący System operacyjny jest mniejsza niż Windows 7.  
  
## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars
Określa pozycje automatycznie powłoki ukryć paski.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość całkowita z zakodowanym flagi, określające pozycji automatycznie ukryć paski. Może on połączyć następujące wartości: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Wydanie interfejsy uzyskiwaną `GetITaskbarList` i `GetITaskbarList3` metody.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Tworzy i inicjuje obiekt elementu powłoki, na podstawie nazwy podczas analizowania.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Parametry   
 `pszPath`  
 [in] Wskaźnik do nazwy wyświetlanej.  
  
 `pbc`  
 Wskaźnik do kontekstu powiązania kontrolujące operacji analizy.  
  
 `riid`  
 Odwołanie do identyfikatora interfejsu.  
  
 `ppv`  
 [out] Po powrocie z tej funkcji zawiera wskaźnik interfejsu w `riid`. Są to zazwyczaj `IShellItem` lub `IShellItem2`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia; w przeciwnym razie wartość błędu.  

