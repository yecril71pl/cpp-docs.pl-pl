---
title: '&lt;allocators —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <allocators>
dev_langs:
- C++
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f578ab4ea06db68b23a03374bcd787dc03715ab5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847315"
---
# <a name="ltallocatorsgt"></a>&lt;allocators —&gt;

Definiuje kilka szablonów, które pomagają przydzielić i zwolnij bloki pamięci dla kontenerów na podstawie węzła.

## <a name="syntax"></a>Składnia

```cpp
#include <allocators>
```

## <a name="remarks"></a>Uwagi

\<Allocators — > nagłówka oferuje sześć alokatora szablony, których można użyć do wybrania strategii zarządzania pamięci dla kontenerów na podstawie węzła. Do użytku z tych szablonów także kilka różnych synchronizacji filtrów dostosować strategii zarządzania pamięcią szereg różnych systemów wielowątkowości (w tym none). Dopasowywanie strategii zarządzania pamięci wzorce użycia pamięci znanych i wymaganiach dotyczących synchronizacji konkretnej aplikacji można często przyspieszenie lub Zmniejsz ogólnych wymagań dotyczących pamięci aplikacji.

Szablony programu przydzielania są implementowane przy użyciu składniki wielokrotnego użytku, które można dostosować lub zastąpić zapewnienie dodatkowych zarządzania pamięcią strategii.

Kontenerów na podstawie węzła w standardowej biblioteki C++ (kontener std::list, kontener std::set, std::multiset, std::map i std::multimap) przechowywania ich elementów w poszczególnych węzłach. Wszystkie węzły dla typu kontenerem są ten sam rozmiar, więc elastyczność Menedżera ogólnego przeznaczenia pamięci nie jest potrzebny. Ponieważ rozmiar każdego bloku pamięci jest znany w czasie kompilacji, Menedżer pamięci może być znacznie łatwiejsze i szybsze.

W przypadku użycia z kontenerów, które nie są oparte na węzłach (na przykład std::deque std::vector kontenery standardowa biblioteka C++ i std::basic_string), szablony alllocator będzie działał prawidłowo, ale prawdopodobnie nie zapewniają poprawy wydajności za pośrednictwem Program przydzielania domyślne.

Program przydzielania to klasa szablonu opisujący obiekt, który zarządza Alokacja magazynu i zwalnianie obiekty i tablice obiektów wyznaczonych typu. Allocator — obiekty są wykorzystywane przez kilka klas szablonów kontenera w standardowa biblioteka C++.

Allocators — są wszystkie szablony tego typu:

`template<class` `Type` `>`

`class allocator;`

