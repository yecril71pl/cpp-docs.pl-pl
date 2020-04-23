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
ms.openlocfilehash: 91460e3435130530ecc57bdcc09d1c7301333a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753080"
---
# <a name="cd2dpathgeometry-class"></a>Klasa CD2DPathGeometry

Otoka dla ID2D1PathGeometry.

## <a name="syntax"></a>Składnia

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Konstruuje obiekt CD2DPathGeometry.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DPathGeometry::Tworzenie](#create)|Tworzy CD2DPathGeometry. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Niszczy obiekt CD2DPathGeometry. (Zastępuje [CD2DGeometria::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Pobiera liczbę cyfr w geometrii ścieżki.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Pobiera liczbę segmentów w geometrii ścieżki.|
|[CD2DPathGeometry::Otwórz](#open)|Pobiera ujście geometrii, który jest używany do wypełniania geometrii ścieżki figurami i segmentami.|
|[CD2DPathGeometry::Strumień](#stream)|Kopiuje zawartość geometrii ścieżki do określonego identyfikatora ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Wskaźnik do ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometria](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPathGeometry::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry

Konstruuje obiekt CD2DPathGeometry.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPathGeometry::Tworzenie

Tworzy CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPathGeometry::Destroy

Niszczy obiekt CD2DPathGeometry.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPathGeometry::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount

Pobiera liczbę cyfr w geometrii ścieżki.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę cyfr w geometrii ścieżki.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount

Pobiera liczbę segmentów w geometrii ścieżki.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę segmentów w geometrii ścieżki.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry

Wskaźnik do ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPathGeometry::Otwórz

Pobiera ujście geometrii, który jest używany do wypełniania geometrii ścieżki figurami i segmentami.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ID2D1GeometrySink, który jest używany do wypełniania geometrii ścieżki z postaciami i segmentami.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPathGeometry::Strumień

Kopiuje zawartość geometrii ścieżki do określonego identyfikatora ID2D1GeometrySink.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parametry

*geometriaSink*<br/>
Zlew, do którego kopiowana jest zawartość geometrii ścieżki. Modyfikacja tego ujścia nie powoduje zmiany zawartości tej geometrii ścieżki.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
