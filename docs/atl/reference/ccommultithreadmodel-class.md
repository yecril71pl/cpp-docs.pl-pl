---
title: Klasa CComMultiThreadModel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6861f19e6b785ac72edec54577b92dea0c307bff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100607"
---
# <a name="ccommultithreadmodel-class"></a>Klasa CComMultiThreadModel

`CComMultiThreadModel` zapewnia metody obsługujące wielowątkowość zwiększanie i zmniejszanie wartości zmiennej.

## <a name="syntax"></a>Składnia

```
class CComMultiThreadModel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Odwołuje się do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Statyczny) Zmniejsza wartość określonej zmiennej w sposób bezpieczny dla wątków.|
|[CComMultiThreadModel::Increment](#increment)|(Statyczny) Zwiększa wartość zmiennej określonej w sposób bezpieczny dla wątków.|

## <a name="remarks"></a>Uwagi

Zazwyczaj można użyć `CComMultiThreadModel` za pomocą jednego z dwóch **typedef** nazwy albo [CComObjectThreadModel] (atl-typedefs.md #ccomobjectthreadmodel lub [CComGlobalsThreadModel] (atl-typedefs.md #ccomglobalsthreadmodel. Klasa przywoływana przez każdą **typedef** zależy od modelu wątkowości używane, jak pokazano w poniższej tabeli:

|— klasa typedef|Pojedynczy wątkowości|Wątkowość|Bezpłatne wątkowości|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComMultiThreadModel` sam definiuje trzy **typedef** nazwy. `AutoCriticalSection` i `CriticalSection` odwoływać się do klasy, które zapewniają metody uzyskiwania i zwalniania własności sekcję krytyczną. `ThreadModelNoCS` odwołania do klasy [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

Korzystając z `CComMultiThreadModel`, **typedef** nazwa `AutoCriticalSection` odwołuje się do klasy [CComAutoCriticalSection](ccomautocriticalsection-class.md), który zawiera metody służące do uzyskania i zwalnianie własności sekcję krytyczną obiekt.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) również zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `AutoCriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `AutoCriticalSection`, możesz użyć **typedef** nazwa [CriticalSection](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

Poniższy kod jest modelowane [CComObjectRootEx](ccomobjectrootex-class.md)i pokazuje `AutoCriticalSection` używane w środowisku wątków.

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

W poniższej tabeli przedstawiono wyniki `InternalAddRef` i `Lock` metod, w zależności od `ThreadModel` parametrem szablonu i model wątków używanych przez aplikację:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Jedno- lub wątkowość|Bezpłatne, wątkowości|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest metodą o bezpiecznych wątkach.|Przyrost jest metodą o bezpiecznych wątkach.|
|`Lock`|Nie wykonuje żadnych czynności; nie istnieje żadna sekcja krytycznego do blokowania.|Sekcja krytycznego jest zablokowana.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Metoda|Jedno- lub wątkowość|Bezpłatne, wątkowości|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Przyrost nie jest metodą o bezpiecznych wątkach.|Przyrost jest metodą o bezpiecznych wątkach.|
|`Lock`|Nie wykonuje żadnych czynności; nie istnieje żadna sekcja krytycznego do blokowania.|Nie wykonuje żadnych czynności; nie istnieje żadna sekcja krytycznego do blokowania.|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

Korzystając z `CComMultiThreadModel`, **typedef** nazwa `CriticalSection` odwołuje się do klasy [CComCriticalSection](ccomcriticalsection-class.md), który zawiera metody służące do uzyskania i zwalnianie własności obiektu sekcję krytyczną.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Uwagi

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) również zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy sekcję krytyczną, odwołuje się `CriticalSection`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Oprócz `CriticalSection`, możesz użyć **typedef** nazwa [AutoCriticalSection](#autocriticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub statycznych składowych, jeśli chcesz wyeliminować kod uruchamiający CRT.

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement), która zmniejsza wartość zmiennej wskazywany przez *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej do zmniejszenia.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik dekrementacji wynosi 0, to `Decrement` zwraca wartość 0. Wynik dekrementacji jest różna od zera, wartość zwracana, również jest różna od zera, ale nie może mieć wartość równą wynik dekrementacji.

### <a name="remarks"></a>Uwagi

`InterlockedDecrement` Zapobiega więcej niż jeden wątek jednocześnie przy użyciu tej zmiennej.

##  <a name="increment"></a>  CComMultiThreadModel::Increment

Ta funkcja statyczna wywołuje funkcję Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement), która zwiększa wartość zmiennej, do których prowadzą *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do zmiennej, aby być zwiększony.

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik przyrostu jest równy 0, następnie `Increment` zwraca wartość 0. Wynik przyrost jest różna od zera, wartość zwracana jest również wartość różną od zera, ale nie może mieć wartość równą wartości przyrostu.

### <a name="remarks"></a>Uwagi

`InterlockedIncrement` Zapobiega więcej niż jeden wątek jednocześnie przy użyciu tej zmiennej.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

Korzystając z `CComMultiThreadModel`, **typedef** nazwa `ThreadModelNoCS` odwołuje się do klasy [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Uwagi

`CComMultiThreadModelNoCS` zapewnia metody obsługujące wielowątkowość zwiększanie i zmniejszanie zmiennej; jednak nie zapewnia sekcję krytyczną.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) i `CComMultiThreadModelNoCS` również zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasą modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:

|Klasy zdefiniowanej w|Odwołanie do klasy|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Przykład

Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Zobacz też

[Klasa CComSingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Klasa CComAutoCriticalSection](ccomautocriticalsection-class.md)<br/>
[Klasa CComCriticalSection](ccomcriticalsection-class.md)<br/>
[Klasa — Przegląd](../atl-class-overview.md)