gdzie argument szablonu `Type` jest zarządzane przez program przydzielania wystąpienie typu. Standardowa biblioteka C++ zawiera domyślne przydzielania, klasy szablonu [alokatora](../standard-library/allocator-class.md), która jest zdefiniowana w [ \<pamięci >](../standard-library/memory.md). \<Allocators — > Nagłówek zawiera następujący allocators —:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded —](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Użyj odpowiedniego wystąpienia alokatora jako drugi argument typu podczas tworzenia kontenera, takich jak w poniższym przykładzie kodu.

`#include <list>`

`#include <allocators>`

`std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`

Węzły o przydziela _List0 `allocator_chunklist` i domyślnego filtru synchronizacji.

Użyj makra [allocator_decl —](../standard-library/allocators-functions.md#allocator_decl) do tworzenia szablonów alokatora z filtrami synchronizacji inny niż domyślny:

`#include <list>`

`#include <allocators>`

`ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`

`std::list<int, alloc<int> > _List1;`

Węzły o przydziela _Lst1 `allocator_chunklist` i [sync_per_thread —](../standard-library/sync-per-thread-class.md) filtr synchronizacji.

Pamięć podręczną lub filtr jest przydzielania bloku. Pamięć podręczna jest szablon klasy, która przyjmuje jeden argument typu std::size_t. Definiuje przydzielania bloku, który przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego. Należy uzyskać przy użyciu operatora pamięci `new`, ale nie potrzebują sporządzać wymaga oddzielnego wywołania operatora `new` dla każdego bloku. Może na przykład alokacje podrzędne z większą bloku lub alokację bloków dla kolejnych; Ponowna alokacja pamięci podręcznej.

Z kompilatorem, którego nie można skompilować ponownie Utwórz wiązanie, wartość argumentu std::size_t używany, gdy utworzono wystąpienie szablonu, nie ma zawsze wartość _Sz argument przekazany do funkcji Członkowskich jako pamięci podręcznej przydzielić i cofnięcia przydzielenia.

\<allocators — > udostępnia następujące szablony pamięci podręcznej:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr jest przydzielania bloku, który implementuje jego funkcje Członkowskie przy użyciu innego przydzielania bloku, który jest przekazywany do niego jako argument szablonu. Najczęściej filtru jest filtrem synchronizacji, zastosowanie zasad synchronizacji, aby kontrolować dostęp do funkcji Członkowskich wystąpienia inny przydzielania bloku. \<allocators — > udostępnia następujące filtry synchronizacji:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators — > udostępnia również filtr [rts_alloc —](../standard-library/rts-alloc-class.md), które zawiera wiele przydzielania bloku wystąpień i określa, które wystąpienie na potrzeby alokacji lub dezalokacji w czasie wykonywania, a nie w czasie kompilacji. Jest ona używana z kompilatorów, których nie można skompilować ponownie Utwórz wiązanie.

Zasady synchronizacji Określa, jak wystąpienia alokatora obsługuje równoczesnych żądań alokacji i dezalokacji wiele wątków. Najprostsza zasad służy do przekazywania wszystkich żądań bezpośrednio za pomocą do źródłowego obiektu pamięci podręcznej, pozostawiając zarządzania synchronizacji dla użytkownika. Bardziej złożone zasady można serializować dostępu do obiektu źródłowego pamięci podręcznej przy użyciu elementu mutex.

Jeśli kompilatora obsługuje kompilowania aplikacji zarówno jednowątkowe i wielowątkowych, domyślnego filtru synchronizacji aplikacji jednowątkowych jest `sync_none`; dla wszystkich innych przypadkach jest `sync_shared`.

Szablon pamięci podręcznej `cache_freelist` przyjmuje argument max klasy, która określa maksymalną liczbę elementów, które mają być przechowywane w liście wolne.

\<allocators — > udostępnia następujące klasy maksymalna:

- [max_none —](../standard-library/max-none-class.md)

- [max_unbounded —](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size —](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|Macro|Opis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Daje alokatora klasy szablonu.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Daje `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST —](../standard-library/allocators-functions.md#cache_freelist)|Daje `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Daje `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Daje filtr synchronizacji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Operator! = (\<allocators — >)](../standard-library/allocators-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[Operator == (\<allocators — >)](../standard-library/allocators-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definiuje klasę podstawową i typowe funkcje niezbędne do utworzenia programu przydzielania zdefiniowane przez użytkownika z filtru synchronizacji.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów przy użyciu pamięci podręcznej typu [cache_chunklist —](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist —](../standard-library/cache-freelist-class.md) o długości zarządza [max_fixed_size —](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje przydzielania, która używa `operator delete` można cofnąć alokacji pamięci bloku i `operator new` przydzielić bloku pamięci.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_suballoc —](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded —](../standard-library/allocator-unbounded-class.md)|Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist —](../standard-library/cache-freelist-class.md) o długości zarządza [max_unbounded —](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist —](../standard-library/cache-freelist-class.md) o długości zarządza [max_variable_size —](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definiuje przydzielania bloku, który przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definiuje przydzielania bloku, który przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definiuje przydzielania bloku, który przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.|
|[FreeList —](../standard-library/freelist-class.md)|Zarządza listą bloki pamięci.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Zawiera opis obiektu max klasy, która ogranicza [elementu freelist](../standard-library/freelist-class.md) obiekt do stałej długości maksymalnej.|
|[max_none —](../standard-library/max-none-class.md)|Zawiera opis obiektu max klasy, która ogranicza [elementu freelist](../standard-library/freelist-class.md) obiektu maksymalną długość równą zero.|
|[max_unbounded —](../standard-library/max-unbounded-class.md)|Zawiera opis obiektu max klasy, która nie istnieje limit maksymalnego [elementu freelist](../standard-library/freelist-class.md) obiektu.|
|[max_variable_size —](../standard-library/max-variable-size-class.md)|Zawiera opis obiektu max klasy, która ogranicza [elementu freelist](../standard-library/freelist-class.md) obiektu maksymalną długość, który jest około proporcjonalny do liczby przydzielonych bloków pamięci.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Rts_alloc — klasa szablonu opisuje [filtru](../standard-library/allocators-header.md) zawierający tablicę pamięci podręcznej wystąpienia i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji.|
|[sync_none](../standard-library/sync-none-class.md)|Zawiera opis filtru synchronizacji, który dostarcza ma synchronizacji.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Zawiera opis filtru synchronizacji, który dostarcza obiektu osobne dla każdego obiektu przydzielania.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Zawiera opis filtru synchronizacji, który dostarcza obiektu osobne dla każdego wątku.|
|[sync_shared](../standard-library/sync-shared-class.md)|W tym artykule opisano filtr synchronizacji, który używa obiektu mutex do kontrolowania dostępu do obiektu, który jest współużytkowana przez wszystkie allocators —.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
