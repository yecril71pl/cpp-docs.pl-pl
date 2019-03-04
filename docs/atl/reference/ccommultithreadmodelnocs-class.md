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
ms.openlocfilehash: 9b1622525635a4ea852dec9095fcd479b21044c4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261560"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS Class

`CComMultiThreadModelNoCS` udostępnia metody wątkowo zwiększanie i zmniejszanie wartości zmiennej, bez sekcję krytyczną blokowanie lub odblokowywanie funkcji.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection`.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statyczny) Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statyczny) Zwiększa wartość zmiennej określonej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS` jest podobny do [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) , zapewnia metody obsługujące wielowątkowość zwiększanie i zmniejszanie zmienną. Jednak gdy odwołujesz się klasy sekcję krytyczną, za pośrednictwem `CComMultiThreadModelNoCS`, metody takie jak `Lock` i `Unlock` nic nie rób.

Zazwyczaj można użyć `CComMultiThreadModelNoCS` za pośrednictwem `ThreadModelNoCS` **typedef** nazwy. To **typedef** jest zdefiniowany w `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Globalna **typedef** nazwy [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) i [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) nie odwołują się do `CComMultiThreadModelNoCS`.

Oprócz `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definiuje `AutoCriticalSection` i `CriticalSection`. Tych dwóch **typedef** nazwy odwołania [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), która zapewnia metody pusty związanych z uzyskaniem i zwalniania sekcję krytyczną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Korzystając z `CComMultiThreadModelNoCS`, **typedef** nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcję krytyczną, nic nie rób jej metody.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `AutoCriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`, możesz użyć **typedef** nazwa [CriticalSection](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

See [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

Korzystając z `CComMultiThreadModelNoCS`, **typedef** nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

Ponieważ `CComFakeCriticalSection` nie zawiera sekcję krytyczną, nic nie rób jej metody.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `CriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`, możesz użyć **typedef** nazwa `AutoCriticalSection`. Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

See [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement), która zmniejsza wartość zmiennej wskazywany przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej do zmniejszenia.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik dekrementacji wynosi 0, to `Decrement` zwraca wartość 0. Wynik dekrementacji jest różna od zera, wartość zwracana, również jest różna od zera, ale nie może mieć wartość równą wynik dekrementacji.

### <a name="remarks"></a>Uwagi

**InterlockedDecrement** zapobiega więcej niż jeden wątek jednocześnie przy użyciu tej zmiennej.

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement), która zwiększa wartość zmiennej, do których prowadzą *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej, aby być zwiększony.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik przyrost wynosi 0, to **przyrostu** zwraca wartość 0. Wynik przyrost jest różna od zera, wartość zwracana jest również wartość różną od zera, ale nie może mieć wartość równą wartości przyrostu.

### <a name="remarks"></a>Uwagi

**InterlockedIncrement** zapobiega więcej niż jeden wątek jednocześnie przy użyciu tej zmiennej.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

Korzystając z `CComMultiThreadModelNoCS`, **typedef** nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComMultiThreadModelNoCS`.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Należy pamiętać, że definicja `ThreadModelNoCS` w `CComMultiThreadModelNoCS` zapewnia symetrię z `CComMultiThreadModel` i `CComSingleThreadModel`. Załóżmy na przykład, kod przykładowy w `CComMultiThreadModel::AutoCriticalSection` zadeklarowana następujące **typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Niezależnie od tego, klasa określona dla `ThreadModel` (takie jak `CComMultiThreadModelNoCS`), `_ThreadModel` rozpoznaje odpowiednio.

### <a name="example"></a>Przykład

See [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
