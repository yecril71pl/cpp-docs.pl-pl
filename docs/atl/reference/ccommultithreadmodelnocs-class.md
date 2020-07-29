---
title: Klasa CComMultiThreadModelNoCS
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
ms.openlocfilehash: beb5cd1e13de1a10546f28d4a7eb98e45b6e9af1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224269"
---
# <a name="ccommultithreadmodelnocs-class"></a>Klasa CComMultiThreadModelNoCS

`CComMultiThreadModelNoCS`zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania wartości zmiennej bez krytycznego blokowania lub odblokowywania sekcji.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS:: CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection` .|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy `CComMultiThreadModelNoCS` .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::D ecrement](#decrement)|Ruchom Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModelNoCS:: Increment](#increment)|Ruchom Zwiększa wartość określonej zmiennej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS`jest podobna do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) w tym, że zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania zmiennej. Jednak w przypadku odwoływania się do klasy sekcji krytycznej za pomocą `CComMultiThreadModelNoCS` metod, takich jak `Lock` i `Unlock` nic nie rób.

Zwykle jest używana `CComMultiThreadModelNoCS` przez `ThreadModelNoCS` **`typedef`** nazwę. **`typedef`** Jest to zdefiniowane w `CComMultiThreadModelNoCS` , `CComMultiThreadModel` i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Nazwy globalne **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) i [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) nie są odwołaniami `CComMultiThreadModelNoCS` .

Oprócz `ThreadModelNoCS` , `CComMultiThreadModelNoCS` definiuje `AutoCriticalSection` i `CriticalSection` . Te ostatnie dwie **`typedef`** nazwy odwołują się do [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), które zawierają puste metody związane z uzyskaniem i zwalnianiem sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

W przypadku używania `CComMultiThreadModelNoCS` , **`typedef`** nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ nie `CComFakeCriticalSection` zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `AutoCriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `AutoCriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz programu `AutoCriticalSection` można użyć **`typedef`** nazwy [CriticalSection](#criticalsection). `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS:: CriticalSection

W przypadku używania `CComMultiThreadModelNoCS` , **`typedef`** nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ nie `CComFakeCriticalSection` zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `CriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `CriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz programu `CriticalSection` można użyć **`typedef`** nazwy `AutoCriticalSection` . `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::D ecrement

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), która zmniejsza wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik zmniejszenia wynosi 0, `Decrement` zwraca wartość 0. Jeśli wynik zmniejszenia jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi zmniejszenia.

### <a name="remarks"></a>Uwagi

**InterlockedDecrement** uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS:: Increment

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), która zwiększa wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zwiększona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik przyrostu wynosi 0, a następnie wartość **przyrostu** zwróci wartość 0. Jeśli wynik przyrostu jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi przyrostu.

### <a name="remarks"></a>Uwagi

**InterlockedIncrement** uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

W przypadku używania `CComMultiThreadModelNoCS` , **`typedef`** nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComMultiThreadModelNoCS` .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `ThreadModelNoCS` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą, do której odwołuje się `ThreadModelNoCS` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Należy zauważyć, że definicja `ThreadModelNoCS` w programie `CComMultiThreadModelNoCS` zapewnia symetrię z `CComMultiThreadModel` i `CComSingleThreadModel` . Załóżmy na przykład, że przykładowy kod jest `CComMultiThreadModel::AutoCriticalSection` zadeklarowany w następujący sposób **`typedef`** :

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Niezależnie od klasy określonej dla `ThreadModel` (takiej jak `CComMultiThreadModelNoCS` ), `_ThreadModel` odpowiednio rozwiązuje.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
