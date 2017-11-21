---
title: "Ccontrolbar — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
dev_langs: C++
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb4852990bd928a00c5aaf8de4669ed791f68468
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccontrolbar-class"></a>Ccontrolbar — klasa
Klasa podstawowa dla klasy pasków sterowania [cstatusbar —](../../mfc/reference/cstatusbar-class.md), [ctoolbar —](../../mfc/reference/ctoolbar-class.md), [cdialogbar —](../../mfc/reference/cdialogbar-class.md), [crebar —](../../mfc/reference/crebar-class.md), i [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|Konstruuje `CControlBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Zwraca rozmiar paska dynamicznej kontroli jako [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Zwraca rozmiar pasek sterowania jako [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|Zwraca bieżące wymiary powierzchni paska sterowania; w tym obramowania.|  
|[CControlBar::DoPaint](#dopaint)|Renderuje obramowania i uchwyt paska sterowania.|  
|[CControlBar::DrawBorders](#drawborders)|Renderuje obramowania paska sterowania.|  
|[CControlBar::DrawGripper](#drawgripper)|Renderuje uchwyt paska sterowania.|  
|[CControlBar::EnableDocking](#enabledocking)|Umożliwia, aby pasek sterowania był zadokowany lub przestawny.|  
|[CControlBar::GetBarStyle](#getbarstyle)|Pobiera ustawienia stylu paska sterowania.|  
|[CControlBar::GetBorders](#getborders)|Pobiera wartości obramowania paska sterowania.|  
|[CControlBar::GetCount](#getcount)|Zwraca liczbę z systemem innym niż `HWND` elementów w pasek sterowania.|  
|[CControlBar::GetDockingFrame](#getdockingframe)|Zwraca wskaźnik do ramki, w której jest zadokowany pasek sterowania.|  
|[CControlBar::IsFloating](#isfloating)|Zwraca wartość niezerową, jeśli dany pasek sterowania jest przestawny.|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Wywołuje obsługę poleceń interfejsu użytkownika.|  
|[CControlBar::SetBarStyle](#setbarstyle)|Modyfikuje ustawienia stylu paska sterowania.|  
|[CControlBar::SetBorders](#setborders)|Ustawia wartości obramowania paska sterowania.|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Zmienia lokalnego właściciela paska sterowania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Lokalny właściciel paska sterowania.|  
  
## <a name="remarks"></a>Uwagi  
 Pasek sterowania to okno, które jest zazwyczaj wyrównane do lewej lub prawej strony okna ramki. Może on zawierać elementy podrzędne, które są `HWND`- based formanty, które są systemu windows, które Generowanie i odpowiadać na komunikaty systemu Windows lub z systemem innym niż — `HWND`— na podstawie elementów, które nie są systemu windows i są zarządzane przez kod aplikacji lub kodu framework. Pola listy i formantach edycyjnych są przykłady `HWND`- formanty oparte na; okienka paska stanu i mapy bitowej przycisków to przykłady z systemem innym niż — `HWND`— na podstawie kontrolki.  
  
 Okienka paska sterowania to zazwyczaj okienka podrzędne dla nadrzędnej ramki okna i zazwyczaj elementy równorzędne dla widoku klienta lub klienta MDI ramki okna. Obiekt `CControlBar` używa informacji dotyczących prostokąta klienta okna nadrzędnego, w celu ustalenia własnej pozycji. Następnie informuje okno nadrzędne, ile miejsca pozostaje nieprzydzielonego, w obszarze klienta okna nadrzędnego.  
  
 Aby uzyskać więcej informacji na temat funkcji `CControlBar`, zobacz:  
  
- [Paski sterowania](../../mfc/control-bars.md)  
  
- [Uwaga techniczna 31: Paski sterowania](../../mfc/tn031-control-bars.md).  
  
-   Artykuł bazy wiedzy Q242577: PRB: Aktualizacja obsługi poleceń interfejsu użytkownika nie działa dla menu dołączonego do okna dialogowego  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout  
 Struktura wywołuje funkcji członkowskiej do obliczenia wymiarów dynamiczne paska narzędzi.  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>Parametry  
 `nLength`  
 Wymiar żądanego paska kontroli poziomej lub pionowej, w zależności od `dwMode`.  
  
 `nMode`  
 Następujące flagi wstępnie zdefiniowane są używane do określenia wysokość i szerokość paska dynamicznej kontroli. Użyj wartości bitowe lub (&#124;) operatora łączenia flag.  
  
|Flagi trybu układu|Co to oznacza|  
|-----------------------|-------------------|  
|`LM_STRETCH`|Wskazuje, czy pasek sterowania powinny być rozciągany tak, aby rozmiar ramki. Zestaw, jeśli nie jest pasek dokowania paska (niedostępne dla dokowanie). Nie ustawiona, gdy pasek jest zadokowane i przestawne (dostępne dla dokowanie). Jeśli ustawiona, `LM_STRETCH` ignoruje `nLength` i zwraca wymiary na podstawie `LM_HORZ` stanu. `LM_STRETCH`działa podobnie do `bStretch` parametru użytego w [CalcFixedLayout](#calcfixedlayout); Zobacz tej funkcji członkowskiej, aby uzyskać więcej informacji na temat relacji między rozciąganie i orientacji.|  
|`LM_HORZ`|Wskazuje, że pasek jest zorientowany poziomo czy pionowo. Ustaw Jeśli orientacji poziomej pasku, a jeśli tak jest w orientacji pionowej, nie jest ustawiona. `LM_HORZ`działa podobnie do `bHorz` parametru użytego w [CalcFixedLayout](#calcfixedlayout); Zobacz tej funkcji członkowskiej, aby uzyskać więcej informacji na temat relacji między rozciąganie i orientacji.|  
|**LM_MRUWIDTH**|Ostatnio używane szerokość dynamicznych. Ignoruje `nLength` parametru i używa zapamiętanych ostatnio używane szerokości.|  
|`LM_HORZDOCK`|Poziomy zadokowane wymiarów. Ignoruje `nLength` parametrów i zwraca rozmiar dynamicznej z największych szerokości.|  
|`LM_VERTDOCK`|Pionowy zadokowane wymiarów. Ignoruje `nLength` parametrów i zwraca rozmiar dynamicznej z największą wysokość.|  
|`LM_LENGTHY`|Jeśli `nLength` wskazuje zamiast szerokość, wysokość (kierunku Y).|  
|`LM_COMMIT`|Resetuje **LM_MRUWIDTH** Bieżąca szerokość przestawne pasek sterowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasek sterowania rozmiar, w pikselach, o [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby zapewnić dynamiczne układu w pochodzi od klasy `CControlBar`. Pochodne klasy MFC `CControlBar`, takich jak [ctoolbar —](../../mfc/reference/ctoolbar-class.md)ich implementacji i przesłonić tę funkcję elementu członkowskiego.  
  
##  <a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout  
 Wywołanie tej funkcji Członkowskich do obliczenia rozmiaru poziomy pasek sterowania.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 `bStretch`  
 Wskazuje, czy pasek powinny być rozciągany tak, aby rozmiar ramki. `bStretch` Parametr jest różna od zera, gdy pasek nie jest pasek dokowania (niedostępne dla dokowanie) i jest 0 gdy jest zadokowane i przestawne (dostępne dla dokowanie).  
  
 `bHorz`  
 Wskazuje, że pasek jest zorientowany poziomo czy pionowo. `bHorz` Parametr jest różna od zera, jeśli pasku jest orientacji poziomej i wynosi 0, jeśli jest w orientacji pionowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasek sterowania rozmiar, w pikselach, o `CSize` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Paski sterowania, takie jak paski narzędzi mogą stretch poziomie lub pionie umożliwiających przycisków znajdujących się w pasek sterowania.  
  
 Jeśli `bStretch` jest **TRUE**, stretch wymiaru wzdłuż orientację pochodzącymi `bHorz`. Innymi słowy Jeśli `bHorz` jest **FALSE**, pasek sterowania jest rozciągany w pionie. Jeśli `bStretch` jest **FALSE**, stretch nie występuje. W poniższej tabeli przedstawiono możliwe permutacji, a wynikowy style pasek sterowania, z `bStretch` i `bHorz`.  
  
|bStretch|bHorz|Rozciąganie|Orientacja|Dokowanie nie dokowanie|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**WARTOŚĆ TRUE**|**WARTOŚĆ TRUE**|Rozciąganie pozioma|Orientacji poziomej|Dokowanie nie|  
|**WARTOŚĆ TRUE**|**WARTOŚĆ FALSE**|Rozciąganie w pionie|Ukierunkowane pionowo|Dokowanie nie|  
|**WARTOŚĆ FALSE**|**WARTOŚĆ TRUE**|Nie rozciąganie dostępne|Orientacji poziomej|Dokowanie|  
|**WARTOŚĆ FALSE**|**WARTOŚĆ FALSE**|Nie rozciąganie dostępne|Ukierunkowane pionowo|Dokowanie|  
  
##  <a name="calcinsiderect"></a>CControlBar::CalcInsideRect  
 Struktura wywołuje tę funkcję, aby obliczyć obszaru klienckiego pasek sterowania.  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Zawiera bieżącego rozmiaru pasek sterowania; w tym obramowania.  
  
 `bHorz`  
 Wskazuje, że pasek jest zorientowany poziomo czy pionowo. `bHorz` Parametr jest różna od zera, jeśli pasku jest orientacji poziomej i wynosi 0, jeśli jest w orientacji pionowej.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przed pasek sterowania jest rysowane.  
  
 Należy przesłonić tę funkcję, aby dostosować renderowaniem obramowań i pasek uchwytu pasek sterowania.  
  
##  <a name="ccontrolbar"></a>CControlBar::CControlBar  
 Konstruuje `CControlBar` obiektu.  
  
```  
CControlBar();
```  
  
##  <a name="dopaint"></a>CControlBar::DoPaint  
 Wywoływane przez platformę, by renderować obramowania i paska uchwytu pasek sterowania.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskazuje kontekstu urządzenia używanego do renderowania obramowania i uchwytu pasek sterowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować zachowanie rysowania pasek sterowania.  
  
 Inna metoda dostosowania jest zastąpienie `DrawBorders` i `DrawGripper` funkcje i Dodaj niestandardowy kod rysowania obramowań i uchwytu. Ponieważ te metody są wywoływane przy użyciu domyślnej `DoPaint` metoda, zastępująca `DoPaint` nie jest wymagana.  
  
##  <a name="drawborders"></a>CControlBar::DrawBorders  
 Wywoływane przez platformę, by renderować obramowania pasek sterowania.  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskazuje kontekstu urządzenia używanego do renderowania obramowania pasek sterowania.  
  
 `rect`  
 A `CRect` obiektu zawierającego wymiary pasek sterowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować wygląd obramowań pasek sterowania.  
  
##  <a name="drawgripper"></a>CControlBar::DrawGripper  
 Wywoływane przez platformę, by renderować uchwytu pasek sterowania.  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskazuje kontekstu urządzenia używanego do renderowania uchwytu pasek sterowania.  
  
 `rect`  
 A `CRect` obiektu zawierającego wymiary uchwytu pasek sterowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować wygląd uchwytu pasek sterowania.  
  
##  <a name="enabledocking"></a>CControlBar::EnableDocking  
 Wywołanie tej funkcji, aby włączyć pasek sterowania możliwości dokowania.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDockStyle`  
 Określa, czy pasek sterowania obsługuje dokowanie i stron jej okna nadrzędnego, do której może być zadokowany pasek sterowania, jeśli jest to obsługiwane. Może to być jeden lub więcej z następujących czynności:  
  
- `CBRS_ALIGN_TOP`Umożliwia dokowanie u góry obszaru klienckiego.  
  
- `CBRS_ALIGN_BOTTOM`Umożliwia dokowanie w dolnej części obszaru klienckiego.  
  
- `CBRS_ALIGN_LEFT`Umożliwia dokowania po lewej stronie obszaru klienckiego.  
  
- `CBRS_ALIGN_RIGHT`Umożliwia dokowania po prawej stronie obszaru klienckiego.  
  
- `CBRS_ALIGN_ANY`Umożliwia dokowanie na dowolnej stronie obszaru klienta.  
  
- `CBRS_FLOAT_MULTI`Umożliwia wielu pasków sterowania jest przestawione w jednej ramce mini okno.  
  
 Jeśli jest to 0 (oznacza to, co oznacza żadnych flag), nie będzie dokowania pasków sterowania.  
  
### <a name="remarks"></a>Uwagi  
 Strony określony musi odpowiadać jednej strony włączone dla dokowanie w oknie ramowym docelowy, lub pasek sterowania nie może być zadokowane do tej ramki okna.  
  
##  <a name="getbarstyle"></a>CControlBar::GetBarStyle  
 Wywołanie tej funkcji, aby określić, które **CBRS_** (stylów formantu paska) ustawienia są aktualnie ustawione dla pasek sterowania.  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący **CBRS_** (stylów formantu paska) ustawienia pasek sterowania. Zobacz [CControlBar::SetBarStyle](#setbarstyle) Aby uzyskać pełną listę dostępnych stylów.  
  
### <a name="remarks"></a>Uwagi  
 Nie obsługuje **WS_** style (styl okna).  
  
##  <a name="getborders"></a>CControlBar::GetBorders  
 Zwraca bieżące wartości obramowania pasek sterowania.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` obiekt, który zawiera bieżący szerokość (w pikselach) po obu stronach obiektu pasek sterowania. Na przykład wartość `left` elementu członkowskiego, z [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektów, to szerokość krawędzi lewej.  
  
##  <a name="getcount"></a>CControlBar::GetCount  
 Zwraca liczbę z systemem innym niż `HWND` elementów na `CControlBar` obiektu.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba spoza `HWND` elementów na `CControlBar` obiektu. Ta funkcja zwraca wartość 0 dla [cdialogbar —](../../mfc/reference/cdialogbar-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Typ elementu zależy od obiektu pochodnego: panele dla [cstatusbar —](../../mfc/reference/cstatusbar-class.md) obiekty i przycisków i separatory dla [ctoolbar —](../../mfc/reference/ctoolbar-class.md) obiektów.  
  
##  <a name="getdockingframe"></a>CControlBar::GetDockingFrame  
 Wywołanie tej funkcji Członkowskich uzyskać wskaźnik do bieżącego okna ramki, do którego jest zadokowany z pasek sterowania.  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okno ramowe w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
 Jeśli pasek sterowania nie jest zadokowany okno ramowe (jeśli jest zmiennoprzecinkową pasek sterowania), ta funkcja zwraca wskaźnik do elementu nadrzędnego [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat paski sterowania zadokowane, zobacz [CControlBar::EnableDocking](#enabledocking) i [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
##  <a name="isfloating"></a>CControlBar::IsFloating  
 Wywołanie tej funkcji Członkowskich do ustalenia, czy pasek sterowania jest przestawne lub dokowanych.  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pasek sterowania jest zmiennoprzecinkową; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zmień stan pasek sterowania z zadokowane i przestawne, wywołania [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).  
  
##  <a name="m_bautodelete"></a>CControlBar::m_bAutoDelete  
 Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_bAutoDelete`jest publiczny zmiennej typu **BOOL**.  
  
 Obiekt pasek sterowania zwykle jest osadzony w obiekcie okna ramowego. W takim przypadku `m_bAutoDelete` wynosi 0, ponieważ obiekt osadzony pasek sterowania zostanie zniszczony, gdy okno ramowe zostanie zniszczony.  
  
 Ustaw wartość tej zmiennej na wartość niezerową Jeśli przydzielone `CControlBar` obiektów na stercie, nie jest planowane wywołać **usunąć**.  
  
##  <a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner  
 Lokalny właściciel paska sterowania.  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, aby zaktualizować stan paska narzędzi lub paska stanu.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pTarget`  
 Wskazuje główną ramkę okna aplikacji. Ten wskaźnik jest używany do przesyłania wiadomości aktualizacji.  
  
 `bDisableIfNoHndler`  
 Flaga wskazująca, czy formant, który ma bez obsługi aktualizacji powinna być automatycznie wyświetlana jako wyłączone.  
  
### <a name="remarks"></a>Uwagi  
 Aby zaktualizować poszczególnych przycisk lub okienko, użyj `ON_UPDATE_COMMAND_UI` makra mapy wiadomości, można odpowiednio ustawić programu obsługi aktualizacji. Zobacz [on_update_command_ui —](message-map-macros-mfc.md#on_update_command_ui) Aby uzyskać więcej informacji o korzystaniu z tego makra.  
  
 `OnUpdateCmdUI`jest wywoływane przez platformę, gdy aplikacja jest w stanie bezczynności. Okno ramowe aktualizacji musi być oknem podrzędnym co najmniej pośrednio okno ramowe widoczne. `OnUpdateCmdUI`jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="setbarstyle"></a>CControlBar::SetBarStyle  
 Wywołanie tej funkcji, aby ustawić żądaną **CBRS_** style pasek sterowania.  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Żądany style pasek sterowania. Może to być jeden lub więcej z następujących czynności:  
  
- `CBRS_ALIGN_TOP`Umożliwia pasek sterowania możliwości dokowania u góry obszaru klienckiego okna ramki.  
  
- `CBRS_ALIGN_BOTTOM`Umożliwia pasek sterowania możliwości dokowania z dolną krawędzią obszaru klienckiego okna ramki.  
  
- `CBRS_ALIGN_LEFT`Umożliwia pasek sterowania na jest zadokowany do lewej strony obszaru klienckiego okna ramki.  
  
- `CBRS_ALIGN_RIGHT`Umożliwia pasek sterowania możliwości dokowania do prawej krawędzi obszaru klienckiego okna ramki.  
  
- `CBRS_ALIGN_ANY`Umożliwia pasek sterowania możliwości dokowania do dowolnej krawędzi obszaru klienckiego okna ramki.  
  
- `CBRS_BORDER_TOP`Powoduje, że obramowanie jest narysowanie wzdłuż górnej krawędzi pasek sterowania, gdy będzie ona widoczna.  
  
- `CBRS_BORDER_BOTTOM`Powoduje, że rysowane na dolnej krawędzi pasek sterowania, gdy będą widoczne obramowanie.  
  
- `CBRS_BORDER_LEFT`Powoduje, że obramowanie jest narysowanie do lewej krawędzi pasek sterowania, gdy będzie ona widoczna.  
  
- `CBRS_BORDER_RIGHT`Powoduje, że rysowane na prawej krawędzi paska kontroli, gdy będą widoczne obramowanie.  
  
- `CBRS_FLOAT_MULTI`Umożliwia wielu pasków sterowania jest przestawione w jednej ramce mini okno.  
  
- `CBRS_TOOLTIPS`Powoduje, że etykietki narzędzia ma być wyświetlany dla pasek sterowania.  
  
- `CBRS_FLYBY`Powoduje, że tekst komunikatu do aktualizacji w tym samym czasie jako etykietek narzędzi.  
  
- **CBRS_GRIPPER** powoduje, że uchwytu, podobnie jak na paskami w **crebar —** obiektu, które będą używane dla każdego `CControlBar`-klasy.  
  
### <a name="remarks"></a>Uwagi  
 Nie wpływa na **WS_** ustawienia (styl okna).  
  
##  <a name="setborders"></a>CControlBar::SetBorders  
 Wywołanie tej funkcji, aby określić rozmiar obramowania pasek sterowania.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *cxLeft*  
 Szerokość (w pikselach) pasek sterowania lewej krawędzi.  
  
 *cyTop*  
 Wysokość (w pikselach) pasek sterowania górnej krawędzi.  
  
 *cxRight*  
 Szerokość (w pikselach) pasek sterowania prawej krawędzi.  
  
 *cyBottom*  
 Wysokość (w pikselach) pasek sterowania dolnej krawędzi.  
  
 `lpRect`  
 Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera Bieżąca szerokość (w pikselach) każdej krawędzi obiektu pasek sterowania.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia górnej i dolnej krawędzi pasek sterowania na 5 pikseli i lewe i prawe obramowanie pikseli 2:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner  
 Zmienia lokalnego właściciela paska sterowania.  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do `CWnd` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Ctoolbar — klasa](../../mfc/reference/ctoolbar-class.md)   
 [Cdialogbar — klasa](../../mfc/reference/cdialogbar-class.md)   
 [Cstatusbar — klasa](../../mfc/reference/cstatusbar-class.md)   
 [Crebar — klasa](../../mfc/reference/crebar-class.md)
