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
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327332"
---
# <a name="ccomsinglethreadmodel-class"></a>Klasa CComSingleThreadModel

Ta klasa zawiera metody zwiększania i zmniejszania wartości zmiennej.

## <a name="syntax"></a>Składnia

```
class CComSingleThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection CComSingleThreadModel::AutoCriticalSection CComSingleThreadModel::AutoCriticalSection CCom](#autocriticalsection)|Odwołania klasa [CComFakeCriticalSekcja](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection CComSingleThreadModel::CriticalSection CComSingleThreadModel::CriticalSection CCom](#criticalsection)|Odwołania klasy `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referencje `CComSingleThreadModel`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSingleThreadModel::Dekrównik](#decrement)|Zmniejsza wartość określonej zmiennej. Ta implementacja nie jest bezpieczna dla wątków.|
|[CComSingleThreadModel::Przyrost](#increment)|Zwiększa wartość określonej zmiennej. Ta implementacja nie jest bezpieczna dla wątków.|

## <a name="remarks"></a>Uwagi

`CComSingleThreadModel`zawiera metody zwiększania i zmniejszania wartości zmiennej. W przeciwieństwie do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS,](../../atl/reference/ccommultithreadmodelnocs-class.md)metody te nie są bezpieczne dla wątków.

Zazwyczaj można użyć `CComSingleThreadModel` za pośrednictwem jednej z dwóch nazw **typedef,** albo [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Klasa, do którego odwołuje się każdy **typedef,** zależy od użytego modelu gwintowania, jak pokazano w poniższej tabeli:

| — klasa typedef|Model pojedynczych gwintów|Model gwintowania mieszkania|Bezpłatny model gwintowania|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

`CComSingleThreadModel`sama definiuje trzy nazwy **typedef.** `ThreadModelNoCS`referencje `CComSingleThreadModel`. `AutoCriticalSection`i `CriticalSection` klasy referencyjnej [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), która zapewnia puste metody związane z uzyskaniem i zwolnieniem własności sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection CComSingleThreadModel::AutoCriticalSection CComSingleThreadModel::AutoCriticalSection CCom

Podczas `CComSingleThreadModel`korzystania z , `AutoCriticalSection` **nazwa typedef** odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zapewnia sekcji krytycznej, jego metody nic nie robią.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają `AutoCriticalSection`definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `AutoCriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`programu , można użyć nazwy **typedef** [CriticalSection](#criticalsection). Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel::CriticalSection CComSingleThreadModel::CriticalSection CComSingleThreadModel::CriticalSection CCom

Podczas `CComSingleThreadModel`korzystania z , `CriticalSection` **nazwa typedef** odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zapewnia sekcji krytycznej, jego metody nic nie robią.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają `CriticalSection`definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `CriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`programu , można użyć nazwy **typedef** [AutoCriticalSection](#autocriticalsection). Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::Dekrównik

Ta funkcja statyczna zmniejsza wartość zmiennej wskazywalonej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma zostać zdymisjonowana.

### <a name="return-value"></a>Wartość zwracana

Wynik dekrementacji.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Przyrost

Ta funkcja statyczna zwiększa wartość zmiennej wskazywała na *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma być zwiększana.

### <a name="return-value"></a>Wartość zwracana

Wynik przyrostu.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Podczas `CComSingleThreadModel`korzystania z , `ThreadModelNoCS` nazwa `CComSingleThreadModel` **typedef** po prostu odwołuje się .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają `ThreadModelNoCS`definicje dla . W poniższej tabeli przedstawiono relację między klasą `ThreadModelNoCS`modelu wątkowego a klasą, do których odwołuje się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
