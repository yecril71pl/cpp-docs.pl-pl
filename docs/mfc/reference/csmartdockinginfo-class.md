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
ms.openlocfilehash: 653be2fb1847403436bccb86807da382ef09cc25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018213"
---
# <a name="csmartdockinginfo-class"></a>Klasa CSmartDockingInfo
Definiuje wygląd znaczników inteligentnego dokowania.  
  
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
|[CSmartDockingInfo::CopyTo](#copyto)|Kopiuje bieżący inteligentnego dokowania parametrów informacji o do podanych [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) obiektu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Określa, czy użyć bieżący kolor motywu, jeśli struktura Wyświetla znaczników inteligentnego dokowania.|  
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Określa kolor tła podstawowy znaczników inteligentnego dokowania.|  
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Określa kolor, który zastępuje `m_clrToneSrc` inteligentnego dokowania bitmap znacznika.|  
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Określa kolor inteligentnego dokowania mapy bitowe znacznika.|  
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Określa kolor inteligentnego dokowania mapy bitowe znacznika, gdy są one niewidoczne.|  
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Określa przesunięcie grupy centralnej znaczników inteligentnego dokowania z granic prostokąta centralnego grupy.|  
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Określa całkowity rozmiar wszystkich znaczników inteligentnego dokowania w grupie.|  
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definiuje zasób identyfikatory mapy bitowe, w ramach używany dla znaczników inteligentnego dokowania, które nie są wyróżnione.|  
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definiuje zasób identyfikatory mapy bitowe, w ramach używany dla znaczników inteligentnego dokowania, które są wyróżnione.|  
  
## <a name="remarks"></a>Uwagi  
 Uchwyty framework inteligentne znaczniki dokowania wewnętrznie. Poniższa ilustracja przedstawia standardowych znaczników inteligentnego dokowania:  
  
 ![Standardowa znaczników inteligentnego dokowania](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")  
  
 Na tym rysunku obraz po lewej stronie zawiera grupy centralnej inteligentnego dokowania znacznik bez dokowanie karty włączone. Na ilustracji w środku przedstawiono znacznik inteligentnego dokowania prawej krawędzi. Obraz po prawej stronie pokazuje centralna grupa inteligentnego dokowania znacznik mających dokowanie karty włączone. Znacznika inteligentnego dokowania centralna grupa ma głównej mapy bitowej i pięć inteligentnego dokowania bitmap znacznika.  
  
 Można dostosować następujące parametry znaczników inteligentnego dokowania.  
  
-   Kolor. Na przykład można zastąpić koloru niebieskiego znaczników na rysunku kolorów zdefiniowanych przez użytkownika.  
  
-   Przezroczysty kolor.  
  
-   Przesunięcie znacznika inteligentnego dokowania w grupie centralnej obramowania prostokąta otaczający.  
  
-   Głównej mapy bitowej, która reprezentuje grupę centralnej.  
  
-   Mapy bitowe, które reprezentuje regularne i wyróżnione znaczników inteligentnego dokowania.  
  
 Na poniższej ilustracji przedstawiono przykład znaczników inteligentnego dokowania, które zostały dostosowane:  
  
 ![Niestandardowych znaczników inteligentnego dokowania](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDockingManager.h  
  
##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo  
 Kopiuje bieżącego inteligentnego dokowania parametrów do udostępnionych [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) obiektu.  
  
```  
void CopyTo(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parametry  
*params*<br/>
[out] Obiekt typu `CSmartDockingInfo` , jest wypełniana przy użyciu bieżących parametrów inteligentnego dokowania.  
  
##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading  
 Określa, czy użyć bieżący kolor motywu, jeśli struktura Wyświetla znaczników inteligentnego dokowania.  
  
```  
BOOL m_bUseThemeColorInShading;  
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku opcji TRUE znaczniki są wyświetlane przy użyciu bieżący kolor motywu. w przeciwnym razie znaczników są rysowane w jasny kolor niebieski.  
  
 Wartość domyślna to FALSE.  
  
##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground  
 Określa kolor tła podstawowy znaczników inteligentnego dokowania.  
  
```  
COLORREF m_clrBaseBackground;  
```  
  
##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest  
 Określa kolor, który zastąpi `m_clrToneSrc` inteligentnego dokowania bitmap znacznika.  
  
```  
COLORREF m_clrToneDest;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw tę wartość, aby zmienić kolor znacznika map bitowych programowo. Na przykład jeśli chcesz zmienić kolor znaczników standardowe wyposażone w ramach, ta wartość żądany kolor. Domyślnie [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) ustawiono RGB (61 123, 241) (kolor niebieskawy).  
  
 Aby zmienić kolor znaczniki niestandardowe, należy określić zarówno `m_clrToneDest` i `m_clrToneSrc`.  
  
##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc  
 Określa kolor inteligentnego dokowania mapy bitowe znacznika.  
  
```  
COLORREF m_clrToneSrc;  
```  
  
### <a name="remarks"></a>Uwagi  
 Tę wartość można ustawić tylko wtedy, gdy chcesz zastąpić kolor niestandardowej mapy bitowej przy użyciu innego koloru. Nie masz ustawić tę wartość, jeśli zmieniasz kolor standardowy (struktura dostępna) znacznika.  
  
 Użyj `(COLORREF)-1` pozostawić puste członkiem inteligentnego dokowania grupy.  
  
##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent  
 Określa kolor inteligentnego dokowania mapy bitowe znacznika, gdy są one niewidoczne.  
  
```  
COLORREF m_clrTransparent;  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy ustawić tę wartość podczas wyświetlania niestandardowe znaczniki i niestandardowych map bitowych w grupie dokowania.  
  
##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset  
 Określa przesunięcie między centralna grupa znaczników inteligentnego dokowania i granice prostokąta centralnego grupy.  
  
```  
int m_nCentralGroupOffset;  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy określić tę wartość, jeśli chcesz zmienić domyślne przesunięcie niestandardowe znaczniki i granice centralna grupa znaczników inteligentnego dokowania. Przesunięcie domyślna to 5 pikseli.  
  
##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal  
 Określa całkowity rozmiar otaczający prostokąt, który otacza wszystkich znaczników inteligentnego dokowania centralnego grupy.  
  
```  
CSize m_sizeTotal;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_sizeTotal` rozmiarowi prostokąt otaczający znacznika centralnego grupy. Należy określić tę wartość, jeśli używasz niestandardowych map bitowych dla znaczników.  
  
##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID  
 Definiuje zasób identyfikatory mapy bitowe, które są używane na potrzeby-wyróżnione niestandardowych znaczników inteligentnego dokowania.  
  
```  
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Uwagi  
 Wypełnienie tej tablicy identyfikatory mapy bitowe, reprezentujący znaczników inteligentnego dokowania. AFX_SD_MARKERS_NUM jest obecnie zdefiniowany jako 5. Wypełnienia tablicy w następujący sposób:  
  
```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```
  
##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID  
 Definiuje zasób identyfikatory mapy bitowe, które są używane na potrzeby wyróżnione niestandardowe inteligentnego dokowania znaczników.  
  
```  
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Uwagi  
 Wypełnienie tej tablicy identyfikatory mapy bitowe, reprezentujący wyróżnione znaczników inteligentnego dokowania. AFX_SD_MARKERS_NUM jest obecnie zdefiniowany jako 5. Wypełnienia tablicy w następujący sposób:  
  
```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
