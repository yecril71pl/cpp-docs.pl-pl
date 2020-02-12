---
title: Context — Klasa
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143131"
---
# <a name="context-class"></a>Context — Klasa

Reprezentuje streszczenie dla kontekstu wykonania.

## <a name="syntax"></a>Składnia

```cpp
class Context;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[~ Context — destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Blok](#block)|Blokuje bieżący kontekst.|
|[CurrentContext](#currentcontext)|Zwraca wskaźnik do bieżącego kontekstu.|
|[GetId —](#getid)|Zwraca identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy kontekst.|
|[Getschedulegroupid —](#getschedulegroupid)|Zwraca identyfikator grupy harmonogramu, nad którą aktualnie pracuje kontekst.|
|[Getvirtualprocessorid —](#getvirtualprocessorid)|Zwraca identyfikator procesora wirtualnego, na którym aktualnie wykonywany jest kontekst.|
|[Identyfikator](#id)|Zwraca identyfikator bieżącego kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy bieżący kontekst.|
|[Iscurrenttaskcollectioncanceling —](#iscurrenttaskcollectioncanceling)|Zwraca wskazanie, czy kolekcja zadań, która jest obecnie wykonywana wewnętrznie w bieżącym kontekście, znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce).|
|[Issynchronouslyblocked —](#issynchronouslyblocked)|Określa, czy kontekst jest blokowany synchronicznie. Kontekst jest uznawany za synchronicznie blokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokowania.|
|[Oversubscribe —](#oversubscribe)|Wprowadza dodatkowy procesor wirtualny do harmonogramu na czas trwania bloku kodu wywoływany w kontekście wykonywanym na jednym z procesorów wirtualnych w tym harmonogramie.|
|[Schedulegroupid —](#schedulegroupid)|Zwraca identyfikator grupy harmonogramu, w której działa bieżący kontekst.|
|[Odblokować](#unblock)|Odblokowuje kontekst i powoduje, że staje się on możliwy do uruchomienia.|
|[Virtualprocessorid —](#virtualprocessorid)|Zwraca identyfikator procesora wirtualnego, na którym jest wykonywany bieżący kontekst.|
|[Zbiór](#yield)|Przekazuje wykonywanie, aby można było wykonać inny kontekst. Jeśli żaden inny kontekst nie jest dostępny do przekazywania, harmonogram może przekazać do innego wątku systemu operacyjnego.|

## <a name="remarks"></a>Uwagi

Harmonogram środowisko uruchomieniowe współbieżności (zobacz [Scheduler](scheduler-class.md)) używa kontekstów wykonywania, aby wykonać pracę umieszczoną w kolejce przez aplikację. Wątek Win32 to przykład kontekstu wykonywania w systemie operacyjnym Windows.

W dowolnym momencie poziom współbieżności harmonogramu jest równy liczbie procesorów wirtualnych przyznanych mu przez Menedżer zasobów. Procesor wirtualny jest abstrakcją dla zasobu przetwarzania i jest mapowany na wątek sprzętowy w systemie bazowym. Tylko jeden kontekst harmonogramu można wykonać na wirtualnym procesorze w danym momencie.

Harmonogram jest w tej samej firmie, a kontekst wykonywania może przynieść swój procesor wirtualny do innego kontekstu w dowolnym momencie, jeśli chce wprowadzić stan oczekiwania. Gdy jej oczekiwanie zaczeka, nie można jej wznowić, dopóki nie rozpocznie się wykonywanie przez harmonogram dostępnego procesora wirtualnego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Context`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="block"></a>Odblokowan

Blokuje bieżący kontekst.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

Jeśli kontekst wywołujący jest uruchomiony w procesorze wirtualnym, procesor wirtualny znajdzie inny kontekst możliwy do uruchomienia do wykonania lub może potencjalnie utworzyć nowy.

