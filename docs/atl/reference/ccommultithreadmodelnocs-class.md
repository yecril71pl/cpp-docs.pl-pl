---
title: CComMultiThreadModelNoCS Class
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
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497086"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS Class

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
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odwołuje `CComFakeCriticalSection`się do klasy.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odwołuje `CComMultiThreadModelNoCS`się do klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|Ruchom Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModelNoCS::Increment](#increment)|Ruchom Zwiększa wartość określonej zmiennej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS`jest podobna do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) w tym, że zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania zmiennej. Jednak w przypadku odwoływania się do klasy sekcji krytycznej za pomocą `CComMultiThreadModelNoCS`metod, takich jak `Lock` i `Unlock` nic nie rób.

Zwykle używany `CComMultiThreadModelNoCS` `ThreadModelNoCS` przez nazwę **typedef** . Ten **element typedef** jest zdefiniowany `CComMultiThreadModelNoCS`w `CComMultiThreadModel`, i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Nazwy globalnych **typedef** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) i [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) nie są odwołaniami `CComMultiThreadModelNoCS`.

Oprócz `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definiuje i`AutoCriticalSection` . `CriticalSection` Te ostatnie dwa nazwy **typedef** zawierają odwołania [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), które udostępniają puste metody skojarzone z uzyskaniem i wydawaniem sekcji krytycznej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

W przypadku `CComMultiThreadModelNoCS`używania, nazwa `AutoCriticalSection` typedef odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `AutoCriticalSection`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do `AutoCriticalSection`której odwołuje się:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`, można użyć nazwy **typedef** [CriticalSection](#criticalsection). Jeśli chcesz wyeliminować kod `AutoCriticalSection` uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComMultiThreadModelNoCS:: CriticalSection

W przypadku `CComMultiThreadModelNoCS`używania, nazwa `CriticalSection` typedef odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcji krytycznej, jej metody nic nie rób.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `CriticalSection`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do `CriticalSection`której odwołuje się:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`, można użyć nazwy `AutoCriticalSection` **typedef** . Jeśli chcesz wyeliminować kod `AutoCriticalSection` uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComMultiThreadModelNoCS::D ecrement

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), która zmniejsza wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik zmniejszenia wynosi 0, `Decrement` zwraca wartość 0. Jeśli wynik zmniejszenia jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi zmniejszenia.

### <a name="remarks"></a>Uwagi

**InterlockedDecrement** uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

##  <a name="increment"></a>CComMultiThreadModelNoCS:: Increment

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), która zwiększa wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zwiększona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik przyrostu wynosi 0, a następnie wartość **przyrostu** zwróci wartość 0. Jeśli wynik przyrostu jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi przyrostu.

### <a name="remarks"></a>Uwagi

**InterlockedIncrement** uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

##  <a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

W przypadku `CComMultiThreadModelNoCS`używania, nazwa `ThreadModelNoCS` typedef jest po `CComMultiThreadModelNoCS`prostu odwołuje się do.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) zawierają również definicje dla `ThreadModelNoCS`. W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą, do której `ThreadModelNoCS`odwołuje się:

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Należy zauważyć, że definicja `ThreadModelNoCS` w `CComMultiThreadModelNoCS` programie zapewnia symetrię `CComSingleThreadModel`z `CComMultiThreadModel` i. Załóżmy na przykład, że przykładowy kod w `CComMultiThreadModel::AutoCriticalSection` zadeklarowany jest następujący **element typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Niezależnie od klasy określonej dla `ThreadModel` (takiej jak `CComMultiThreadModelNoCS`), `_ThreadModel` odpowiednio rozwiązuje.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
