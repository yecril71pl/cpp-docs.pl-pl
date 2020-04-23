---
title: '&lt;Allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f6be154be68cd5e43fd6f934d88c04fb25be9dc5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754443"
---
# <a name="ltallocatorsgt"></a>&lt;Allocators&gt;

Definiuje kilka szablonów, które pomagają przydzielić i zwolnić bloki pamięci dla kontenerów opartych na węzłach.

## <a name="syntax"></a>Składnia

```cpp
#include <allocators>
```

> [!NOTE]
> \<przydziały> jest przestarzałe, począwszy od programu Visual Studio 2019 w wersji 16.3.

## <a name="remarks"></a>Uwagi

Nagłówki \<> alokatorów zawiera sześć szablonów alokatora, które mogą służyć do wybierania strategii zarządzania pamięcią dla kontenerów opartych na węzłach. Do użytku z tych szablonów, zapewnia również kilka różnych filtrów synchronizacji, aby dostosować strategię zarządzania pamięcią do różnych schematów wielowątkowych (w tym żaden). Można przyspieszyć aplikację lub zmniejszyć jej wymagania dotyczące pamięci, dopasowując strategię zarządzania pamięcią do wzorców użycia pamięci i wymagań synchronizacji.

Szablony alokatora są implementowane za pomocą składników wielokrotnegoużytnia, które można dostosować lub zastąpić, aby zapewnić dodatkowe strategie zarządzania pamięcią.

Kontenery oparte na węzłach w standardowej bibliotece języka C++ (std::list, std::set, std::multiset, std::map i std::multimap) przechowują swoje elementy w poszczególnych węzłach. Wszystkie węzły dla określonego typu kontenera mają ten sam rozmiar, więc elastyczność menedżera pamięci ogólnego przeznaczenia nie jest potrzebna. Ponieważ rozmiar każdego bloku pamięci jest znany w czasie kompilacji, menedżer pamięci może być znacznie prostsze i szybsze.

