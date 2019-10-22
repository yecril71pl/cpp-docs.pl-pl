---
title: '&lt;memory &gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 4a6383ee94d021373b984122926a5bb73e18f953
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689365"
---
# <a name="ltmemorygt"></a>&lt;memory &gt;

Określa klasę, operator i kilka szablonów, które pomagają przydzielać i zwalniać obiekty.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<memory >

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|||
|-|-|
|[AddressOf](../standard-library/memory-functions.md#addressof)|Pobiera prawdziwy adres obiektu.|
|[align](../standard-library/memory-functions.md#align)|Zwraca wskaźnik do zakresu o podanej wielkości, na podstawie podanego wyrównania i adresu początkowego.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Tworzy `shared_ptr` do obiektów, które są przydzielane i skonstruowane dla danego typu przy użyciu określonego alokatora.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Rzutowanie const na `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje moduł odśmiecający pamięci, że znaki, począwszy od określonego adresu i objęte rozmiarem bloku, nie zawierają wskaźników mogących podlegać śledzeniu.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Usuwa obiekty przydzielono do `operator new`. Odpowiednie do użycia z `unique_ptr`.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|Skrót `destroy` metody.|
|[usunięcie](../standard-library/memory-functions.md#destroy)|Skrót `destroy` metody.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|Skrót `destroy` metody.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamiczne rzutowanie na `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Pobierz usuwanie z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Zwraca typ bezpieczeństwa wskaźnika założony przez dowolny moduł odśmiecania pamięci.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Przydziela tymczasową pamięć dla sekwencji elementów, która nie przekracza określonej liczby elementów.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Tworzy i zwraca `shared_ptr` wskazujące przydzieloną obiekt skonstruowany z zero lub więcej argumentów przy użyciu domyślnego alokatora.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Tworzy i zwraca [unique_ptr](../standard-library/unique-ptr-class.md) , który wskazuje na przydzieloną obiekt skonstruowany z zero lub więcej argumentów.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Wyliczenie wszystkich możliwych wartości zwracanych dla `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zwalnia pamięć tymczasową, która została przydzielona za pomocą funkcji szablonu `get_temporary_buffer`.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statyczne rzutowanie na `shared_ptr`.|
|[wymiany](../standard-library/memory-functions.md#swap)|Zamień dwa `shared_ptr` lub `weak_ptr` obiekty.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje `garbage_collector`, że określona lokalizacja pamięci jest nieosiągalna.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Kopiuje obiekty z określonego zakresu wejściowego do niezainicjowanego zakresu docelowego.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Tworzy kopię określonej liczby elementów z iteratora danych wejściowych. Kopie są wprowadzane do iteratora do przodu.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|Skrót `uninitialized_default_construct` metody.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|Skrót `uninitialized_construct` metody.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Kopiuje obiekty z określoną wartością do niezainicjowanego zakresu docelowego.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Kopiuje obiekty z określoną wartością do określonej liczby elementów niezainicjowanego zakresu docelowego.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|Skrót `uninitialized_move` metody.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|Skrót `uninitialized_move` metody.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|Skrót `uninitialized_value_construct` metody.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|Skrót `uninitialized_value_construct` metody.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[operator = =](../standard-library/memory-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testuje, czy jeden obiekt alokatora jest większy niż lub równy drugiemu obiektowi alokatora określonej klasy.|
|[< operatora](../standard-library/memory-operators.md#op_lt)|Testuje, czy jeden obiekt jest mniejszy niż drugi obiekt określonej klasy.|
|[\< operatora =](../standard-library/memory-operators.md#op_gt_eq)|Testuje, czy jeden obiekt jest mniejszy niż lub równy drugiemu obiektowi określonej klasy.|
|[> operatora](../standard-library/memory-operators.md#op_gt)|Testuje, czy jeden obiekt jest większy niż drugi obiekt określonej klasy.|
|[< operatora <](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` wstawer.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|Szablon klasy opisuje obiekt, który zarządza alokacją magazynu i zwalnia dla tablic **obiektów typu typ.**|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Opisuje obiekt określający wszystkie informacje, które są wymagane przez kontener z obsługą alokatora.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Szablon klasy opisuje obiekt, który przechowuje wskaźnik do przydzielony obiekt **typu typu** <strong>\*</strong> , który zapewnia, że obiekt, do którego wskazuje, zostaje usunięty po usunięciu otaczających auto_ptr.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Zgłasza zły wyjątek weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomaga wygenerować `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Dostarcza informacje, które są konieczne przez obiekt typu `allocator_traits` do opisania alokatora z typem wskaźnika `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Klasa adaptera, która jest dostarczana, aby umożliwić algorytmom zapisywanie ich wyników do pamięci niezainicjowanej.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Otacza inteligentny wskaźnik zliczonych odwołań wokół obiektu przydzielanego dynamicznie.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Przechowuje wskaźnik do posiadanego obiektu. Wskaźnik nie jest własnością żadnego innego `unique_ptr`. @No__t_0 jest niszczony, gdy właściciel zostanie zniszczony.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Otacza słabo połączony wskaźnik.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|Zapewnia przeciążenia wyspecjalizowane dla `unique_ptr` i `shared_ptr`.|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[Alokator \<void >](../standard-library/allocator-void-class.md)|Specjalizacja alokatora szablonu klasy do typu **void**, definiująca tylko typy elementów członkowskich, które mają sens w tym wyspecjalizowanym kontekście.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
