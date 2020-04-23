---
title: Klasa CD2DBitmapBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: 8d0804c094204bc0e8ab420e20c8b6a6a35dc70a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754290"
---
# <a name="cd2dbitmapbrush-class"></a>Klasa CD2DBitmapBrush

Otoka dla ID2D1BitmapBrush.

## <a name="syntax"></a>Składnia

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Przeciążone. Konstruuje obiekt CD2DBitmapBrush z pliku.|
|[CD2DBitmapBrush::~CD2DBitmapBrush](#dtor)|Destruktor. Wywoływane, gdy obiekt pędzla mapy bitowej D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapbrush::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DBitmapbrush::Tworzenie](#create)|Tworzy pędzel CD2DBitmapBrush. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Niszczy obiekt CD2DBitmapBrush. (Zastępuje [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DBitmapBrush::Get](#get)|Zwraca interfejs ID2D1BitmapBrush|
|[CD2DBitmapbrush::GetBitmap](#getbitmap)|Pobiera źródło mapy bitowej używane przez ten pędzel do malowania|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Pobiera metodę, za pomocą której pędzel poziomo kafelki te obszary, które wykraczają poza jego mapy bitowej|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Pobiera metodę, za pomocą której pędzel pionowo kafelki te obszary, które wykraczają poza jego mapy bitowej|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Pobiera metodę interpolacji używaną, gdy mapa bitowa pędzla jest skalowana lub obracana|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Określa źródło mapy bitowej używane przez ten pędzel do malowania|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Określa sposób poziomego układania kafelków przez pędzel tych obszarów, które wykraczają poza mapę bitową|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Określa sposób pionowego układania kafelków przez pędzel tych obszarów, które wykraczają poza mapę bitową|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Określa tryb interpolacji używany podczas skalowania lub obracania mapy bitowej pędzla|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicjuje obiekt|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::operator ID2D1BitmapBrush*](#operator_id2d1bitmapbrush_star)|Zwraca interfejs ID2D1BitmapBrush|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Przechowuje wskaźnik do obiektu CD2DBitmap.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Przechowuje wskaźnik do obiektu ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Właściwości pędzla mapy bitowej.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[Cd2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush::~CD2DBitmapBrush

Destruktor. Wywoływane, gdy obiekt pędzla mapy bitowej D2D jest niszczony.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapbrush::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```cpp
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

Konstruuje obiekt CD2DBitmapBrush.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*pBitmapBrushWłaściwości*<br/>
Wskaźnik do trybów rozszerzania i trybu interpolacji pędzla mapy bitowej.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

*interfejs użytkownika uiResID*<br/>
Numer identyfikatora zasobu.

*lpszType (typ)*<br/>
Wskaźnik do ciągu zakończonego z wartością null, który zawiera typ zasobu.

*rozmiarDest*<br/>
Rozmiar docelowy mapy bitowej.

*lpszImagePath (Ścieżka lpszImagePath)*<br/>
Wskaźnik do ciągu zakończonego wartością null, który zawiera nazwę pliku.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit

Inicjuje obiekt

```cpp
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parametry

*pBitmapBrushWłaściwości*<br/>
Wskaźnik do właściwości pędzla mapy bitowej.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapbrush::Tworzenie

Tworzy pędzel CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy

Niszczy obiekt CD2DBitmapBrush.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Get

Zwraca interfejs ID2D1BitmapBrush

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapbrush::GetBitmap

Pobiera źródło mapy bitowej używane przez ten pędzel do malowania

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu CD2DBitmap lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX

Pobiera metodę, za pomocą której pędzel poziomo kafelki te obszary, które wykraczają poza jego mapy bitowej

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość określająca sposób, w jaki pędzel jest poziomo kafelkami, które rozciągają się poza mapę bitową

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY

Pobiera metodę, za pomocą której pędzel pionowo kafelki te obszary, które wykraczają poza jego mapy bitowej

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość określająca sposób pionowego układania kafelków w pionie tych obszarów, które wykraczają poza mapę bitową

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode

Pobiera metodę interpolacji używaną, gdy mapa bitowa pędzla jest skalowana lub obracana

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda interpolacji używana podczas skalowania lub obracania mapy bitowej pędzla

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap

Przechowuje wskaźnik do obiektu CD2DBitmap.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

Przechowuje wskaźnik do obiektu ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

Właściwości pędzla mapy bitowej.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush*

Zwraca interfejs ID2D1BitmapBrush

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap

Określa źródło mapy bitowej używane przez ten pędzel do malowania

```cpp
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmapa*<br/>
Źródło mapy bitowej używane przez pędzel

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX

Określa sposób poziomego układania kafelków przez pędzel tych obszarów, które wykraczają poza mapę bitową

```cpp
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parametry

*extendModeX*<br/>
Wartość określająca sposób, w jaki pędzel jest poziomo kafelkami, które rozciągają się poza mapę bitową

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY

Określa sposób pionowego układania kafelków przez pędzel tych obszarów, które wykraczają poza mapę bitową

```cpp
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parametry

*extendModeY (rozszerzamodey)*<br/>
Wartość określająca sposób pionowego układania kafelków w pionie tych obszarów, które wykraczają poza mapę bitową

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode

Określa tryb interpolacji używany podczas skalowania lub obracania mapy bitowej pędzla

```cpp
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parametry

*Interpolationmode*<br/>
Tryb interpolacji używany podczas skalowania lub obracania mapy bitowej pędzla

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
