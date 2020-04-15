---
title: Klasa CD2DMesh
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: 64f5dd7b40853a86dc7f964ecd3701f132a94e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369182"
---
# <a name="cd2dmesh-class"></a>Klasa CD2DMesh

Otoka dla ID2D1Mesh.

## <a name="syntax"></a>Składnia

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Konstruuje obiekt CD2DMesh.|
|[CD2DMesh:~CD2DMesh](#_dtorcd2dmesh)|Destruktor. Wywoływana, gdy obiekt siatki D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DMesh::Tworzenie](#create)|Tworzy plik CD2DMesh. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Niszczy obiekt CD2DMesh. (Zastępuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DMesh::Pobierz](#get)|Zwraca interfejs ID2D1Mesh|
|[CD2DMesh::IsValid](#isvalid)|Sprawdza ważność zasobu (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Otwórz](#open)|Otwiera siatkę dla populacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::operator ID2D1Mesh*](#operator_id2d1mesh_star)|Zwraca interfejs ID2D1Mesh|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Wskaźnik do ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2DMesh:~CD2DMesh

Destruktor. Wywoływana, gdy obiekt siatki D2D jest niszczony.

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2DMesh::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2DMesh::CD2DMesh

Konstruuje obiekt CD2DMesh.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2DMesh::Tworzenie

Tworzy plik CD2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh::Destroy

Niszczy obiekt CD2DMesh.

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dmeshget"></a><a name="get"></a>CD2DMesh::Pobierz

Zwraca interfejs ID2D1Mesh

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Mesh lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh::IsValid

Sprawdza ważność zasobu

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh::m_pMesh

Wskaźnik do ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2DMesh::Otwórz

Otwiera siatkę dla populacji.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do identyfikatora ID2D1TesselationSink używany do wypełniania siatki.

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2DMesh::operator ID2D1Mesh*

Zwraca interfejs ID2D1Mesh

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Mesh lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
