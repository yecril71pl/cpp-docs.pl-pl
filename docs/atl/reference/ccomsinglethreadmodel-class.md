---
title: Klasa CComSingleThreadModel
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215463"
---
# <a name="ccomsinglethreadmodel-class"></a>Klasa CComSingleThreadModel

Ta klasa zapewnia metody zwiększania i zmniejszania wartości zmiennej.

## <a name="syntax"></a>Składnia

```
class CComSingleThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|Odwołuje się `CComFakeCriticalSection`klasy.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się `CComSingleThreadModel`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Zmniejsza wartość określonej zmiennej. Ta implementacja nie jest bezpieczna wątkowo.|
|[CComSingleThreadModel:: Increment](#increment)|Zwiększa wartość określonej zmiennej. Ta implementacja nie jest bezpieczna wątkowo.|

## <a name="remarks"></a>Uwagi

`CComSingleThreadModel` zapewnia metody zwiększania i zmniejszania wartości zmiennej. W przeciwieństwie do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)te metody nie są bezpieczne wątkowo.

Zazwyczaj używa się `CComSingleThreadModel` do jednego z dwóch nazw **typedef** , [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Klasa, do której odwołuje się każdy **element typedef** , zależy od używanego modelu wątkowości, jak pokazano w poniższej tabeli:

|— klasa typedef|Jednowątkowy model|Model wątkowości apartamentu|Model wolnych wątków|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` sam definiuje trzy nazwy **typedef** . `CComSingleThreadModel`odwołania `ThreadModelNoCS`. `AutoCriticalSection` i `CriticalSection` Klasa referencyjna [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), która zapewnia puste metody związane z uzyskaniem i zwalnianiem własności sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

W przypadku używania `CComSingleThreadModel`nazwa **typedef** `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `AutoCriticalSection`:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`można użyć nazwy **typedef** [CriticalSection](#criticalsection). Nie należy określać `AutoCriticalSection` w obiektach globalnych ani statycznych składowych klas, jeśli chcesz wyeliminować kod uruchomienia CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

W przypadku używania `CComSingleThreadModel`nazwa **typedef** `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `CriticalSection`:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`można użyć nazwy **typedef** [AutoCriticalSection](#autocriticalsection). Nie należy określać `AutoCriticalSection` w obiektach globalnych ani statycznych składowych klas, jeśli chcesz wyeliminować kod uruchomienia CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComSingleThreadModel::D ecrement

Ta funkcja statyczna zmniejsza wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zmniejszona.

### <a name="return-value"></a>Wartość zwrócona

Wynik zmniejszenia.

##  <a name="increment"></a>CComSingleThreadModel:: Increment

Ta funkcja statyczna zwiększa wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zwiększona.

### <a name="return-value"></a>Wartość zwrócona

Wynik przyrostu.

##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

W przypadku używania `CComSingleThreadModel`nazwa **typedef** `ThreadModelNoCS` po prostu odwołuje się do `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą, do której odwołuje się `ThreadModelNoCS`:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
