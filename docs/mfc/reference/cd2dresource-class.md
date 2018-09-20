---
title: Klasa CD2DResource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
dev_langs:
- C++
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2ee4f7f5f1e3e6126cee6e5822468a7487eb1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442269"
---
# <a name="cd2dresource-class"></a>Klasa CD2DResource

Abstrakcyjna klasa, która udostępnia interfejs do tworzenia i zarządzania zasobami D2D, takimi jak pędzle, warstwy i teksty.

## <a name="syntax"></a>Składnia

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Tworzy obiekt CD2DResource.|
|[CD2DResource:: ~ CD2DResource](#cd2dresource__~cd2dresource)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt zasobów D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DResource::Create](#create)|Tworzy CD2DResource.|
|[CD2DResource::Destroy](#destroy)|Niszczy obiekt CD2DResource.|
|[CD2DResource::IsValid](#isvalid)|Sprawdzanie zasobów ważności|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Automatycznego wyboru zniszczyć flagi.|
|[CD2DResource::ReCreate](#recreate)|Ponownie tworzy CD2DResource.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Zasób zostanie destoyed przez właściciela (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Wskaźnik do elementu nadrzędnego CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  CD2DResource:: ~ CD2DResource

Destruktor. Wywołuje się, kiedy niszczony jest obiekt zasobów D2D.

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

Tworzy obiekt CD2DResource.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DResource::Create

Tworzy CD2DResource.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DResource::Destroy

Niszczy obiekt CD2DResource.

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

Automatycznego wyboru zniszczyć flagi.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli obiekt jest niszczony udzielonej przez właściciela; w przeciwnym razie wartość FALSE.

##  <a name="isvalid"></a>  CD2DResource::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

Zasób zostanie destoyed przez właściciela (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

Wskaźnik do elementu nadrzędnego CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

Ponownie tworzy CD2DResource.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
