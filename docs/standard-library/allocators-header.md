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
ms.openlocfilehash: 1a1d2d710631c01a39b910e7d9b15f14179b3125
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965746"
---
# <a name="ltallocatorsgt"></a>&lt;Buforów&gt;

Definiuje kilka szablonów, które pomagają przydzielać i zwalniać bloki pamięci dla kontenerów opartych na węźle.

## <a name="syntax"></a>Składnia

```cpp
#include <allocators>
```

## <a name="remarks"></a>Uwagi

\<Buforów > Nagłówek zawiera sześć szablonów programu przydzielania, które mogą służyć do wybierania strategie zarządzania pamięci dla kontenerów opartych na węźle. Korzystanie z tych szablonów zawiera także kilka filtrów różnych synchronizacji dostosować strategię zarządzania pamięcią z szeroką gamą różnych systemów wielowątkowości (w tym none). Dopasowanie strategii zarządzania pamięci do pamięci znanych wzorców użycia i wymagania dotyczące synchronizacji określonej aplikacji można często zwiększyć szybkość lub zmniejszyć ogólne wymagania dotyczące pamięci aplikacji.

Szablony programu przydzielania są implementowane za pomocą składniki wielokrotnego użytku, które można dostosować lub zastąpione, aby zapewnić dodatkowe zarządzanie pamięcią strategii.

Kontenery oparte na węzłach w standardowej bibliotece C++ (kontener std::list, kontener std::set, std::multiset, std::map i std::multimap) przechowywania ich elementy w poszczególnych węzłach. Wszystkie węzły z konkretnym typem kontenera jest taki sam rozmiar dzięki elastyczności Menedżera pamięci ogólnego przeznaczenia nie jest potrzebna. Ponieważ rozmiar każdy blok pamięci jest znany w czasie kompilacji, Menedżer pamięci może być znacznie prostszy i szybszy.

W przypadku użycia za pomocą kontenerów, które nie są oparte na węzłach (na przykład std::deque std::vector kontenery standardowej biblioteki języka C++ i std::basic_string), szablony alllocator będą działać poprawnie, ale prawdopodobnie nie zapewnia poprawy wydajności domyślnego programu przydzielania.

Alokatora jest klasa szablonu opisująca obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiekty i tablice obiektów wyznaczonym typu. Obiektami alokatora są używane przez szereg klas szablonu kontenera standardowej biblioteki języka C++.

Allocators — są wszystkie szablony tego typu:

`template<class` `Type` `>`

`class allocator;`

gdy argument szablonu `Type` jest typu zarządzanego przez to wystąpienie programu przydzielania. Standardowa biblioteka C++ zawiera domyślnego programu przydzielania, szablon klasy [alokatora](../standard-library/allocator-class.md), który jest zdefiniowany w [ \<pamięci >](../standard-library/memory.md). \<Buforów > Nagłówek zawiera następujący buforów:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded —](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Podczas tworzenia kontenera, na przykład w poniższym przykładzie kodu należy użyć odpowiedniej podczas tworzenia wystąpienia alokatora jako drugi argument typu.

`#include <list>`

`#include <allocators>`

`std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`

_List0 przydziela węzły z `allocator_chunklist` i domyślny filtr synchronizacji.

Użyj makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) do tworzenia szablonów alokatora z filtrami synchronizacji inny niż domyślny:

`#include <list>`

`#include <allocators>`

`ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`

`std::list<int, alloc<int> > _List1;`

_Lst1 przydziela węzły z `allocator_chunklist` i [sync_per_thread —](../standard-library/sync-per-thread-class.md) filtr synchronizacji.

Alokator bloku jest pamięć podręczna lub filtru. Pamięć podręczna jest klasą szablonu, który przyjmuje jeden argument typu std::size_t. Definiuje alokator bloku, który przydziela i zwalnia bloki pamięci o rozmiarze jednego. Musi uzyskać pamięci za pomocą operatora **nowe**, ale potrzebujesz tworzy osobne wywołanie operatora **nowe** dla każdego bloku. Na przykład, może on podrzędnej z większych blokowych lub bloków dla kolejnych ponownej alokacji z cofniętą alokacją pamięci podręcznej.

Za pomocą kompilatora nie można skompilować ponowne wiązanie, wartość argumentu std::size_t używany, gdy szablon został uruchomiony, nie ma zawsze wartość _Sz argument przekazany do funkcji elementów członkowskich w pamięci podręcznej przydzielić i cofnąć jej przydział.

