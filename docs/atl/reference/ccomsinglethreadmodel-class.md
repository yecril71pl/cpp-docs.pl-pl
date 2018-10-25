---
title: Klasa CComSingleThreadModel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 2a20a5c8ad87428e66f90b8f04c3006e5f1c2e84
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068875"
---
# <a name="ccomsinglethreadmodel-class"></a>Klasa CComSingleThreadModel

Ta klasa zawiera metody służące do zwiększanie i zmniejszanie, wartość zmiennej.

## <a name="syntax"></a>Składnia

```
class CComSingleThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołania `CComSingleThreadModel`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Zmniejsza wartość określonej zmiennej. Ta implementacja nie jest metodą o bezpiecznych wątkach.|
|[CComSingleThreadModel::Increment](#increment)|Zwiększa wartość określonej zmiennej. Ta implementacja nie jest metodą o bezpiecznych wątkach.|

## <a name="remarks"></a>Uwagi

`CComSingleThreadModel` udostępnia metody zwiększanie i zmniejszanie wartości zmiennej. W odróżnieniu od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), te metody nie są wątkowo.

Zazwyczaj można użyć `CComSingleThreadModel` za pomocą jednego z dwóch **typedef** nazwy albo [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Klasa przywoływana przez każdą **typedef** zależy od modelu wątkowości używane, jak pokazano w poniższej tabeli:

|— klasa typedef|Pojedynczy model wątkowości|Model wątkowości typu apartment|Model wątkowości bezpłatnie|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` sam definiuje trzy **typedef** nazwy. `ThreadModelNoCS` odwołania `CComSingleThreadModel`. `AutoCriticalSection` i `CriticalSection` reference — klasa [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), która zapewnia metody pusty związanych z uzyskaniem i zwalniania własności sekcję krytyczną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection

Korzystając z `CComSingleThreadModel`, **typedef** nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcję krytyczną, nic nie rób jej metody.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `AutoCriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`, możesz użyć **typedef** nazwa [CriticalSection](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection

Korzystając z `CComSingleThreadModel`, **typedef** nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcję krytyczną, nic nie rób jej metody.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `CriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`, możesz użyć **typedef** nazwa [AutoCriticalSection](#autocriticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComSingleThreadModel::Decrement

Zmniejsza to funkcję statyczną wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej do zmniejszenia.

### <a name="return-value"></a>Wartość zwracana

Wynik dekrementacji.

##  <a name="increment"></a>  CComSingleThreadModel::Increment

Zmniejsza to funkcję statyczną wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej, aby być zwiększony.

### <a name="return-value"></a>Wartość zwracana

Wynik przyrostu.

##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS

Korzystając z `CComSingleThreadModel`, **typedef** nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
