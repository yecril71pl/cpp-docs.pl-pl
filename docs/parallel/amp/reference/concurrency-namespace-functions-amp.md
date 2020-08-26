---
title: Funkcje przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: b03a6189d2205dff62d94f07bc597ca2e1013a28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840209"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkcje przestrzeni nazw współbieżności (AMP)

:::row:::
   :::column span="":::
      [`all_memory_fence`](#all_memory_fence)\
      [`amp_uninitialize`](#amp_uninitialize)\
      [`atomic_compare_exchange`](#atomic_compare_exchange)\
      [`atomic_exchange`](#atomic_exchange)\
      [`atomic_fetch_add`](#atomic_fetch_add)\
      [`atomic_fetch_and`](#atomic_fetch_and)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_dec`](#atomic_fetch_dec)\
      [`atomic_fetch_inc`](#atomic_fetch_inc)\
      [`atomic_fetch_max`](#atomic_fetch_max)\
      [`atomic_fetch_min`](#atomic_fetch_min)\
      [`atomic_fetch_or`](#atomic_fetch_or)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_sub`](#atomic_fetch_sub)\
      [`atomic_fetch_xor`](#atomic_fetch_xor)\
      [`copy`](#copy)\
      [`copy_async`](#copy_async)\
      [`direct3d_abort`](#direct3d_abort)
   :::column-end:::
   :::column span="":::
      [`direct3d_errorf`](#direct3d_errorf)\
      [`direct3d_printf`](#direct3d_printf)\
      [`global_memory_fence`](#global_memory_fence)\
      [`parallel_for_each`](#parallel_for_each)\
      [`tile_static_memory_fence`](#tile_static_memory_fence)
   :::column-end:::
:::row-end:::

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a> all_memory_fence

Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich operacji dostępu do pamięci. Daje to pewność, że wszystkie dostępy do pamięci są widoczne dla innych wątków w kafelku wątku i są wykonywane w kolejności programu.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt `tile_barrier`.

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a> amp_uninitialize

Umożliwia odinicjowanie środowiska uruchomieniowego C++ AMP. Istnieje możliwość wielokrotnego wywołania tej funkcji w okresie istnienia aplikacji. Wywołanie interfejsu API C++ AMP po wywołaniu tej funkcji spowoduje ponowne zainicjowanie środowiska uruchomieniowego C++ AMP. Należy zauważyć, że nie jest dozwolone używanie C++ AMP obiektów w ramach wywołań tej funkcji, co spowoduje niezdefiniowane zachowanie. Ponadto współbieżne wywoływanie tej funkcji i innych interfejsów API AMP jest niedozwolone i spowoduje niezdefiniowane zachowanie.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a> atomic_compare_exchange

Niepodzielnie porównuje wartość przechowywaną w lokalizacji w pamięci określonej w pierwszym argumencie dla równości z wartością drugiego określonego argumentu, a jeśli wartości są takie same, wartość w lokalizacji pamięci jest zmieniana na trzeci określony argument.

```cpp
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,
    _Inout_ int* _Expected_value,
    int value
    ) restrict(amp)

inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,
    _Inout_ unsigned int* _Expected_value,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja, z której jest odczytywana jedna z wartości, które mają być porównane, i do której ma zostać zapisana nowa wartość (jeśli istnieje).

*_Expected_value*<br/>
Lokalizacja, z której zostanie odczytana druga wartość do porównania.

*wartościami*<br/>
Wartość, która ma być przechowywana w lokalizacji pamięci określonej w parametrze `_Dest` if `_Dest` jest równa `_Expected_value` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli operacja się powiedzie; w przeciwnym razie **`false`** .

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a> Funkcja atomic_exchange (C++ AMP)

Ustawia wartość lokalizacji docelowej jako operację niepodzielną.

```cpp
inline int atomic_exchange(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)

inline float atomic_exchange(
    _Inout_ float* _Dest,
    float value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji docelowej.

*wartościami*<br/>
Nowa wartość.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji docelowej.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a> Funkcja atomic_fetch_add (C++ AMP)

Niepodzielnie Dodaj wartość do wartości lokalizacji pamięci.

```cpp
inline int atomic_fetch_add(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji pamięci.

*wartościami*<br/>
Wartość, która ma zostać dodana.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a> Funkcja atomic_fetch_and (C++ AMP)

Niepodzielnie wykonuje wartości bitowe i wartość lokalizacji pamięci.

```cpp
inline int atomic_fetch_and(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji pamięci.

*wartościami*<br/>
Wartość, która ma być używana w obliczeniach bitowych i.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a> atomic_fetch_dec

Niepodzielnie zmniejsza wartość przechowywaną w określonej lokalizacji pamięci.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości do zmniejszenia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a> atomic_fetch_inc

Niepodzielnie zwiększa wartość przechowywaną w określonej lokalizacji pamięci.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości do zwiększenia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a> atomic_fetch_max

Niepodzielnie oblicza wartość maksymalną między wartością przechowywaną w lokalizacji w pamięci określonej w pierwszym argumencie i wartością określoną w drugim argumencie i zapisuje ją w tej samej lokalizacji pamięci.

```cpp
inline int atomic_fetch_max(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja, z której jest odczytywana jedna z wartości, które mają być porównane, i do której mają być przechowywane wartości maksymalne z dwóch.

*wartościami*<br/>
Wartość do porównania z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji lokalizacji.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a> atomic_fetch_min

Niepodzielnie oblicza wartość minimalną między wartością przechowywaną w lokalizacji pamięci określonej w pierwszym argumencie i wartością określoną w drugim argumencie i zapisuje ją w tej samej lokalizacji pamięci.

```cpp
inline int atomic_fetch_min(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja, z której jest odczytywana jedna z wartości, które mają być porównane, i do której mają być przechowywane minimum dwóch wartości.

*wartościami*<br/>
Wartość do porównania z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji lokalizacji.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a> Funkcja atomic_fetch_or (C++ AMP)

Niepodzielnie wykonuje operacje bitowe lub z wartością oraz wartością lokalizacji pamięci.

```cpp
inline int atomic_fetch_or(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji pamięci.

*wartościami*<br/>
Wartość, która ma być używana w obliczeniach bitowych lub.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a> Funkcja atomic_fetch_sub (C++ AMP)

Niepodzielnie odejmuje wartość z lokalizacji pamięci.

```cpp
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji docelowej.

*wartościami*<br/>
Wartość do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a> Funkcja atomic_fetch_xor (C++ AMP)

Niepodzielnie wykonuje bitowe operacje XOR o wartości i lokalizacji pamięci.

```cpp
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Wskaźnik do lokalizacji pamięci.

*wartościami*<br/>
Wartość, która ma zostać użyta w obliczeniach XOR.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="copy"></a><a name="copy"></a> kopiowane

Kopiuje obiekt C++ AMP. Spełnione są wszystkie wymagania dotyczące synchronicznego transferu danych. Nie można skopiować danych podczas uruchamiania kodu na akceleratorze. Ogólna forma tej funkcji to `copy(src, dest)` .

```cpp
template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
   OutputIterator _DestIter);

template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt do skopiowania.

*_DestIter*<br/>
Iterator danych wyjściowych do pozycji początkowej w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora danych wyjściowych.

*_Rank*<br/>
Ranga obiektu, z którego ma zostać skopiowana lub do której ma być kopiowany obiekt.

*_Src*<br/>
Na obiekt do skopiowania.

*_SrcFirst*<br/>
Początkowy iterator do kontenera źródłowego.

*_SrcLast*<br/>
Końcowy iterator do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

## <a name="copy_async"></a><a name="copy_async"></a> copy_async

Kopiuje obiekt C++ AMP i zwraca obiekt [completion_future](completion-future-class.md) , który może być oczekiwany. Nie można skopiować danych podczas uruchamiania kodu na akceleratorze.  Ogólna forma tej funkcji to `copy(src, dest)` .

```cpp
template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt do skopiowania.

*_DestIter*<br/>
Iterator danych wyjściowych do pozycji początkowej w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora danych wyjściowych.

*_Rank*<br/>
Ranga obiektu, z którego ma zostać skopiowana lub do której ma być kopiowany obiekt.

*_Src*<br/>
Na obiekt do skopiowania.

*_SrcFirst*<br/>
Początkowy iterator do kontenera źródłowego.

*_SrcLast*<br/>
Końcowy iterator do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

### <a name="return-value"></a>Wartość zwracana

`future<void>`, Który może być oczekiwany.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a> direct3d_abort

Przerywa wykonywanie funkcji z `restrict(amp)` klauzulą ograniczenia. Gdy środowisko uruchomieniowe AMP wykryje wywołanie, wywołuje [runtime_exception](runtime-exception-class.md) wyjątek z komunikatem o błędzie "Rasteryzuj referenceer: trafienie instrukcji przerwania cienia".

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a> direct3d_errorf

Drukuje sformatowany ciąg w oknie danych wyjściowych programu Visual Studio. Jest wywoływana z funkcji z `restrict(amp)` klauzulą ograniczenia. Gdy środowisko uruchomieniowe AMP wykryje wywołanie, wywołuje [runtime_exception](runtime-exception-class.md) wyjątek z tym samym ciągiem formatowania.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a> direct3d_printf

Drukuje sformatowany ciąg w oknie danych wyjściowych programu Visual Studio. Jest wywoływana z funkcji z `restrict(amp)` klauzulą ograniczenia.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a> global_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku do momentu zakończenia wszystkich dostępów do pamięci globalnej. Gwarantuje to, że dostępy do pamięci globalnej są widoczne dla innych wątków w kafelku wątku i są wykonywane w kolejności programu.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a> Funkcja parallel_for_each (C++ AMP)

Uruchamia funkcję w całej domenie obliczeniowej. Aby uzyskać więcej informacji, zobacz [C++ amp przegląd](../../../parallel/amp/cpp-amp-overview.md).

```cpp
template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
   const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Obiekt, dla `accelerator_view` którego ma zostać uruchomione obliczenie równoległe.

*_Compute_domain*<br/>
`extent`Obiekt, który zawiera dane do obliczenia.

*_Dim0*<br/>
Wymiar `tiled_extent` obiektu.

*_Dim1*<br/>
Wymiar `tiled_extent` obiektu.

*_Dim2*<br/>
Wymiar `tiled_extent` obiektu.

*_Kernel*<br/>
Obiekt lambda lub funkcja, która przyjmuje argument typu "index \<_Rank> " i wykonuje obliczenia równoległe.

*_Kernel_type*<br/>
Lambda lub Funktor.

*_Rank*<br/>
Ranga zakresu.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a> tile_static_memory_fence

Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich zaległych `tile_static` operacji dostępu do pamięci. Dzięki temu `tile_static` dostęp do pamięci będzie widoczny dla innych wątków w kafelku wątku, a dostęp do nich jest wykonywany w kolejności programu.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