W przypadku użycia z kontenerami, które nie są oparte na węźle (takich jak kontenery biblioteki standardowej języka C++basic_string :d:

Alokator to szablon klasy opisujący obiekt, który zarządza alokacją magazynu i zwalnianiem obiektów i tablic obiektów określonego typu. Obiekty alokatora są używane przez kilka szablonów klas kontenera w bibliotece standardowej języka C++.

Alokatory są wszystkie szablony tego typu:

```cpp
template<class Type>
class allocator;
```

gdzie argument `Type` szablonu jest typem zarządzanym przez wystąpienie alokatora. Standardowa biblioteka języka C++ udostępnia domyślny alokator, [alokator](../standard-library/allocator-class.md)szablonów klas, który jest zdefiniowany w [ \<pamięci>](../standard-library/memory.md). Nagłówki \<alokatorów> zawiera następujące alokatory:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Użyj odpowiedniego wystąpienia alokatora jako drugiego argumentu typu podczas tworzenia kontenera, takiego jak poniższy przykład kodu.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 przydziela węzły z `allocator_chunklist` i domyślnym filtrem synchronizacji.

Użyj [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) makr, aby utworzyć szablony alokatora z filtrami synchronizacji innymi niż domyślne:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 przydziela węzły z `allocator_chunklist` filtrem synchronizacji sync_per_thread i [sync_per_thread.](../standard-library/sync-per-thread-class.md)

Alokator bloków jest pamięcią podręczną lub filtrem. Pamięć podręczna jest szablonem klasy, który przyjmuje jeden argument typu std::size_t. Definiuje alokator blokowy, który przydziela i przydziela bloki pamięci o jednym rozmiarze. Musi uzyskać pamięć przy użyciu operatora **nowy**, ale nie musi dokonać oddzielnego wywołania operatora **nowy** dla każdego bloku. Może na przykład suballocate z większego bloku lub pamięci podręcznej oklokowane bloki do późniejszego ponownego przydziału.

Z kompilatorem, który nie może ponownie powiększyć wartość argumentu std::size_t używanego podczas tworzenia wystąpienia szablonu, niekoniecznie jest wartością argumentu, _Sz przekazana do funkcji członkowskich pamięci podręcznej przydzielić i przydzielić alokację.

\<> alokatorów udostępnia następujące szablony pamięci podręcznej:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr jest alokatorem bloków, który implementuje swoje funkcje członkowskie przy użyciu innego alokatora bloków, który jest przekazywany do niego jako argument szablonu. Najczęstszą formą filtru jest filtr synchronizacji, który stosuje zasady synchronizacji do kontrolowania dostępu do funkcji członkowskich wystąpienia innego alokatora bloków. \<> zapewnia następujące filtry synchronizacji:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<alokatorów> również filtr [rts_alloc](../standard-library/rts-alloc-class.md), który zawiera wiele wystąpień alokatora bloków i określa, które wystąpienie do użycia do alokacji lub alokacji transakcji w czasie wykonywania, a nie w czasie kompilacji. Jest on używany z kompilatorami, które nie można skompilować rebind.

Zasady synchronizacji określa, jak wystąpienie alokatora obsługuje jednoczesne żądania alokacji i alokacji z wielu wątków. Najprostszą zasadą jest przekazywanie wszystkich żądań bezpośrednio do obiektu podstawowej pamięci podręcznej, pozostawiając zarządzanie synchronizacją użytkownikowi. Bardziej złożone zasady może być użycie obiektu mutex do serializacji dostępu do obiektu podstawowej pamięci podręcznej.

Jeśli kompilator obsługuje kompilowanie zarówno aplikacji jednowątkowych, jak i wielowątkowych, domyślny filtr synchronizacji dla aplikacji jednowątkowych jest `sync_none`; we wszystkich innych `sync_shared`przypadkach jest to .

Szablon `cache_freelist` pamięci podręcznej przyjmuje argument klasy max, który określa maksymalną liczbę elementów, które mają być przechowywane na liście wolnych.

\<> zapewnia następujące klasy max:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|Makro|Opis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Daje szablon klasy alokatora.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Plony `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Plony `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Plony `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Daje filtr synchronizacji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=\<( alokatorów>)](../standard-library/allocators-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[operator==\<( alokatory>)](../standard-library/allocators-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definiuje klasę podstawową i typowe funkcje potrzebne do utworzenia alokatora zdefiniowanego przez użytkownika z filtru synchronizacji.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|W tym artykule opisano obiekt, który zarządza alokacją magazynu i zwalnianiem obiektów przy użyciu pamięci podręcznej typu [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|W tym artykule opisano obiekt, który zarządza `Type` alokacją magazynu i zwalnianiem obiektów typu przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_fixed_size](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje alokator, który używa **usuwania operatora** do usuwania alokacji bloku pamięci i **operatora nowy,** aby przydzielić blok pamięci.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|W tym artykule opisano obiekt, który zarządza `Type` alokacją magazynu i zwalnianiem obiektów typu przy użyciu pamięci podręcznej typu [cache_suballoc](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|W tym artykule opisano obiekt, który zarządza `Type` alokacją magazynu i zwalnianiem obiektów typu przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_unbounded](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|W tym artykule opisano obiekt, który zarządza `Type` alokacją magazynu i zwalnianiem obiektów typu przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_variable_size](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definiuje alokator bloków, który przydziela i przydziela bloki pamięci o jednym rozmiarze.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definiuje alokator bloków, który przydziela i przydziela bloki pamięci o jednym rozmiarze.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definiuje alokator bloków, który przydziela i przydziela bloki pamięci o jednym rozmiarze.|
|[freelist](../standard-library/freelist-class.md)|Zarządza listą bloków pamięci.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Opisuje obiekt klasy max, który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do stałej maksymalnej długości.|
|[max_none](../standard-library/max-none-class.md)|Opisuje obiekt klasy max, który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do maksymalnej długości zero.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Opisuje obiekt klasy max, który nie ogranicza maksymalnej długości obiektu [freelist.](../standard-library/freelist-class.md)|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Opisuje obiekt klasy max, który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do maksymalnej długości, która jest w przybliżeniu proporcjonalna do liczby przydzielonych bloków pamięci.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Szablon klasy rts_alloc opisuje [filtr,](../standard-library/allocators-header.md) który zawiera tablicę wystąpień pamięci podręcznej i określa, które wystąpienie ma być używane do alokacji i alokacji w czasie wykonywania, a nie w czasie kompilacji.|
|[sync_none](../standard-library/sync-none-class.md)|W tym artykule opisano filtr synchronizacji, który nie zapewnia synchronizacji.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|W tym artykule opisano filtr synchronizacji, który udostępnia oddzielny obiekt pamięci podręcznej dla każdego obiektu alokatora.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|W tym artykule opisano filtr synchronizacji, który zapewnia oddzielny obiekt pamięci podręcznej dla każdego wątku.|
|[sync_shared](../standard-library/sync-shared-class.md)|W tym artykule opisano filtr synchronizacji, który używa obiektu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkie alokatory.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
