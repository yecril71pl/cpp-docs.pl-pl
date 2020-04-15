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
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369067"
---
# <a name="cd2dsizef-class"></a>Klasa CD2DSizeF

Opakowanie do D2D1_SIZE_F.

## <a name="syntax"></a>Składnia

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Przeciążone. Konstruuje `CD2DSizeF` obiekt `D2D1_SIZE_F` z obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF::Isnull](#isnull)|Zwraca wartość **logiczną,** która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|`CD2DSizeF` Konwertuje `CSize` na obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_SIZE_F`

[Płyta CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

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

*Rozmiar*<br/>
rozmiar źródła

*Cx*<br/>
szerokość źródła

*Cy*<br/>
wysokość źródła

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::Isnull

Zwraca wartość logiczną, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli szerokość i wysokość są puste; w przeciwnym razie FALSE.

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::operator CSize

Konwertuje obiekt CD2DSizeF na obiekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
