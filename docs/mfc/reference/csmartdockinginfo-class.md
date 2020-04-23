---
title: Klasa CSmartDockingInfo
ms.date: 11/19/2018
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
ms.openlocfilehash: ebb5e75b5b298097cfce043bd83ec88ca0ab4030
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751295"
---
# <a name="csmartdockinginfo-class"></a>Klasa CSmartDockingInfo

Definiuje wygląd inteligentnych znaczników dokowania.

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
|[CSmartDockingInfo::CopyTo](#copyto)|Kopiuje bieżące parametry informacji inteligentnego dokowania do dostarczonego obiektu [CSmartDockingInfo.](../../mfc/reference/csmartdockinginfo-class.md)|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Określa, czy bieżący kolor motywu ma być używany, gdy w ramach wyświetlane są inteligentne znaczniki dokowania.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Określa podstawowy kolor tła znaczników inteligentnego dokowania.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Określa kolor, który `m_clrToneSrc` zastępuje w mapach bitowych znacznika inteligentnego dokowania.|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Określa kolor map bitowych znaczników inteligentnego dokowania.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Określa kolor map bitowych znaczników inteligentnego dokowania, gdy są przezroczyste.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Określa przesunięcie centralnej grupy znaczników inteligentnego dokowania od granic prostokąta grupy centralnej.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Określa całkowity rozmiar wszystkich znaczników inteligentnego dokowania w grupie.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definiuje identyfikatory zasobów map bitowych, których struktura używa dla znaczników inteligentnego dokowania, które nie są wyróżnione.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definiuje identyfikatory zasobów map bitowych, których struktura używa dla znaczników inteligentnego dokowania, które są wyróżnione.|

## <a name="remarks"></a>Uwagi

Struktura obsługuje inteligentne znaczniki dokowania wewnętrznie. Na poniższej ilustracji przedstawiono standardowe inteligentne znaczniki dokowania:

![Standardowe znaczniki do inteligentnego dokowania](../../mfc/reference/media/nextsdmarkers.png "Standardowe znaczniki do inteligentnego dokowania")

Na tym rysunku obraz po lewej stronie przedstawia znacznik inteligentnego dokowania grupy centralnej, który nie ma włączonego dokowania do karty. Obraz w środku przedstawia znacznik inteligentnego dokowania prawej krawędzi. Obraz po prawej stronie przedstawia znacznik inteligentnego dokowania grupy centralnej, który ma włączone dokowanie do karty. Znacznik inteligentnego dokowania grupy centralnej ma główną mapę bitową i pięć map bitowych znacznika inteligentnego dokowania.

Można dostosować następujące parametry inteligentnych znaczników dokowania:

- Kolor. Na przykład można zastąpić niebieski kolor znaczników na rysunku dowolnym kolorem zdefiniowanym przez użytkownika.

- Kolor przezroczystości.

- Odsunięcie inteligentnego znacznika dokowania w grupie centralnej od granicy prostokąta ograniczającego.

- Główna mapa bitowa reprezentująca grupę centralną.

- Mapy bitowe reprezentujące regularne i wyróżnione inteligentne znaczniki dokowania.

Na poniższej ilustracji przedstawiono przykład inteligentnych znaczników dokowania, które zostały dostosowane:

![Niestandardowe znaczniki inteligentnego dokowania](../../mfc/reference/media/nextsdmarkerscustom.png "Niestandardowe znaczniki inteligentnego dokowania")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDockingInfo::CopyTo

Kopiuje bieżące parametry inteligentnego dokowania do dostarczonego obiektu [CSmartDockingInfo.](../../mfc/reference/csmartdockinginfo-class.md)

```cpp
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[na zewnątrz] Obiekt typu, `CSmartDockingInfo` który jest wypełniany bieżącymi parametrami inteligentnego dokowania.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDockingInfo::m_bUseThemeColorInShading

Określa, czy bieżący kolor motywu ma być używany, gdy w ramach wyświetlane są inteligentne znaczniki dokowania.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Uwagi

Jeśli prawda, znaczniki są rysowane przy użyciu bieżącego koloru motywu; w przeciwnym razie znaczniki są rysowane w kolorze jasnoniebieskim.

Wartością domyślną jest FAŁSZ.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDockingInfo::m_clrBaseBackground

Określa podstawowy kolor tła znaczników inteligentnego dokowania.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDockingInfo::m_clrToneDest

Określa kolor, który `m_clrToneSrc` zastąpi w mapach bitowych znacznika inteligentnego dokowania.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Uwagi

Ustaw tę wartość, aby programowo zmieniać kolor znaczników bitmap. Na przykład, jeśli chcesz zmienić kolor standardowych znaczników dostarczonych z platformą, ustaw tę wartość na żądany kolor. Domyślnie [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) jest ustawiona na RGB (61, 123, 241) (niebieskawy kolor).

Aby zmienić kolor znaczników niestandardowych, `m_clrToneDest` `m_clrToneSrc`należy określić zarówno i .

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDockingInfo::m_clrToneSrc

Określa kolor map bitowych znaczników inteligentnego dokowania.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Uwagi

Tę wartość należy ustawiać tylko wtedy, gdy chcesz zastąpić kolor niestandardowej mapy bitowej innym kolorem. Nie trzeba ustawiać tej wartości, jeśli zmieniasz kolor standardowego znacznika (pod warunkiem framework).

Służy `(COLORREF)-1` do pozostawienia członka inteligentnej grupy dokowania pustego.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDockingInfo::m_clrTransparent

Określa kolor map bitowych znaczników inteligentnego dokowania, gdy są przezroczyste.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Uwagi

Tę wartość należy ustawić podczas wyświetlania niestandardowych znaczników i niestandardowych map bitowych w grupie dokowania.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDockingInfo::m_nCentralGroupOffset

Określa przesunięcie między centralną grupą znaczników inteligentnego dokowania a obwiedniami prostokąta grupy centralnej.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Uwagi

Określ tę wartość, jeśli chcesz zmienić domyślne przesunięcie między znacznikami niestandardowymi a granicami centralnej grupy znaczników inteligentnego dokowania. Domyślne przesunięcie wynosi 5 pikseli.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDockingInfo::m_sizeTotal

Określa całkowity rozmiar prostokąta ograniczającego, który otacza wszystkie inteligentne znaczniki dokowania w grupie centralnej.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Uwagi

Ustaw `m_sizeTotal` rozmiar prostokąta ograniczającego znacznika grupy centralnej. Jest wymagane określenie tej wartości, jeśli używasz niestandardowych map bitowych dla znaczników.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDockingInfo::m_uiMarkerBmpResID

Definiuje identyfikatory zasobów map bitowych, które są używane dla niepodświetlonych niestandardowych znaczników inteligentnego dokowania.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Uwagi

Wypełnij tę tablicę identyfikatorami zasobów map bitowych reprezentujących inteligentne znaczniki dokowania. AFX_SD_MARKERS_NUM jest obecnie zdefiniowany jako 5. Tablicę wypełniasz w następujący sposób:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDockingInfo::m_uiMarkerLightBmpResID

Definiuje identyfikatory zasobów map bitowych, które są używane dla wyróżnionych niestandardowych znaczników inteligentnego dokowania.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Uwagi

Wypełnij tę tablicę identyfikatorami zasobów map bitowych reprezentujących wyróżnione znaczniki inteligentnego dokowania. AFX_SD_MARKERS_NUM jest obecnie zdefiniowany jako 5. Tablicę wypełniasz w następujący sposób:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
