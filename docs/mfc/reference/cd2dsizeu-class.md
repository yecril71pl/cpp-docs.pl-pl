---
title: Klasa CD2DSizeU
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359293"
---
# <a name="cd2dsizeu-class"></a>Klasa CD2DSizeU

Opakowanie do D2D1_SIZE_U.

## <a name="syntax"></a>Składnia

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Przeciążone. Konstruuje `CD2DSizeU` obiekt `D2D1_SIZE_U` z obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeu::Isnull](#isnull)|Zwraca wartość **logiczną,** która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|`CD2DSizeU` Konwertuje `CSize` na obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

Konstruuje obiekt CD2DSizeU z obiektu CSize.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
rozmiar źródła

*Cx*<br/>
szerokość źródła

*Cy*<br/>
wysokość źródła

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeu::Isnull

Zwraca wartość logiczną, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli szerokość i wysokość są puste; w przeciwnym razie FALSE.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU::operator CSize

Konwertuje CD2DSizeU do obiektu CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
