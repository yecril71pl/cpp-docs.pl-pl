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
ms.openlocfilehash: 1cc1769f66b54f2a9a23ef9ad94298687fe4d925
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445646"
---
# <a name="cd2dmesh-class"></a>Klasa CD2DMesh

Otoka ID2D1Mesh.

## <a name="syntax"></a>Składnia

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Tworzy obiekt CD2DMesh.|
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt siatki D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DMesh::Create](#create)|Tworzy CD2DMesh. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Niszczy obiekt CD2DMesh. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DMesh::Get](#get)|Zwraca ID2D1Mesh interfejsu|
|[CD2DMesh::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Open](#open)|Zostanie otwarty siatki dla populacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|Zwraca ID2D1Mesh interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Wskaźnik do ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dmesh"></a>  CD2DMesh:: ~ CD2DMesh

Destruktor. Wywołuje się, kiedy niszczony jest obiekt siatki D2D.

```
virtual ~CD2DMesh();
```

##  <a name="attach"></a>  CD2DMesh::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dmesh"></a>  CD2DMesh::CD2DMesh

Tworzy obiekt CD2DMesh.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DMesh::Create

Tworzy CD2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DMesh::Destroy

Niszczy obiekt CD2DMesh.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DMesh::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DMesh::Get

Zwraca ID2D1Mesh interfejsu

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Mesh lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="isvalid"></a>  CD2DMesh::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_pmesh"></a>  CD2DMesh::m_pMesh

Wskaźnik do ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

##  <a name="open"></a>  CD2DMesh::Open

Zostanie otwarty siatki dla populacji.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ID2D1TessellationSink, który jest używany do wypełniania siatkę.

##  <a name="operator_id2d1mesh_star"></a>  CD2DMesh::operator ID2D1Mesh *

Zwraca ID2D1Mesh interfejsu

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Mesh lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