\<allocators — > zawiera następujące szablony pamięci podręcznej:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr jest alokator bloku, który implementuje jej funkcje Członkowskie przy użyciu innego alokator bloku, który jest przekazywany do niej jako argument szablonu. Najczęściej używany typ filtru jest filtr synchronizacji mają zastosowanie zasady synchronizacji, aby kontrolować dostęp do funkcji składowych wystąpienia innym alokator bloku. \<allocators — > zawiera następujące filtry synchronizacji:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators — > udostępnia również filtr [rts_alloc —](../standard-library/rts-alloc-class.md), który posiada wiele alokator bloku wystąpień i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji. Kompilatory, których nie można skompilować ponowne wiązanie jest używany.

Zasady synchronizacji Określa, jak wystąpienie programu przydzielania obsługuje równoczesnych żądań alokacji i dezalokacji z wielu wątków. Najprostszą jest przekazywanie wszystkich żądań bezpośrednio przez do bazowego obiektu pamięci podręcznej, pozostawiając zarządzania synchronizacji dla użytkownika. Bardziej złożone zasady można serializować dostęp do bazowego obiektu pamięci podręcznej za pomocą elementu mutex.

Jeśli kompilator obsługuje kompilowanie aplikacje jednowątkowe i wielowątkowych, jest domyślnego filtru synchronizacji aplikacje jednowątkowe `sync_none`; w przypadku wszystkich innych przypadkach jest `sync_shared`.

Szablon pamięci podręcznej `cache_freelist` przyjmuje argument max klasy, która określa maksymalną liczbę elementów, które mają być przechowywane na liście bezpłatne.

\<allocators — > zawiera następujące klasy maksymalna:

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
|[Operator! = (\<buforów >)](../standard-library/allocators-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[Operator == (\<buforów >)](../standard-library/allocators-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definiuje klasę bazową i typowe funkcje potrzebne do utworzenia programu przydzielania zdefiniowanych przez użytkownika z filtru synchronizacji.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów przy użyciu pamięci podręcznej typu [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu `Type` używanie pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządza [max_fixed_size —](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje alokatora, który używa **operatora delete** można cofnąć alokacji pamięci bloku i **nowy operator** można przydzielić bloku pamięci.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu `Type` używanie pamięci podręcznej typu [cache_suballoc](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded —](../standard-library/allocator-unbounded-class.md)|Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu `Type` używanie pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządza [max_unbounded —](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu `Type` używanie pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządza [max_variable_size —](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definiuje alokator bloku, który przydziela i zwalnia bloki pamięci o rozmiarze jednego.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definiuje alokator bloku, który przydziela i zwalnia bloki pamięci o rozmiarze jednego.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definiuje alokator bloku, który przydziela i zwalnia bloki pamięci o rozmiarze jednego.|
|[FreeList —](../standard-library/freelist-class.md)|Zarządza listą bloki pamięci.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Zawiera opis obiektu max klasy, która ogranicza [FreeList —](../standard-library/freelist-class.md) obiekt do stałej długości maksymalnej.|
|[max_none —](../standard-library/max-none-class.md)|Zawiera opis obiektu max klasy, która ogranicza [FreeList —](../standard-library/freelist-class.md) obiektu do maksymalnej długości równy zero.|
|[max_unbounded —](../standard-library/max-unbounded-class.md)|Zawiera opis obiektu max klasy, która nie istnieje limit maksymalnego [FreeList —](../standard-library/freelist-class.md) obiektu.|
|[max_variable_size —](../standard-library/max-variable-size-class.md)|Zawiera opis obiektu max klasy, która ogranicza [FreeList —](../standard-library/freelist-class.md) obiektu do maksymalnej długości, który jest około proporcjonalny do liczby przydzielonych bloków pamięci.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Rts_alloc — klasa szablonu opisuje [filtru](../standard-library/allocators-header.md) zawierający tablicę pamięci podręcznej wystąpień i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji.|
|[sync_none](../standard-library/sync-none-class.md)|W tym artykule opisano filtr synchronizacji, który zapewnia brak synchronizacji.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|W tym artykule opisano filtr synchronizacji, który dostarcza obiekt oddzielne pamięci podręcznej dla każdego obiektu programu przydzielania.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|W tym artykule opisano filtr synchronizacji, który dostarcza obiekt oddzielne pamięci podręcznej dla każdego wątku.|
|[sync_shared](../standard-library/sync-shared-class.md)|W tym artykule opisano filtr synchronizacji, który używa obiektu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkich buforów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
