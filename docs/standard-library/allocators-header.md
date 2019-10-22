---
title: '&lt;allocators &gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: 3619f3810f167fef291ad3def4a2b94f9a6b9b1a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688478"
---
# <a name="ltallocatorsgt"></a>&lt;allocators &gt;

Definiuje kilka szablonów, które ułatwiają przydzielanie i zwalnianie bloków pamięci dla kontenerów opartych na węzłach.

## <a name="syntax"></a>Składnia

```cpp
#include <allocators>
```

## <a name="remarks"></a>Uwagi

Nagłówek > \<allocators zawiera sześć szablonów alokatora, których można użyć do wybrania strategii zarządzania pamięcią dla kontenerów opartych na węzłach. Do użycia z tymi szablonami zapewnia także kilka różnych filtrów synchronizacji w celu dostosowywania strategii zarządzania pamięcią do różnych różnych schematów wielowątkowości (w tym brak). Dopasowanie strategii zarządzania pamięcią do znanych wzorców użycia pamięci i wymagania dotyczące synchronizacji konkretnej aplikacji może często zwiększyć szybkość lub zmniejszyć ogólne wymagania dotyczące pamięci aplikacji.

Szablony programu przydzielania są implementowane za pomocą składników wielokrotnego użytku, które można dostosować lub zastąpić, aby zapewnić dodatkowe strategie zarządzania pamięcią.

Kontenery oparte na węzłach w C++ standardowej bibliotece (std:: list, std:: Set, std:: zestaw wielokrotny, std:: map i std:: multimap) przechowują elementy w poszczególnych węzłach. Wszystkie węzły dla określonego typu kontenera mają taki sam rozmiar, więc elastyczność Menedżera pamięci ogólnego przeznaczenia nie jest wymagana. Ponieważ rozmiar każdego bloku pamięci jest znany w czasie kompilacji, Menedżer pamięci może być znacznie prostszy i szybszy.

W przypadku używania z kontenerami, które nie są oparte na węzłach C++ (takich jak standardowe kontenery biblioteki std:: Vector std::d eque, i std:: basic_string), szablony alllocator będą działały prawidłowo, ale nie zapewniają zwiększenia wydajności domyślny Alokator.

Program przydzielający to szablon klasy, który opisuje obiekt, który zarządza alokacją pamięci masowej i zwalnia dla obiektów i tablic obiektów o wydzielonym typie. Obiekty alokatora są używane przez kilka szablonów klas kontenerów C++ w standardowej bibliotece.

Wszystkie szablony tego typu są następujące:

```cpp
template<class Type>
class allocator;
```

gdzie argument szablonu `Type` jest typem zarządzanym przez wystąpienie alokatora. Biblioteka C++ standardowa zawiera domyślnego alokatora [, który](../standard-library/allocator-class.md)jest zdefiniowany w [\<memory >](../standard-library/memory.md). Nagłówek \<allocators > zapewnia następujące przydzielenie:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Użyj odpowiedniego wystąpienia alokatora jako drugiego argumentu typu podczas tworzenia kontenera, takiego jak Poniższy przykład kodu.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 przydziela węzły z `allocator_chunklist` i domyślny filtr synchronizacji.

Użyj [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) makro, aby utworzyć szablony alokatora z filtrami synchronizacji inną niż domyślna:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 przydziela węzły z `allocator_chunklist` i filtru synchronizacji [sync_per_thread](../standard-library/sync-per-thread-class.md) .

Alokator bloku jest pamięcią podręczną lub filtrem. Pamięć podręczna to szablon klasy, który przyjmuje jeden argument typu std:: size_t. Definiuje program przydzielający blok, który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze. Musi on uzyskać pamięć przy użyciu operatora **New**, ale nie musi wykonywać osobnego wywołania operatora **New** dla każdego bloku. Może to być na przykład alokacja z większymi blokami lub alokacja pamięci podręcznej w celu kolejnej ponownej alokacji.

Kompilator, który nie może skompilować ponownie powiązać wartości argumentu std:: size_t użytego podczas tworzenia wystąpienia szablonu, nie musi być wartością argumentu _Sz przekazaną do funkcji składowych pamięci podręcznej alokacji i alokacji.

