---
title: Klasa CSmartDockingInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
dev_langs:
- C++
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3328eacb9789b892a271208193e82546eb73f7e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csmartdockinginfo-class"></a>Klasa CSmartDockingInfo
Określa wygląd znaczniki inteligentnego dokowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CSmartDockingInfo::CSmartDockingInfo`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSmartDockingInfo::CopyTo](#copyto)|Kopiuje bieżącego inteligentne dokowania parametrów informacji o do udostępnionych [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) obiektu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Określa, czy ma być używany bieżący kolor motywu, gdy platformę Wyświetla znaczniki inteligentnego dokowania.|  
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Określa kolor tła podstawowej znaczniki inteligentnego dokowania.|  
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Określa kolor, który zastępuje `m_clrToneSrc` inteligentne dokowania bitmap znacznika.|  
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Określa kolor inteligentne dokowania bitmapy znacznika.|  
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Określa kolor inteligentne dokowania map bitowych znacznika, gdy są one niewidoczne.|  
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Określa przesunięcie centralnego grupy znaczniki inteligentnego dokowania z prostokąta centralnej grupy granic.|  
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Określa całkowity rozmiar wszystkich znaczniki inteligentnego dokowania w grupie.|  
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definiuje identyfikatorów map bitowych używanego w ramach dla znaczniki inteligentnego dokowania, które nie są wyróżnione zasobów.|  
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definiuje identyfikatorów map bitowych używanego w ramach dla znaczniki inteligentnego dokowania, które są wyróżnione zasobów.|  
  
## <a name="remarks"></a>Uwagi  
 Uchwyty framework inteligentne znaczników dokowania wewnętrznie. Na poniższej ilustracji przedstawiono standardowe znaczniki inteligentnego dokowania:  
  
 ![Standardowe znaczniki inteligentnego dokowania](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")  
  
 Na tym rysunku obraz po lewej stronie pokazuje centralna grupa inteligentne dokowania znacznik niezawierający Dokowanie do karty włączone. Obraz w środku przedstawiono prawej krawędzi inteligentne znacznika dokowania. Obraz po prawej stronie pokazuje centralna grupa inteligentne dokowania znacznik mające Dokowanie do karty włączone. Inteligentne znacznika dokowania centralna grupa ma głównego mapy bitowej i pięć inteligentne dokowania bitmapy znacznika.  
  
 Można dostosować następujące parametry znaczniki inteligentnego dokowania:  
  
-   Kolor. Na przykład można zastąpić niebieski znaczników na ilustracji kolorów zdefiniowanych przez użytkownika.  
  
-   Przezroczysty kolor.  
  
-   Przesunięcie znacznika dokowania inteligentne w grupie centralnej obramowanie z prostokątem.  
  
-   Główne mapy bitowej, która reprezentuje grupę centralnej.  
  
-   Mapy bitowe, które reprezentuje regularne i wyróżnione znaczniki inteligentnego dokowania.  
  
 Na poniższej ilustracji przedstawiono przykład znaczniki inteligentnego dokowania, które zostały dostosowane:  
  
 ![Znaczniki niestandardowe dla inteligentnych dokowanie](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDockingManager.h  
  
##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo  
 Kopiuje bieżących inteligentne dokowania parametrów do udostępnionych [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) obiektu.  
  
```  
void CopyTo(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `params`  
 Obiekt typu `CSmartDockingInfo` który jest wypełniane przy użyciu bieżących inteligentne parametrów dokowania.  
  
##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading  
 Określa, czy ma być używany bieżący kolor motywu, gdy platformę Wyświetla znaczniki inteligentnego dokowania.  
  
```  
BOOL m_bUseThemeColorInShading;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, znaczniki są rysowane przy użyciu bieżący kolor motywu; w przeciwnym razie są rysowane znaczniki światła kolorem niebieskim.  
  
 Wartość domyślna to `FALSE`.  
  
##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground  
 Określa kolor tła podstawowej znaczniki inteligentnego dokowania.  
  
```  
COLORREF m_clrBaseBackground;  
```  
  
##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest  
 Określa kolor, który będzie zastępował `m_clrToneSrc` inteligentne dokowania bitmap znacznika.  
  
```  
COLORREF m_clrToneDest;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw tę wartość można zmienić kolor znacznika map bitowych programowo. Na przykład jeśli chcesz zmienić kolor standardowych znaczników zapewnionej w ramach, ta wartość żądany kolor. Domyślnie [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) ma ustawioną wartość RGB (61, 123, 241) (kolor niebieskawy).  
  
 Aby zmienić kolor znaczniki niestandardowe, należy określić zarówno `m_clrToneDest` i `m_clrToneSrc`.  
  
##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc  
 Określa kolor inteligentne dokowania bitmapy znacznika.  
  
```  
COLORREF m_clrToneSrc;  
```  
  
### <a name="remarks"></a>Uwagi  
 Tę wartość można ustawić tylko wtedy, gdy chcesz zastąpić kolor niestandardową mapę bitową z innym kolorem. Nie masz można ustawić tej wartości, aby zmienić kolor standardowego (struktura dostępna) znacznika.  
  
 Użyj `(COLORREF)-1` pozostawić członek grupy dokowania inteligentne puste.  
  
##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent  
 Określa kolor inteligentne dokowania map bitowych znacznika, gdy są one niewidoczne.  
  
```  
COLORREF m_clrTransparent;  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy ustawić tę wartość podczas wyświetlania niestandardowe znaczniki i niestandardowych map bitowych w grupie dokowania.  
  
##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset  
 Określa przesunięcie od centralna grupa znaczniki inteligentnego dokowania i granice prostokąta grupy centralnej.  
  
```  
int m_nCentralGroupOffset;  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy podać tę wartość, jeśli chcesz zmienić domyślne przesunięcie niestandardowe znaczniki i granic centralnej grupy znaczniki inteligentnego dokowania. Przesunięcie domyślna to 5 pikseli.  
  
##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal  
 Określa całkowity rozmiar obwiedni prostokąt ograniczający wszystkie znaczniki inteligentnego dokowania w grupie centralnej.  
  
```  
CSize m_sizeTotal;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_sizeTotal` rozmiar prostokątem znacznika centralnego grupy. Należy podać tę wartość, jeśli używasz niestandardowych map bitowych znaczników.  
  
##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID  
 Definiuje identyfikatorów mapy bitowe, które są używane do-wyróżnione niestandardowe znaczniki inteligentnego dokowania zasobów.  
  
```  
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Uwagi  
 Wypełnienie tej tablicy identyfikatorów bitmapy reprezentujący znaczniki inteligentnego dokowania zasobów. `AFX_SD_MARKERS_NUM` obecnie jest zdefiniowany jako 5. Tablica wypełnienie w następujący sposób:  
  
 `params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;`  
  
 `params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;`  
  
 `params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;`  
  
 `params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;`  
  
 `params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;`  
  
##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID  
 Definiuje identyfikatorów mapy bitowe, które są używane do wyróżnione niestandardowe znaczniki dokowania inteligentne zasobów.  
  
```  
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Uwagi  
 Wypełnienie tej tablicy identyfikatorów bitmapy reprezentujący wyróżnione znaczniki inteligentnego dokowania zasobów. `AFX_SD_MARKERS_NUM` obecnie jest zdefiniowany jako 5. Tablica wypełnienie w następujący sposób:  
  
 `params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;`  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
