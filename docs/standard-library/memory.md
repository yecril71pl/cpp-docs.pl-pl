---
title: '&lt;Pamięć&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
dev_langs:
- C++
helpviewer_keywords:
- memory header
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b90a96816855e08610d0f63f3ab5c237d564453
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217952"
---
# <a name="ltmemorygt"></a>&lt;Pamięć&gt;

Określa klasę, operator i kilka szablonów, które pomagają przydzielać i zwalniać obiekty.

## <a name="syntax"></a>Składnia

```cpp
#include <memory>

```

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[AddressOf](../standard-library/memory-functions.md#addressof)|Pobiera prawdziwy adres obiektu.|
|[align](../standard-library/memory-functions.md#align)|Zwraca wskaźnik do zakresu o podanej wielkości, na podstawie podanego wyrównania i adresu początkowego.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Tworzy `shared_ptr` do obiektów, które są przydzielane i zbudowane dla danego typu przy użyciu określonego alokatora.|
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Rzutowanie stałe na `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje moduł odśmiecający pamięci, że znaki, począwszy od określonego adresu i objęte rozmiarem bloku, nie zawierają wskaźników mogących podlegać śledzeniu.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Usuwa obiekty przydzielone za pomocą `operator new`. Odpowiedni do użytku z `unique_ptr`.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Rzutowanie dynamiczne na `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Pobieranie programu usuwającego z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Zwraca typ bezpieczeństwa wskaźnika założony przez dowolny moduł odśmiecania pamięci.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Przydziela tymczasową pamięć dla sekwencji elementów, która nie przekracza określonej liczby elementów.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Tworzy i zwraca `shared_ptr` który wskazuje na przydzielony obiekt skonstruowany z zera lub więcej argumentów za pomocą domyślnego alokatora.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Tworzy i zwraca [unique_ptr](../standard-library/unique-ptr-class.md) który wskazuje na przydzielony obiekt skonstruowany z zera lub więcej argumentów.|
|[owner_less —](../standard-library/memory-functions.md#owner_less)|Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Wyliczenie wszystkich możliwych wartości zwracanych dla `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zwalnia pamięć tymczasową, która została przydzielona za pomocą `get_temporary_buffer` funkcji szablonu.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Rzutowanie statyczne na `shared_ptr`.|
|[swap](../standard-library/memory-functions.md#swap)|Zamienia dwa `shared_ptr` lub `weak_ptr` obiektów.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje `garbage_collector` określona lokalizacja w pamięci nie jest dostępny.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Kopiuje obiekty z określonego zakresu wejściowego do niezainicjowanego zakresu docelowego.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Tworzy kopię określonej liczby elementów z iteratora danych wejściowych. Kopie są wprowadzane do iteratora do przodu.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Kopiuje obiekty z określoną wartością do niezainicjowanego zakresu docelowego.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Kopiuje obiekty z określoną wartością do określonej liczby elementów niezainicjowanego zakresu docelowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testuje, czy jeden obiekt alokatora jest większy niż lub równy drugiemu obiektowi alokatora określonej klasy.|
|[Operator <](../standard-library/memory-operators.md#op_lt)|Testuje, czy jeden obiekt jest mniejszy niż drugi obiekt określonej klasy.|
|[Operator\<=](../standard-library/memory-operators.md#op_gt_eq)|Testuje, czy jeden obiekt jest mniejszy niż lub równy drugiemu obiektowi określonej klasy.|
|[operator>](../standard-library/memory-operators.md#op_gt)|Testuje, czy jeden obiekt jest większy niż drugi obiekt określonej klasy.|
|[Operator <<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` inserter.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[allocator](../standard-library/allocator-class.md)|Klasa szablonu opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla tablic obiektów typu **typu**.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Opisuje obiekt określający wszystkie informacje, które są wymagane przez kontener z obsługą alokatora.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Klasa szablonu opisuje obiekt przechowujący wskaźnik do przydzielonego obiektu typu **typu** <strong>\*</strong> który zapewnia, że obiekt, do których się punkty zostaje usunięty po zniszczeniu jego otaczającego auto_ptr pobiera zniszczone.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Zgłasza zły wyjątek weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Ułatwia generowanie `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Dostarcza informacje, które są wymagane przez obiekt klasy szablonu `allocator_traits` do opisania alokatora z typem wskaźnika `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Klasa adaptera, która jest dostarczana, aby umożliwić algorytmom zapisywanie ich wyników do pamięci niezainicjowanej.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Otacza inteligentny wskaźnik zliczonych odwołań wokół obiektu przydzielanego dynamicznie.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Przechowuje wskaźnik do posiadanego obiektu. Wskaźnik jest własnością żadnego innego `unique_ptr`. `unique_ptr` Jest niszczony, kiedy niszczony jest właściciel.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Otacza słabo połączony wskaźnik.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|Specjalizacja alokatora klasy szablonu do typu void, definiująca tylko typy składowych, które mają sens w tym wyspecjalizowanym kontekście.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
