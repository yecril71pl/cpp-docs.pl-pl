---
title: "Namespace współbieżności (C++ AMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a9f82baade21cdbde41fc49fd0bfe6163c0f6af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-c-amp"></a>Przestrzeń nazw współbieżności (C++ AMP)
Zawiera klasy i funkcje, które przyspieszenie wykonywania kodu C++ na sprzęcie równoległe danych. Aby uzyskać więcej informacji, zobacz [Przegląd C++ AMP](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="namespaces"></a>Namespaces  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)|Udostępnia funkcje, które obsługują współdziałanie D3D. Umożliwia bezproblemowe na użytek D3D zasobów obliczeniowych w kodzie AMP i korzystania z zasobów utworzone w AMP w kodzie D3D bez tworzenia nadmiarowe kopie pośrednich. C++ AMP umożliwia przyrostowo przyspieszenia sekcje obliczeniowych aplikacji DirectX i na podstawie obliczenia AMP danych za pomocą interfejsu API D3D.|  
|[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)|Funkcje w `fast_math` nie są zgodnych C99 przestrzeni nazw. Podano tylko pojedynczej precyzji wersje każdej funkcji. Funkcje wewnętrzne DirectX, które są szybsze niż w odpowiednie funkcje używać tych funkcji `precise_math` przestrzeni nazw i nie wymagają rozszerzoną obsługę podwójnej precyzji na akceleratora, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji poziomu zgodności z kodem C99; obie wersje przyjmować i zwracać wartości o pojedynczej precyzji.|  
|[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)|Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.|  
|[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)|Funkcje w `precise_math` zgodnych C99 są przestrzeni nazw. Zarówno pojedynczej precyzji, jak i podwójnej precyzji wersje każdej funkcji są uwzględniane. Te funkcje — dotyczy to również funkcje pojedynczej precyzji — wymagają rozszerzoną obsługę podwójnej precyzji na akceleratora.|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accelerator, klasa](accelerator-class.md)|Reprezentuje abstrakcję węzła fizycznego obliczeń zoptymalizowanych pod kątem punktu dystrybucji.|  
|[accelerator_view, klasa](accelerator-view-class.md)|Reprezentuje abstrakcji urządzenia wirtualnego na akceleratora równoległe danych C++ AMP.|  
|[accelerator_view_removed, klasa](accelerator-view-removed-class.md)|Wyjątek zgłaszany, gdy podstawowy wywołań programu DirectX zakończy się niepowodzeniem z powodu mechanizmu limit czasu wykrywania i odzyskiwania systemu Windows.|  
|[array, klasa](array-class.md)|Łączny na danych `accelerator_view` w domenie siatce. Jest to zbiór zmienne, jedną dla każdego elementu w domenie siatce. Każda zmienna przechowuje wartość, która odpowiada niektórych typów języka C++.|  
|[array_view, klasa](array-view-class.md)|Reprezentuje zapewnia wgląd w dane w tablicy\<T, N >.|  
|[completion_future, klasa](completion-future-class.md)|Reprezentuje przyszłe, która odpowiada C++ AMP operację asynchroniczną.|  
|[extent, klasa](extent-class.md)|Reprezentuje wektor N liczby całkowitej wartości, które określają granice przestrzeni trójwymiarowej N, zawierający początek 0. Wartości w przypadku wektora współrzędnych są uporządkowane od najważniejszych do najmniej znaczący. Na przykład kartezjańskimi 3-wymiarową miejsca, vector zakresu (7,5,3) reprezentuje miejsca, w którym Współrzędna z zakresu od 0 do 7, y współrzędnych w zakresie od 0 do 5, a współrzędna x zakresu od 0 do 3.|  
|[index, klasa](index-class.md)|Definiuje N-wymiarowej punkt indeksu.|  
|[invalid_compute_domain, klasa](invalid-compute-domain-class.md)|Wyjątek zgłaszany, gdy środowisko uruchomieniowe nie może uruchomić jądra przy użyciu określonych w domenie obliczeniowej `parallel_for_each` wywołania.|  
|[out_of_memory, klasa](out-of-memory-class.md)|Wyjątek zgłaszany, gdy metoda kończy się niepowodzeniem z powodu braku pamięci systemu lub urządzenia.|  
|[runtime_exception, klasa](runtime-exception-class.md)|Typ podstawowy dla wyjątków w bibliotece C++ AMP.|  
|[tile_barrier, klasa](tile-barrier-class.md)|Klasy funkcji jest tylko możliwość utworzenia przez system, który jest przekazywany do sąsiadującym `parallel_for_each` lambda jako część `tiled_index` parametru. Zapewnia jedną metodę `wait()`, których celem jest synchronizowanie wykonywania wątków, które są uruchomione w grupie wątku (kafelka).|  
|[tiled_extent, klasa](tiled-extent-class.md)|A `tiled_extent` obiekt jest `extent` obiektu wymiarów jednej do trzech dzielący miejsca zakres do jednowymiarowa, dwuwymiarowa lub trójwymiarowy Kafelki.|  
|[tiled_index, klasa](tiled-index-class.md)|Zapewnia to indeks w `tiled_grid` obiektu. Ta klasa ma właściwości, które mają dostęp element pokrewny ze źródłem Kafelek lokalnego i pokrewne ze źródłem globalnego.|  
|[uninitialized_object, klasa](uninitialized-object-class.md)|Wyjątek zgłaszany, gdy jest używany niezainicjowanego obiektu.|  
|[unsupported_feature, klasa](unsupported-feature-class.md)|Wyjątek zgłaszany, gdy jest używany nieobsługiwanej funkcji.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[access_type — wyliczenie](concurrency-namespace-enums-amp.md#access_type)|Określa typ dostępu do danych.|  
|[queuing_mode — wyliczenie](concurrency-namespace-enums-amp.md#queuing_mode)|Określa kolejkowania tryby, które są obsługiwane na akceleratora.|  
  
### <a name="operators"></a>Operatory  
  
|Operator|Opis|  
|--------------|-----------------|  
|[operator == — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Określa, czy określone dane struktury są takie same.|  
|[operator! = — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Określa, czy struktury określone dane nie są równe.|  
|[operator + — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Oblicza sumę component-wise określonych argumentów.|  
|[operator-— Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Oblicza component-wise różnica między określonymi argumentami.|  
|[operator * — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Oblicza iloczyn component-wise określonych argumentów.|  
|[operator / — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Oblicza iloraz component-wise określonych argumentów.|  
|[operator % — Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Oblicza resztę pierwszy argument określony przez drugi określonego argumentu.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Wykonanie bloki wszystkie wątki na kafelku ukończenie wszystkich uzyskuje dostęp do pamięci.|  
|[amp_uninitialize —](concurrency-namespace-functions-amp.md#amp_uninitialize)|Uninitializes środowiska uruchomieniowego C++ AMP.|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Przeciążone. Jeśli wartość przechowywana we wskazanej lokalizacji porównuje pierwszy określonej wartości, drugi określona wartość jest przechowywane w tej samej lokalizacji co niepodzielną operację.|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji do określonej wartości jako operacją niepodzielną.|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji do sumę tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji wartości bitowych `and` tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Przeciążone. Zmniejsza wartości przechowywane w określonej lokalizacji i zapisuje wynik w tej samej lokalizacji co niepodzielną operację.|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Przeciążone. Zwiększa wartość przechowywana we wskazanej lokalizacji i zapisuje wynik w tej samej lokalizacji co niepodzielną operację.|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji do większy tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji do mniejszego tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji wartości bitowych `or` tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji różnicy tę wartość i określoną wartość jako operacją niepodzielną.|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Przeciążone. Ustawia wartość przechowywana we wskazanej lokalizacji wartości bitowych `xor` tę wartość i określoną wartość jako operacją niepodzielną.|  
|[copy](concurrency-namespace-functions-amp.md#copy)|Kopiuje obiekt C++ AMP. Spełniono wszystkie wymagania transferu danych synchroniczne. Nie można skopiować danych, gdy kod działa kod z akceleratora. Formularz ogólny tej funkcji jest `copy(src, dest)`.|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Kopiuje obiekt C++ AMP i zwraca [completion_future](completion-future-class.md) który mogą być obsługiwane. Nie można skopiować danych, gdy kod działa z akceleratora. Formularz ogólny tej funkcji jest `copy(src, dest)`.|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Przerywa wykonywanie funkcji, która ma `restrict(amp)` Klauzula ograniczenia.|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Wyświetla ciąg formatowania do programu Visual Studio **dane wyjściowe** okno i zgłasza [runtime_exception —](runtime-exception-class.md) wyjątek, który ma tego samego formatowania ciągu.|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Wyświetla ciąg formatowania do programu Visual Studio **dane wyjściowe** okna. Jest ona wywoływana z funkcji, która ma `restrict(amp)` Klauzula ograniczenia.|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Bloki wykonywanie wszystkich wątków na kafelku, dopóki wszystkie pamięci globalnej uzyskuje dostęp do zostały zakończone.|  
|[parallel_for_each — funkcja (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Funkcja znajduje się w domenie obliczeniowej.|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blokuje wykonywanie wszystkich wątków na kafelku do `tile_static` uzyskuje dostęp do pamięci zostały ukończone.|  
  
## <a name="constants"></a>Stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Hlsl_max_num_buffers — stała](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maksymalna liczba buforów dozwoloną DirectX.|  
|[Modulename_max_length — stała](concurrency-namespace-constants-amp.md#modulename_max_length)|Przechowuje maksymalna długość nazwy modułu. Ta wartość musi być taka sama na kompilatora i środowiska uruchomieniowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja (C++ AMP)](reference-cpp-amp.md)