Po wywołaniu metody `Block` lub wywołaniu należy sparować ją z wywołaniem metody [odblokowywania](#unblock) z innego kontekstu wykonywania w celu ponownego uruchomienia. Należy pamiętać, że istnieje krytyczny okres między punktem, w którym kod publikuje swój kontekst dla innego wątku, aby wywołać metodę `Unblock` i miejsce, w którym zostanie wykonane rzeczywiste wywołanie metody `Block`. W tym okresie nie należy wywoływać żadnej metody, która może z kolei blokować i odblokować z własnych powodów (na przykład podczas uzyskiwania blokady). Wywołania metody `Block` i `Unblock` nie śledzą przyczyny blokowania i odblokowywania. Tylko jeden obiekt powinien mieć własność pary `Unblock` `Block`- .

Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Kontekst

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Zwraca wskaźnik do bieżącego kontekstu.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do bieżącego kontekstu.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

## <a name="getid"></a>GetId —

Zwraca identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy kontekst.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy kontekst.

## <a name="getschedulegroupid"></a>Getschedulegroupid —

Zwraca identyfikator grupy harmonogramu, nad którą aktualnie pracuje kontekst.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Identyfikator grupy harmonogramu, nad którą aktualnie pracuje kontekst.

### <a name="remarks"></a>Uwagi

Wartość zwracana z tej metody jest chwilową próbką grupy harmonogramu, w której wykonywany jest kontekst. Jeśli ta metoda jest wywoływana w kontekście innym niż bieżący kontekst, wartość może być nieaktualna w momencie zwrócenia i nie może być używana. Zazwyczaj ta metoda jest używana tylko do celów debugowania lub śledzenia.

## <a name="getvirtualprocessorid"></a>Getvirtualprocessorid —

Zwraca identyfikator procesora wirtualnego, na którym aktualnie wykonywany jest kontekst.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli kontekst jest aktualnie wykonywany w procesorze wirtualnym, identyfikator procesora wirtualnego, na którym jest aktualnie wykonywany ten kontekst; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Wartość zwracana z tej metody jest chwilową próbką procesora wirtualnego, na którym wykonywany jest kontekst. Ta wartość może być nieaktualna w momencie zwrócenia i nie może być używana. Zazwyczaj ta metoda jest używana tylko do celów debugowania lub śledzenia.

## <a name="id"></a>#

Zwraca identyfikator bieżącego kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy bieżący kontekst.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator bieżącego kontekstu, który jest unikatowy w obrębie harmonogramu, do którego należy bieżący kontekst; w przeciwnym razie wartość `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>Iscurrenttaskcollectioncanceling —

Zwraca wskazanie, czy kolekcja zadań, która jest obecnie wykonywana wewnętrznie w bieżącym kontekście, znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce).

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli harmonogram jest dołączony do kontekstu wywołującego, a grupa zadań wykonuje zadanie wbudowane w tym kontekście, wskazuje, czy ta grupa zadań znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce); w przeciwnym razie wartość `false`.

## <a name="issynchronouslyblocked"></a>Issynchronouslyblocked —

Określa, czy kontekst jest blokowany synchronicznie. Kontekst jest uznawany za synchronicznie blokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokowania.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Czy kontekst jest blokowany synchronicznie.

### <a name="remarks"></a>Uwagi

Kontekst jest uznawany za synchronicznie blokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokowania. W harmonogramie wątków oznacza to bezpośrednie wywołanie metody `Context::Block` lub obiektu synchronizacji, który został skompilowany przy użyciu metody `Context::Block`.

Wartość zwracana przez tę metodę jest chwilową próbką, czy kontekst jest blokowany synchronicznie. Ta wartość może być nieaktualna w momencie jej zwrócenia i może być używana tylko w określonych okolicznościach.

## <a name="operator_delete"></a>Usuwanie operatora

Obiekt `Context` jest niszczony wewnętrznie przez środowisko uruchomieniowe. Nie można go jawnie usunąć.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parametry

*_PObject*<br/>
Wskaźnik do obiektu, który ma zostać usunięty.

## <a name="oversubscribe"></a>Oversubscribe —

Wprowadza dodatkowy procesor wirtualny do harmonogramu na czas trwania bloku kodu wywoływany w kontekście wykonywanym na jednym z procesorów wirtualnych w tym harmonogramie.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parametry

*_BeginOversubscription*<br/>
Jeśli **wartość jest równa true**, oznacza to, że dodatkowy procesor wirtualny należy dodać na czas trwania nadmiernej subskrypcji. W przypadku **wartości false**należy wskazać, że nadsubskrypcja powinna zostać zakończona, a wcześniej dodany procesor wirtualny powinien zostać usunięty.

## <a name="schedulegroupid"></a>Schedulegroupid —

Zwraca identyfikator grupy harmonogramu, w której działa bieżący kontekst.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli bieżący kontekst jest dołączony do harmonogramu i pracujesz nad grupą harmonogramów, identyfikator grupy harmonogramu, nad którą pracuje bieżący kontekst; w przeciwnym razie wartość `-1`.

## <a name="unblock"></a>Odblokować

Odblokowuje kontekst i powoduje, że staje się on możliwy do uruchomienia.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Uwagi

Doskonale nawiąże się z wywołaniem metody `Unblock` przed odpowiednim wywołaniem metody [Block](#block) . Tak długo, jak wywołania metod `Block` i `Unblock` są prawidłowo sparowane, środowisko uruchomieniowe prawidłowo obsługuje naturalną rasę każdej kolejności. Wywołanie `Unblock` wywołane przed wywołaniem `Block` po prostu wyklucza efekt wywołania `Block`.

Istnieje kilka wyjątków, które mogą zostać zgłoszone przez tę metodę. Jeśli kontekst próbuje wywołać metodę `Unblock`ową dla samej siebie, zostanie zgłoszony wyjątek [context_self_unblock](context-self-unblock-class.md) . Jeśli wywołania `Block` i `Unblock` nie są poprawnie sparowane (na przykład dwa wywołania `Unblock` są wykonywane dla kontekstu, który jest aktualnie uruchomiony), zostanie zgłoszony wyjątek [context_unblock_unbalanced](context-unblock-unbalanced-class.md) .

Należy pamiętać, że istnieje krytyczny okres między punktem, w którym kod publikuje swój kontekst dla innego wątku, aby wywołać metodę `Unblock` i miejsce, w którym zostanie wykonane rzeczywiste wywołanie metody `Block`. W tym okresie nie należy wywoływać żadnej metody, która może z kolei blokować i odblokować z własnych powodów (na przykład podczas uzyskiwania blokady). Wywołania metody `Block` i `Unblock` nie śledzą przyczyny blokowania i odblokowywania. Tylko jeden obiekt powinien mieć własność pary `Block` i `Unblock`.

## <a name="virtualprocessorid"></a>Virtualprocessorid —

Zwraca identyfikator procesora wirtualnego, na którym jest wykonywany bieżący kontekst.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator procesora wirtualnego, na którym jest wykonywany bieżący kontekst; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Wartość zwracana z tej metody jest chwilową próbką procesora wirtualnego, na którym jest wykonywany bieżący kontekst. Ta wartość może być nieaktualna w momencie zwrócenia i nie może być używana. Zazwyczaj ta metoda jest używana tylko do celów debugowania lub śledzenia.

## <a name="yield"></a>Zbiór

Przekazuje wykonywanie, aby można było wykonać inny kontekst. Jeśli żaden inny kontekst nie jest dostępny do przekazywania, harmonogram może przekazać do innego wątku systemu operacyjnego.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

## <a name="yieldexecution"></a>YieldExecution

Przekazuje wykonywanie, aby można było wykonać inny kontekst. Jeśli żaden inny kontekst nie jest dostępny do przekazywania, harmonogram może przekazać do innego wątku systemu operacyjnego.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

Ta funkcja jest nowa w programie Visual Studio 2015 i jest taka sama jak funkcja [Yield](#yield) , ale nie powoduje konfliktu z makrem Yield w systemie Windows. h.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
