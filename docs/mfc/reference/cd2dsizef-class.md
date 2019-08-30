---
title: Klasa CD2DSizeF
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177200"
---
# <a name="cd2dsizef-class"></a>Klasa CD2DSizeF

Otoka dla D2D1_SIZE_F.

## <a name="syntax"></a>Składnia

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Przeciążone. Konstruuje `D2D1_SIZE_F` obiekt z obiektu. `CD2DSizeF`|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF:: IsNull](#isnull)|Zwraca wartość **logiczną** wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF:: operator CSize](#operator_csize)|Konwertuje `CD2DSizeF` na`CSize` obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget. h

##  <a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

Konstruuje obiekt CD2DSizeF z obiektu CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
rozmiar źródła

*cx*<br/>
Szerokość źródła

*cy*<br/>
wysokość źródła

##  <a name="isnull"></a>CD2DSizeF:: IsNull

Zwraca wartość logiczną wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli szerokość i wysokość są puste; w przeciwnym razie FALSE.

##  <a name="operator_csize"></a>CD2DSizeF:: operator CSize

Konwertuje CD2DSizeF na obiekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
