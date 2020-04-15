---
title: CDefaultHashTraits Klasa
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327085"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits Klasa

Ta klasa zapewnia funkcję statyczną do obliczania wartości skrótu.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statyczne) Wywołanie tej funkcji, aby obliczyć wartość mieszania dla danego elementu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera pojedynczą funkcję statyczną, która zwraca wartość mieszania dla danego elementu. Ta klasa jest wykorzystywana przez [CDefaultElementTraits Klasy](../../atl/reference/cdefaultelementtraits-class.md).

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash

Wywołanie tej funkcji, aby obliczyć wartość mieszania dla danego elementu.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Element.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość mieszania.

### <a name="remarks"></a>Uwagi

Domyślny algorytm mieszania jest bardzo prosty: zwracana wartość jest liczbą elementu. Zastąd w tej funkcji, jeśli wymagany jest bardziej skomplikowany algorytm.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