\<allocators > udostępnia następujące szablony pamięci podręcznej:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr jest przydziałem bloku, który implementuje funkcje składowe przy użyciu innego alokatora bloku, który jest przekazaniem do niego jako argument szablonu. Najbardziej typową formą filtru jest filtr synchronizacji, który stosuje zasady synchronizacji w celu kontrolowania dostępu do funkcji składowych wystąpienia innego alokatora blokowego. \<allocators > udostępnia następujące filtry synchronizacji:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators > udostępnia również filtr [rts_alloc](../standard-library/rts-alloc-class.md), który zawiera wiele wystąpień alokatora blokowego i określa, które wystąpienie ma być używane do alokacji lub cofania alokacji w czasie wykonywania, a nie podczas kompilowania. Jest on używany z kompilatorami, które nie mogą skompilować ponownie powiązania.

Zasady synchronizacji określają, jak wystąpienie alokatora obsługuje równoczesne alokacje i cofa alokacji z wielu wątków. Najprostszą zasadą jest przekazanie wszystkich żądań bezpośrednio do bazowego obiektu pamięci podręcznej, pozostawiając użytkownikowi Zarządzanie synchronizacją. Bardziej skomplikowane zasady mogą być używane do serializacji dostępu do bazowego obiektu pamięci podręcznej przy użyciu elementu mutex.

Jeśli kompilator obsługuje Kompilowanie aplikacji wielowątkowych i wielowątkowych, domyślny filtr synchronizacji dla aplikacji jednowątkowych jest `sync_none`; we wszystkich innych przypadkach jest `sync_shared`.

Szablon pamięci podręcznej `cache_freelist` przyjmuje argument Max Class, który określa maksymalną liczbę elementów, które mają być przechowywane na liście bezpłatnych.

\<allocators > oferuje następujące maksymalne klasy:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|Makro|Opis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Daje szablon klasy alokatora.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Daje `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Daje `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Daje `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Zwraca filtr synchronizacji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! = (\<allocators >)](../standard-library/allocators-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[operator = = (\<allocators >)](../standard-library/allocators-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definiuje klasę bazową i typowe funkcje, które są konieczne do utworzenia alokatora zdefiniowanego przez użytkownika z filtru synchronizacji.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów przy użyciu pamięci podręcznej typu [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_fixed_size](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje program przydzielający, który używa **operatora delete** do cofnięcia alokacji bloku pamięci i **operatora new** , aby przydzielić blok pamięci.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_suballoc](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_unbounded](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_variable_size](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definiuje Alokator bloku, który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definiuje Alokator bloku, który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definiuje Alokator bloku, który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.|
|[freelist](../standard-library/freelist-class.md)|Zarządza listą bloków pamięci.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Opisuje obiekt Max Class, który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do stałej maksymalnej długości.|
|[max_none](../standard-library/max-none-class.md)|Opisuje obiekt klasy maksymalnej, który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości równej zero.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Opisuje obiekt Max Class, który nie ogranicza maksymalnej długości obiektu [freelist](../standard-library/freelist-class.md) .|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Opisuje obiekt klasy maksymalnej, który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości, która jest w przybliżeniu proporcjonalna do liczby przydzielone bloków pamięci.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Szablon klasy rts_alloc opisuje [Filtr](../standard-library/allocators-header.md) , który przechowuje tablicę wystąpień pamięci podręcznej i określa, które wystąpienie ma być używane do alokacji i alokacji w czasie wykonywania, a nie podczas kompilowania.|
|[sync_none](../standard-library/sync-none-class.md)|Opisuje filtr synchronizacji, który nie zapewnia synchronizacji.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Opisuje filtr synchronizacji, który zawiera oddzielny obiekt pamięci podręcznej dla każdego obiektu alokatora.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Opisuje filtr synchronizacji, który zawiera oddzielny obiekt pamięci podręcznej dla każdego wątku.|
|[sync_shared](../standard-library/sync-shared-class.md)|Opisuje filtr synchronizacji, który używa elementu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkie przypisania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators >

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
