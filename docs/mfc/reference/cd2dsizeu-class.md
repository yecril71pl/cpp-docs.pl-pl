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
ms.openlocfilehash: 45625331d0c1be8ca7c663d12c53516dc7bd77c7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177185"
---
# <a name="cd2dsizeu-class"></a>Klasa CD2DSizeU

Otoka dla D2D1_SIZE_U.

## <a name="syntax"></a>Składnia

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Przeciążone. Konstruuje `D2D1_SIZE_U` obiekt z obiektu. `CD2DSizeU`|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeU:: IsNull](#isnull)|Zwraca wartość **logiczną** wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeU:: operator CSize](#operator_csize)|Konwertuje `CD2DSizeU` na`CSize` obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget. h

##  <a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

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

*zmienia*<br/>
rozmiar źródła

*cx*<br/>
Szerokość źródła

*cy*<br/>
wysokość źródła

##  <a name="isnull"></a>CD2DSizeU:: IsNull

Zwraca wartość logiczną wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli szerokość i wysokość są puste; w przeciwnym razie FALSE.

##  <a name="operator_csize"></a>CD2DSizeU:: operator CSize

Konwertuje CD2DSizeU na obiekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
