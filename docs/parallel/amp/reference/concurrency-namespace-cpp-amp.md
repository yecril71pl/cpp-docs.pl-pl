---
title: Przestrzeń nazw współbieżności (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139373"
---
# <a name="concurrency-namespace-c-amp"></a>Przestrzeń nazw współbieżności (C++ AMP)

Dostarcza klasy i funkcje, które przyspieszają wykonywanie C++ kodu na urządzeniach równoległych danych. Aby uzyskać więcej informacji, zobacz [ C++ amp — Omówienie](../cpp-amp-overview.md)

## <a name="syntax"></a>Składnia

```cpp
namespace Concurrency;
```

## <a name="members"></a>Members

### <a name="namespaces"></a>Przestrzenie nazw

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)|Udostępnia funkcje, które obsługują współdziałanie D3D. Pozwala bezproblemowo korzystać z zasobów D3D do obliczeń w kodzie AMP i używania zasobów utworzonych w AMP w kodzie D3D, bez tworzenia nadmiarowych kopii pośrednich. Możesz użyć C++ amp, aby stopniowo przyspieszyć sekcje aplikacji DirectX intensywnie korzystających z mocy obliczeniowej i użyć interfejsu API D3D na danych wyprodukowanych z obliczeń amp.|
|[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)|Funkcje w przestrzeni nazw `fast_math` nie są zgodne z C99. Udostępniane są tylko wersje o pojedynczej precyzji każdej funkcji. Te funkcje używają funkcji wewnętrznych DirectX, które są szybsze niż odpowiednie funkcje w przestrzeni nazw `precise_math` i nie wymagają rozszerzonej obsługi podwójnej precyzji dla akceleratora, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji dla zgodności na poziomie źródła z kodem C99; Obie wersje pobierają i zwracają wartości pojedynczej precyzji.|
|[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)|Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.|
|[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)|Funkcje w przestrzeni nazw `precise_math` są zgodne z C99. Dostępne są zarówno wersje o pojedynczej precyzji, jak i podwójnej precyzji każdej funkcji. Te funkcje — obejmuje funkcje o pojedynczej precyzji — wymagają rozszerzonej obsługi podwójnej precyzji dla akceleratora.|

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accelerator, klasa](accelerator-class.md)|Reprezentuje abstrakcję fizycznego węzła obliczeniowego zoptymalizowanego pod kątem DP.|
|[accelerator_view, klasa](accelerator-view-class.md)|Reprezentuje abstrakcję urządzenia wirtualnego w akceleratorze C++ danych amp-równoległym.|
|[accelerator_view_removed, klasa](accelerator-view-removed-class.md)|Wyjątek, który jest generowany, gdy bazowe wywołanie programu DirectX nie powiedzie się z powodu przekroczenia limitu czasu systemu Windows — wykrywania i odzyskiwania.|
|[array, klasa](array-class.md)|Agregowanie danych na `accelerator_view` w domenie siatki. Jest to zbiór zmiennych, po jednym dla każdego elementu w domenie siatki. Każda zmienna przechowuje wartość odpowiadającą C++ typowi typu.|
|[array_view, klasa](array-view-class.md)|Reprezentuje widok danych w tablicy\<T, N >.|
|[completion_future, klasa](completion-future-class.md)|Reprezentuje przyszłość, która odnosi się do C++ operacji asynchronicznej amp.|
|[extent, klasa](extent-class.md)|Reprezentuje wektora N wartości całkowitych, które określają granice przestrzeni N-wymiarowej, która ma początek 0. Wartości w wektorze współrzędnych są uporządkowane od najbardziej do najmniej znaczących. Na przykład w kartezjańskiego trójwymiarowej przestrzeni wektor zakresu (7, 5, 3) reprezentuje miejsce, w którym Współrzędna z przedziału od 0 do 7, Współrzędna y z zakresu od 0 do 5, a Współrzędna x z przedziału od 0 do 3.|
|[index, klasa](index-class.md)|Definiuje N-wymiarowy punkt indeksu.|
|[invalid_compute_domain, klasa](invalid-compute-domain-class.md)|Wyjątek, który jest generowany, gdy środowisko uruchomieniowe nie może uruchomić jądra przy użyciu domeny obliczeniowej określonej w lokacji wywołania `parallel_for_each`.|
|[out_of_memory, klasa](out-of-memory-class.md)|Wyjątek, który jest generowany, gdy metoda nie powiedzie się z powodu braku pamięci systemowej lub urządzenia.|
|[runtime_exception, klasa](runtime-exception-class.md)|Typ podstawowy dla wyjątków w bibliotece C++ amp.|
|[tile_barrier, klasa](tile-barrier-class.md)|Klasa możliwości, która jest tylko do utworzenia przez system i jest przenoszona do sąsiadujących `parallel_for_each` lambda jako część parametru `tiled_index`. Zapewnia jedną metodę, `wait()`, której celem jest synchronizowanie wykonywania wątków, które są uruchomione w grupie wątków (kafelek).|
|[tiled_extent, klasa](tiled-extent-class.md)|Obiekt `tiled_extent` jest obiektem `extent` od jednego do trzech wymiarów dzielących obszar zakresu na jednowymiarowe, dwuwymiarowe lub trójwymiarowe kafelki.|
|[tiled_index, klasa](tiled-index-class.md)|Zapewnia indeks w obiekcie `tiled_grid`. Ta klasa ma właściwości do uzyskiwania dostępu do elementu względem lokalnego źródła kafelka i względem pierwotnego źródła.|
|[uninitialized_object, klasa](uninitialized-object-class.md)|Wyjątek, który jest generowany, gdy jest używany Niezainicjowany obiekt.|
|[unsupported_feature, klasa](unsupported-feature-class.md)|Wyjątek, który jest generowany w przypadku użycia nieobsługiwanej funkcji.|

