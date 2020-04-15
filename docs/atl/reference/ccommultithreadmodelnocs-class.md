---
title: Klasa CComMultiThreadNodelNoCS
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327652"
---
# <a name="ccommultithreadmodelnocs-class"></a>Klasa CComMultiThreadNodelNoCS

`CComMultiThreadModelNoCS`zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania wartości zmiennej, bez funkcji blokowania sekcji krytycznej lub odblokowywania.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odwołania klasa [CComFakeCriticalSekcja](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection CComMultiThreadNoCS::CriticalSection CComMultiThreadNoCS::CriticalSection CComMultiThread](#criticalsection)|Odwołania klasy `CComFakeCriticalSection`.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odwołania klasy `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Dekrównik](#decrement)|(Statyczne) Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModelNoCS::Przyrost](#increment)|(Statyczne) Zwiększa wartość określonej zmiennej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS`jest podobny do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) w tym, że zapewnia metody wątku bezpieczne dla zwiększania i zmniejszania zmiennej. Jednak po odwołaniu się do `CComMultiThreadModelNoCS`klasy sekcji `Lock` `Unlock` krytycznej za pośrednictwem , metody takie jak i nic nie zrobi.

Zazwyczaj używasz `CComMultiThreadModelNoCS` za `ThreadModelNoCS` pomocą **nazwy typedef.** Ten **typedef** jest `CComMultiThreadModelNoCS` `CComMultiThreadModel`zdefiniowany w programach , i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Globalne nazwy **typedef** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) i [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) nie odwołują się do `CComMultiThreadModelNoCS`.

Oprócz `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definiuje `AutoCriticalSection` i `CriticalSection`. Te ostatnie dwa **typedef** nazwy odwołania [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), który zapewnia puste metody związane z uzyskaniem i zwolnieniem sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

Podczas `CComMultiThreadModelNoCS`korzystania z , `AutoCriticalSection` **nazwa typedef** odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zapewnia sekcji krytycznej, jego metody nic nie robią.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają `AutoCriticalSection`również definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `AutoCriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`programu , można użyć nazwy **typedef** [CriticalSection](#criticalsection). Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection CComMultiThreadNoCS::CriticalSection CComMultiThreadNoCS::CriticalSection CComMultiThread

Podczas `CComMultiThreadModelNoCS`korzystania z , `CriticalSection` **nazwa typedef** odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zapewnia sekcji krytycznej, jego metody nic nie robią.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają `CriticalSection`również definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `CriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`programu , można użyć nazwy `AutoCriticalSection` **typedef** . Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Dekrównik

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), która zmniejsza wartość zmiennej wskazywalnej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma zostać zdymisjonowana.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik dekrementacji wynosi 0, zwraca wartość `Decrement` 0. Jeśli wynik dekrementacji jest niezerowy, zwracana wartość jest również niezerowa, ale może nie być równa wyniku dekrementacji.

### <a name="remarks"></a>Uwagi

**InterlockedDecrement** uniemożliwia jednoczesne użycie tej zmiennej więcej niż jednego wątku.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Przyrost

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), która zwiększa wartość zmiennej wskazywalnej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma być zwiększana.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynikiem przyrostu jest 0, a następnie **przyrost** zwraca 0. Jeśli wynik przyrostu jest niezerowy, zwracana wartość jest również niezerowa, ale może nie być równa wyniku przyrostu.

### <a name="remarks"></a>Uwagi

**InterlockedIncrement** uniemożliwia jednoczesne użycie tej zmiennej więcej niż jednego wątku.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Podczas `CComMultiThreadModelNoCS`korzystania z , `ThreadModelNoCS` nazwa `CComMultiThreadModelNoCS` **typedef** po prostu odwołuje się .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają `ThreadModelNoCS`również definicje dla . W poniższej tabeli przedstawiono relację między klasą `ThreadModelNoCS`modelu wątkowego a klasą, do których odwołuje się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Należy zauważyć, `ThreadModelNoCS` że `CComMultiThreadModelNoCS` definicja w `CComMultiThreadModel` `CComSingleThreadModel`zapewnia symetrię z i . Załóżmy na przykład `CComMultiThreadModel::AutoCriticalSection` przykładowy kod w zadeklarowanym: **typedef**

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Niezależnie od klasy określonej dla `CComMultiThreadModelNoCS` `_ThreadModel` (takich `ThreadModel` jak ), rozwiązuje odpowiednio.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
