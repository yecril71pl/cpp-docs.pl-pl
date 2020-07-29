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
ms.openlocfilehash: 05ef787764045ec7e17f5cdfdb0d4611cb2ac900
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229977"
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
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection` .|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołania `CComSingleThreadModel` .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Zmniejsza wartość określonej zmiennej. Ta implementacja nie jest bezpieczna wątkowo.|
|[CComSingleThreadModel:: Increment](#increment)|Zwiększa wartość określonej zmiennej. Ta implementacja nie jest bezpieczna wątkowo.|

## <a name="remarks"></a>Uwagi

`CComSingleThreadModel`zapewnia metody zwiększania i zmniejszania wartości zmiennej. W przeciwieństwie do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)te metody nie są bezpieczne wątkowo.

Zwykle używasz `CComSingleThreadModel` jednej z dwóch **`typedef`** nazw — [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Klasa, do której odwołuje się każdy **`typedef`** , zależy od używanego modelu wątkowości, jak pokazano w poniższej tabeli:

| — klasa typedef|Jednowątkowy model|Model wątkowości apartamentu|Model wolnych wątków|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

`CComSingleThreadModel`sama sama definiuje trzy **`typedef`** nazwy. `ThreadModelNoCS`odwołania `CComSingleThreadModel` . `AutoCriticalSection`i `CriticalSection` Klasa referencyjna [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), która zapewnia puste metody związane z uzyskaniem i zwalnianiem własności sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

W przypadku używania `CComSingleThreadModel` , **`typedef`** nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ nie `CComFakeCriticalSection` zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje dla `AutoCriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `AutoCriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz programu `AutoCriticalSection` można użyć **`typedef`** nazwy [CriticalSection](#criticalsection). `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

W przypadku używania `CComSingleThreadModel` , **`typedef`** nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ nie `CComFakeCriticalSection` zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje dla `CriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `CriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz programu `CriticalSection` można użyć **`typedef`** nazwy [AutoCriticalSection](#autocriticalsection). `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::D ecrement

Ta funkcja statyczna zmniejsza wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Wynik zmniejszenia.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel:: Increment

Ta funkcja statyczna zwiększa wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zwiększona.

### <a name="return-value"></a>Wartość zwracana

Wynik przyrostu.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

W przypadku używania `CComSingleThreadModel` , **`typedef`** nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComSingleThreadModel` .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje dla `ThreadModelNoCS` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą, do której odwołuje się `ThreadModelNoCS` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