### <a name="enumerations"></a>Wyliczenia

|Name (Nazwa)|Opis|
|----------|-----------------|
|[access_type, Wyliczenie](concurrency-namespace-enums-amp.md#access_type)|Określa typ dostępu do danych.|
|[queuing_mode, Wyliczenie](concurrency-namespace-enums-amp.md#queuing_mode)|Określa tryby kolejkowania, które są obsługiwane w akceleratorze.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|--------------|-----------------|
|[operator = = — operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Określa, czy określone struktury danych są równe.|
|[operator! = — operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_neq)|Określa, czy określone struktury danych są nierówne.|
|[operator + — operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_add)|Oblicza sumę elementów dla określonych argumentów.|
|[operator-— operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator-)|Oblicza różnicę składnika między określonymi argumentami.|
|[operator * — operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_star)|Oblicza produkt ze składnikami dla określonych argumentów.|
|[operator/— operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_div)|Oblicza iloraz składnika dla określonych argumentów.|
|[operator% — operatorC++ (amp)](concurrency-namespace-operators-amp.md#operator_mod)|Oblicza moduł pierwszego określonego argumentu przez drugi określony argument.|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich operacji dostępu do pamięci.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Odinicjuje środowisko uruchomieniowe C++ amp.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Przeciążone. Jeśli wartość przechowywana w określonej lokalizacji jest porównywana równa pierwszej określonej wartości, druga określona wartość jest przechowywana w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na określoną wartość jako operację niepodzielną.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na sumę tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla `and` bitowej tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Przeciążone. Zmniejsza wartość przechowywaną w określonej lokalizacji i zapisuje wynik w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Przeciążone. Zwiększa wartość przechowywaną w określonej lokalizacji i zapisuje wynik w tej samej lokalizacji co operacja niepodzielna.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji do większej tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na mniejszą wartość i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla `or` bitowej tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji na różnicę tej wartości i określoną wartość jako operację niepodzielną.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Przeciążone. Ustawia wartość przechowywaną w określonej lokalizacji dla `xor` bitowej tej wartości i określoną wartość jako operację niepodzielną.|
|[kopiowane](concurrency-namespace-functions-amp.md#copy)|Kopiuje obiekt C++ amp. Spełnione są wszystkie wymagania dotyczące synchronicznego transferu danych. Nie można skopiować danych, gdy kod uruchamia kod na akceleratorze. Ogólna forma tej funkcji jest `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Kopiuje obiekt C++ amp i zwraca [completion_future](completion-future-class.md) , które mogą być oczekiwane. Nie można skopiować danych, gdy kod jest uruchomiony na akceleratorze. Ogólna forma tej funkcji jest `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Przerywa wykonywanie funkcji z klauzulą ograniczenia `restrict(amp)`.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Drukuje sformatowany ciąg w oknie **danych wyjściowych** programu Visual Studio i wywołuje [runtime_exception](runtime-exception-class.md) wyjątek, który ma ten sam ciąg formatowania.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Drukuje sformatowany ciąg w oknie **danych wyjściowych** programu Visual Studio. Jest wywoływana z funkcji, która ma `restrict(amp)` klauzulę ograniczenia.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Blokuje wykonywanie wszystkich wątków w kafelku do momentu zakończenia wszystkich dostępów do pamięci globalnej.|
|[Funkcja parallel_for_each (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each)|Uruchamia funkcję w całej domenie obliczeniowej.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blokuje wykonanie wszystkich wątków w kafelku do momentu ukończenia `tile_static` dostępu do pamięci.|

## <a name="constants"></a>{1&gt;Stałe&lt;1}

|Name (Nazwa)|Opis|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS stała](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maksymalna liczba buforów dozwolona przez program DirectX.|
|[MODULENAME_MAX_LENGTH stała](concurrency-namespace-constants-amp.md#modulename_max_length)|Przechowuje maksymalną długość nazwy modułu. Ta wartość musi być taka sama w kompilatorze i środowisku uruchomieniowym.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

## <a name="see-also"></a>Zobacz też

[Dokumentacja (C++ AMP)](reference-cpp-amp.md)
