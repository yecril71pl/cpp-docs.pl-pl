---
title: Klasa CComMultiThreadModel
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 38ed43e77492484b7c8d8cb06cad71e695d41c4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224282"
---
# <a name="ccommultithreadmodel-class"></a>Klasa CComMultiThreadModel

`CComMultiThreadModel`zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania wartości zmiennej.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel:: CriticalSection](#criticalsection)|Odwołuje się do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::D ecrement](#decrement)|Ruchom Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModel:: Increment](#increment)|Ruchom Zwiększa wartość określonej zmiennej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

Zwykle używasz `CComMultiThreadModel` jednej z dwóch **`typedef`** nazw: [CComObjectThreadModel] (ATL-Typedefs. MD # CComObjectThreadModel lub [CComGlobalsThreadModel] (ATL-Typedefs. MD # CComGlobalsThreadModel. Klasa, do której odwołuje się każdy **`typedef`** , zależy od używanego modelu wątkowości, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze wątki|Wątkowość apartamentu|Bezpłatna wątkowość|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

`CComMultiThreadModel`sama sama definiuje trzy **`typedef`** nazwy. `AutoCriticalSection`i `CriticalSection` klasy referencyjne, które udostępniają metody uzyskiwania i zwalniania własności sekcji krytycznej. `ThreadModelNoCS`References — Klasa [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

W przypadku użycia `CComMultiThreadModel` , **`typedef`** nazwa `AutoCriticalSection` odwołuje się do klasy [CComAutoCriticalSection](ccomautocriticalsection-class.md), która zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) zawierają również definicje dla `AutoCriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `AutoCriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz programu `AutoCriticalSection` można użyć **`typedef`** nazwy [CriticalSection](#criticalsection). `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Poniższy kod jest modelowany po [CComObjectRootEx](ccomobjectrootex-class.md)i demonstruje `AutoCriticalSection` użycie w środowisku wątkowości.

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

W poniższych tabelach przedstawiono wyniki `InternalAddRef` metod i, w `Lock` zależności od `ThreadModel` parametru szablonu i modelu wątkowości używanego przez aplikację:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Wątki pojedyncze lub Apartment|Bezpłatna wątkowość|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest bezpieczny dla wątków.|Przyrost jest bezpieczny dla wątków.|
|`Lock`|Nic nie robi; Brak sekcji krytycznej do zablokowania.|Sekcja krytyczna jest zablokowana.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel:: ThreadModelNoCS

|Metoda|Wątki pojedyncze lub Apartment|Bezpłatna wątkowość|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest bezpieczny dla wątków.|Przyrost jest bezpieczny dla wątków.|
|`Lock`|Nic nie robi; Brak sekcji krytycznej do zablokowania.|Nic nie robi; Brak sekcji krytycznej do zablokowania.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel:: CriticalSection

W przypadku użycia `CComMultiThreadModel` , **`typedef`** nazwa `CriticalSection` odwołuje się do klasy [CComCriticalSection](ccomcriticalsection-class.md), która zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) zawierają również definicje dla `CriticalSection` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą sekcji krytycznej, do której odwołuje się `CriticalSection` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz programu `CriticalSection` można użyć **`typedef`** nazwy [AutoCriticalSection](#autocriticalsection). `AutoCriticalSection`Jeśli chcesz wyeliminować kod uruchomienia CRT, nie należy określać w obiektach globalnych ani statycznych składowych klas.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::D ecrement

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), która zmniejsza wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik zmniejszenia wynosi 0, `Decrement` zwraca wartość 0. Jeśli wynik zmniejszenia jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi zmniejszenia.

### <a name="remarks"></a>Uwagi

`InterlockedDecrement`uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel:: Increment

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), która zwiększa wartość zmiennej wskazywanej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do zmiennej, która ma zostać zwiększona.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik przyrostu wynosi 0, a następnie `Increment` zwraca wartość 0. Jeśli wynik przyrostu jest różny od zera, wartość zwracana jest również różna od zera, ale nie może być równa wynikowi przyrostu.

### <a name="remarks"></a>Uwagi

`InterlockedIncrement`uniemożliwia jednoczesne użycie więcej niż jednego wątku przy użyciu tej zmiennej.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

W przypadku używania `CComMultiThreadModel` , **`typedef`** nazwa `ThreadModelNoCS` odwołuje się do klasy [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS`zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania zmiennej; jednak nie zawiera sekcji krytycznej.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) , a `CComMultiThreadModelNoCS` także zawierają definicje dla `ThreadModelNoCS` . W poniższej tabeli przedstawiono relacje między klasą modelu wątkowego i klasą, do której odwołuje się `ThreadModelNoCS` :

|Klasa zdefiniowana w|Klasa, do której istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Zobacz także

[Klasa CComSingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Klasa CComAutoCriticalSection](ccomautocriticalsection-class.md)<br/>
[Klasa CComCriticalSection](ccomcriticalsection-class.md)<br/>
[Przegląd klas](../atl-class-overview.md)
