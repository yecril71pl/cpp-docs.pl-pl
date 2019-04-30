---
title: Klasa CD2DPathGeometry
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 8657421e67239cdeb782cffbbd42e0c50f6c0e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396356"
---
# <a name="cd2dpathgeometry-class"></a>Klasa CD2DPathGeometry

Otoka ID2D1PathGeometry.

## <a name="syntax"></a>Składnia

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Tworzy obiekt CD2DPathGeometry.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DPathGeometry::Create](#create)|Tworzy CD2DPathGeometry. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Niszczy obiekt CD2DPathGeometry. (Przesłania [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Pobiera liczbę cyfr w geometrii ścieżki.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Pobiera liczbę segmentów geometrii ścieżki.|
|[CD2DPathGeometry::Open](#open)|Pobiera ujścia geometrii, który jest używany do wypełniania geometrii ścieżki przy użyciu danych i segmentów.|
|[CD2DPathGeometry::Stream](#stream)|Kopiuje zawartość geometrii ścieżkę do określonego ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Wskaźnik do ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="attach"></a>  CD2DPathGeometry::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dpathgeometry"></a>  CD2DPathGeometry::CD2DPathGeometry

Tworzy obiekt CD2DPathGeometry.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DPathGeometry::Create

Tworzy CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DPathGeometry::Destroy

Niszczy obiekt CD2DPathGeometry.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DPathGeometry::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="getfigurecount"></a>  CD2DPathGeometry::GetFigureCount

Pobiera liczbę cyfr w geometrii ścieżki.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę cyfr w geometrii ścieżki.

##  <a name="getsegmentcount"></a>  CD2DPathGeometry::GetSegmentCount

Pobiera liczbę segmentów geometrii ścieżki.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę segmentów geometrii ścieżki.

##  <a name="m_ppathgeometry"></a>  CD2DPathGeometry::m_pPathGeometry

Wskaźnik do ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

##  <a name="open"></a>  CD2DPathGeometry::Open

Pobiera ujścia geometrii, który jest używany do wypełniania geometrii ścieżki przy użyciu danych i segmentów.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ID2D1GeometrySink, który jest używany do wypełniania geometrii ścieżki przy użyciu danych i segmentów.

##  <a name="stream"></a>  CD2DPathGeometry::Stream

Kopiuje zawartość geometrii ścieżkę do określonego ID2D1GeometrySink.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parametry

*geometrySink*<br/>
Obiekt sink, do której są kopiowane geometrii ścieżki zawartości. Modyfikowanie tego obiektu sink nie zmienia się zawartość geometrii tej ścieżki.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
