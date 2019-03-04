---
title: Przestrzeń nazw współbieżności (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: e0870eb046f1cec091a72d49c94a2fea41484340
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278694"
---
# <a name="concurrency-namespace-c-amp"></a>Przestrzeń nazw współbieżności (C++ AMP)

Zawiera klasy i funkcje, które przyspieszają wykonywanie kodu C++ na urządzeniach równoległych danych. Aby uzyskać więcej informacji, zobacz [Przegląd C++ AMP](../cpp-amp-overview.md)

## <a name="syntax"></a>Składnia

```
namespace Concurrency;
```

## <a name="members"></a>Elementy członkowskie

### <a name="namespaces"></a>Namespaces

|Nazwa|Opis|
|----------|-----------------|
|[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)|Oferuje funkcje, które obsługują współdziałanie D3D. Umożliwia bezproblemowe korzystanie z zasobów D3D dla obliczeń w kodzie AMP i wykorzystanie zasobów utworzonych w AMP, w kodzie D3D, bez tworzenia nadmiarowych kopii pośrednich. Można użyć C++ AMP, aby stopniowo przyspieszyć sekcje intensywnych obliczeń aplikacji DirectX i użyć interfejsu API D3D na danych wyprodukowanych z obliczeń AMP.|
|[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)|Funkcje w `fast_math` przestrzeni nazw nie są zgodne z C99. Podano tylko pojedynczej precyzji wersje każdej funkcji. Te funkcje używają wewnętrznych funkcji DirectX, które są szybsze od odpowiednich funkcji w `precise_math` przestrzeni nazw i nie wymagają rozszerzonego wsparcia podwójnej precyzji na akceleratorze, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji dla zgodności poziomu źródła z kodem C99; obie wersje przyjmują i zwracają wartości pojedynczej precyzji.|
|[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)|Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.|
|[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)|Funkcje w `precise_math` przestrzeni nazw są zgodne z C99. Uwzględniono pojedynczej precyzji, jak i podwójną precyzją wersje każdej funkcji. Te funkcje — w tym funkcje pojedynczej precyzji — wymagają rozszerzonej obsługi podwójnej precyzji na akceleratorze.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[accelerator, klasa](accelerator-class.md)|Reprezentuje klasą abstrakcyjną węzła obliczeniowego zoptymalizowanego pod kątem DP fizycznych.|
|[accelerator_view, klasa](accelerator-view-class.md)|Reprezentuje abstrakcję urządzenia wirtualnego na akceleratorze danych równoległych C++ AMP.|
|[accelerator_view_removed, klasa](accelerator-view-removed-class.md)|Wyjątek, który jest generowany, kiedy wywołanie DirectX nie powiedzie się z powodu Windows limit czasu — wykrywanie — i mechanizm odzyskiwania.|
|[array, klasa](array-class.md)|Agregacją danych na `accelerator_view` w domenie siatki. Jest to zbiór zmiennych, jeden dla każdego elementu w domenie siatki. Każda zmienna przechowuje wartość odpowiadającą typowi C++.|
|[array_view, klasa](array-view-class.md)|Reprezentuje widok danych w tablicy\<T, N >.|
|[completion_future, klasa](completion-future-class.md)|Reprezentuje stan w przyszłości, który odpowiada na operację asynchroniczną C++ AMP.|
|[extent, klasa](extent-class.md)|Reprezentuje wektor N wartości całkowitych, które określają granice przestrzeni N-wymiarowej, która pochodzi od 0. Wartości w wektorze współrzędnych są uporządkowane od najbardziej do najmniej znaczących. Na przykład w Kartezjańskiego 3-wymiarowej przestrzeni wektor zakresu (7,5,3) reprezentuje miejsca, w której Współrzędna z jest z zakresu od 0 do 7, współrzędna y z zakresu od 0 do 5, a współrzędna x zakresu od 0 do 3.|
|[index, klasa](index-class.md)|Definiuje N-wymiarowy punkt indeksu.|
|[invalid_compute_domain, klasa](invalid-compute-domain-class.md)|Wyjątek, który jest zgłaszany, gdy środowisko uruchomieniowe nie może uruchomić jądra używając domeny obliczeniowej określonej w `parallel_for_each` wywołania.|
|[out_of_memory, klasa](out-of-memory-class.md)|Wyjątek, który jest zgłaszany, gdy metoda nie powiedzie się z powodu braku pamięci systemowej lub urządzenia.|
|[runtime_exception, klasa](runtime-exception-class.md)|Typ podstawowy dla wyjątków w bibliotece C++ AMP.|
|[tile_barrier, klasa](tile-barrier-class.md)|Klasa możliwości, która jest tylko możliwość utworzenia przez system i jest przekazywana do sąsiadującej `parallel_for_each` lambda jako część `tiled_index` parametru. Udostępnia pojedynczą metodę `wait()`, których celem jest synchronizowanie wykonywania wątków działających w grupie wątku (fragment).|
|[tiled_extent, klasa](tiled-extent-class.md)|A `tiled_extent` obiekt jest `extent` obiektu jednego do trzech wymiarów, dzielący przestrzeń na jednowymiarowy lub trójwymiarowe fragmenty.|
|[tiled_index, klasa](tiled-index-class.md)|Dostarcza indeks `tiled_grid` obiektu. Ta klasa posiada właściwości, które umożliwiają dostęp do elementu względem lokalnego fragmentu i pokrewny ze źródłem globalnego.|
|[uninitialized_object, klasa](uninitialized-object-class.md)|Wyjątek, który jest zgłaszany, gdy używany jest obiekt niezainicjowany.|
|[unsupported_feature, klasa](unsupported-feature-class.md)|Wyjątek, który jest zgłaszany, gdy używana jest nieobsługiwana funkcja.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[access_type Enumeration](concurrency-namespace-enums-amp.md#access_type)|Określa typ dostępu do danych.|
|[queuing_mode Enumeration](concurrency-namespace-enums-amp.md#queuing_mode)|Określa tryby kolejkowania, które są obsługiwane w akceleratorze.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|--------------|-----------------|
|[operator == — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Określa, czy określone struktury danych są takie same.|
|[operator! = — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Określa, czy określone struktury danych są nierówne.|
|[operator + — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Oblicza sumę dotyczącą składnika dla określonych argumentów.|
|[operator-— Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Oblicza różnicę dotyczącą składnika między określonymi argumentami.|
|[operator * — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Oblicza iloczyn dotyczący składnika dla określonych argumentów.|
|[operator / — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Oblicza iloraz dotyczący składnika dla określonych argumentów.|
|[operator % — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Oblicza moduł pierwszego określonego argumentu przez drugi określony argument.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich dostępów do pamięci.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Deinicjuje środowisko wykonawcze C++ AMP.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Przeciążone. Jeśli wartość przechowywaną w określonej lokalizacji w porównaniu równa pierwszej określonej wartości, druga określona wartość jest przechowywane w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na określoną wartość jako operację niepodzielną.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla sumy tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji do bitowej `and` tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Przeciążone. Zmniejsza wartość przechowywaną w określonej lokalizacji i zapisuje wynik w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Przeciążone. Zwiększa wartość przechowywaną w określonej lokalizacji i zapisuje wynik w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla większej tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla mniejszej tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji do bitowej `or` tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na różnicę tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji do bitowej `xor` tej wartości i określoną wartość jako operację niepodzielną.|
|[Kopiuj](concurrency-namespace-functions-amp.md#copy)|Kopiuje obiekt C++ AMP. Spełnione są wszystkie wymagania synchronicznego transferu danych. Nie można skopiować danych, gdy kod jest kodem wykonywanym na akceleratorze. Ogólna postać tej funkcji jest `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Kopiuje obiekt C++ AMP i zwraca [completion_future](completion-future-class.md) , może być oczekiwany. Nie można skopiować danych, gdy kod jest wykonywany na akceleratorze. Ogólna postać tej funkcji jest `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Przerywa wykonywanie funkcji, która ma `restrict(amp)` klauzulą ograniczenia.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Drukuje sformatowany ciąg do programu Visual Studio **dane wyjściowe** okna i zgłasza [runtime_exception](runtime-exception-class.md) wyjątek, który ma ten sam formatowanie ciągu.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Drukuje sformatowany ciąg do programu Visual Studio **dane wyjściowe** okna. Jest wywoływane z funkcji, która ma `restrict(amp)` klauzulą ograniczenia.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie do momentu dostępów do pamięci globalnej wszystkie zostały zakończone.|
|[parallel_for_each — funkcja (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Uruchamia funkcję w całej domenie obliczeń.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie, aż `tile_static` dostępy do pamięci zostały ukończone.|

## <a name="constants"></a>Stałe

|Nazwa|Opis|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS Constant](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maksymalna liczba buforów dozwolona przez DirectX.|
|[MODULENAME_MAX_LENGTH Constant](concurrency-namespace-constants-amp.md#modulename_max_length)|Przechowuje maksymalną długość nazwy modułu. Ta wartość musi być taka sama w kompilatorze i środowiska uruchomieniowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

## <a name="see-also"></a>Zobacz także

[Dokumentacja (C++ AMP)](reference-cpp-amp.md)
