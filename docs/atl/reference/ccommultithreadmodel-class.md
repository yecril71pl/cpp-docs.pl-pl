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
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327668"
---
# <a name="ccommultithreadmodel-class"></a>Klasa CComMultiThreadModel

`CComMultiThreadModel`zapewnia metody bezpieczeństwa wątków do zwiększania i zmniejszania wartości zmiennej.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSekcja](#autocriticalsection)|Odwołania klasa [CComAutoCriticalSekcja](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection CComMultiThreadModel::CriticalSection CComMultiThreadModel::CriticalSection CCom](#criticalsection)|Odwołania klasy [CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołania klasa [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::Dekrównik](#decrement)|(Statyczne) Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModel::Przyrost](#increment)|(Statyczne) Zwiększa wartość określonej zmiennej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

Zazwyczaj można użyć `CComMultiThreadModel` za pośrednictwem jednej z dwóch nazw **typedef,** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel. Klasa, do którego odwołuje się każdy **typedef,** zależy od użytego modelu gwintowania, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze gwintowanie|Gwintowanie mieszkań|Gwintowanie swobodne|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

`CComMultiThreadModel`sama definiuje trzy nazwy **typedef.** `AutoCriticalSection`i `CriticalSection` klasy referencyjne, które zapewniają metody uzyskiwania i zwalniania własności sekcji krytycznej. `ThreadModelNoCS`odwołuje się do klasy [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSekcja

Podczas `CComMultiThreadModel`korzystania z , `AutoCriticalSection` **typedef** name odwołuje się do klasy [CComAutoCriticalSection](ccomautocriticalsection-class.md), która zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) zawierają `AutoCriticalSection`również definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `AutoCriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`programu , można użyć nazwy **typedef** [CriticalSection](#criticalsection). Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Poniższy kod jest modelowany po [CComObjectRootEx](ccomobjectrootex-class.md)i demonstruje, `AutoCriticalSection` że jest używany w środowisku wątkowym.

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

W poniższych tabelach `InternalAddRef` przedstawiono wyniki `Lock` i `ThreadModel` metody, w zależności od parametru szablonu i modelu wątkowego używanego przez aplikację:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Gwintowanie pojedyncze lub mieszkalne|Darmowe wątki|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest bezpieczny dla wątków.|Przyrost jest bezpieczny dla wątków.|
|`Lock`|Nic nie robi; nie ma sekcji krytycznej do zablokowania.|Sekcja krytyczna jest zablokowana.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Metoda|Gwintowanie pojedyncze lub mieszkalne|Darmowe wątki|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest bezpieczny dla wątków.|Przyrost jest bezpieczny dla wątków.|
|`Lock`|Nic nie robi; nie ma sekcji krytycznej do zablokowania.|Nic nie robi; nie ma sekcji krytycznej do zablokowania.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel::CriticalSection CComMultiThreadModel::CriticalSection CComMultiThreadModel::CriticalSection CCom

Podczas `CComMultiThreadModel`korzystania z , `CriticalSection` **typedef** name odwołuje się do klasy [CComCriticalSection](ccomcriticalsection-class.md), która zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) zawierają `CriticalSection`również definicje dla . W poniższej tabeli przedstawiono relację między klasą modelu `CriticalSection`wątku a klasą sekcji krytycznej, do których odwołują się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`programu , można użyć nazwy **typedef** [AutoCriticalSection](#autocriticalsection). Nie należy `AutoCriticalSection` określać w obiektach globalnych lub statycznych członków klasy, jeśli chcesz wyeliminować kod startowy CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::Dekrównik

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), która zmniejsza wartość zmiennej wskazywalnej przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma zostać zdymisjonowana.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik dekrementacji wynosi 0, zwraca wartość `Decrement` 0. Jeśli wynik dekrementacji jest niezerowy, zwracana wartość jest również niezerowa, ale może nie być równa wyniku dekrementacji.

### <a name="remarks"></a>Uwagi

`InterlockedDecrement`zapobiega jednoczesnemu używaniu tej zmiennej więcej niż jednego wątku.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel::Przyrost

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), która zwiększa wartość zmiennej wskazywalnej przez *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do zmiennej, która ma być zwiększana.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynikiem przyrostu jest 0, `Increment` zwraca wartość 0. Jeśli wynik przyrostu jest niezerowy, zwracana wartość jest również niezerowa, ale może nie być równa wyniku przyrostu.

### <a name="remarks"></a>Uwagi

`InterlockedIncrement`zapobiega jednoczesnemu używaniu tej zmiennej więcej niż jednego wątku.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

Podczas `CComMultiThreadModel`korzystania z , `ThreadModelNoCS` **nazwa typedef** odwołuje się do klasy [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS`zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania zmiennej; jednak nie zapewnia sekcji krytycznej.

[CComSingleThreadModel,](ccomsinglethreadmodel-class.md) a `CComMultiThreadModelNoCS` także `ThreadModelNoCS`zawierają definicje dla . W poniższej tabeli przedstawiono relację między klasą `ThreadModelNoCS`modelu wątkowego a klasą, do których odwołuje się:

|Klasa zdefiniowana w|Klasa, do którego istnieje odwołanie|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Zobacz też

[Klasa CComSingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Klasa CComAutoCriticalSekcja](ccomautocriticalsection-class.md)<br/>
[Klasa CComCriticalSekcja](ccomcriticalsection-class.md)<br/>
[Przegląd klas](../atl-class-overview.md)
