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
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376352"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkcje przestrzeni nazw współbieżności (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[Funkcja atomic_exchange (C++ AMP)](#atomic_exchange)|[Funkcja atomic_fetch_add (C++ AMP)](#atomic_fetch_add)|[Funkcja atomic_fetch_and (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[Funkcja atomic_fetch_or (C++ AMP)](#atomic_fetch_or)|[Funkcja atomic_fetch_sub (C++ AMP)](#atomic_fetch_sub)|
|[Funkcja atomic_fetch_xor (C++ AMP)](#atomic_fetch_xor)|[Kopii](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[Funkcja parallel_for_each (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku, dopóki nie zostaną ukończone wszystkie dostępy do pamięci. Gwarantuje to, że wszystkie dostępy do pamięci są widoczne dla innych wątków na kafelku wątku i są wykonywane w kolejności programu.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt `tile_barrier`.

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

Uninitializes środowiska wykonawczego C++ AMP. Jest to legalne, aby wywołać tę funkcję wiele razy w okresie istnienia aplikacji. Wywołanie dowolnego interfejsu API C++ AMP po wywołaniu tej funkcji spowoduje ponowne zainicjowanie środowiska wykonawczego C++ AMP. Należy zauważyć, że jest to niezgodne z prawem do korzystania z obiektów C++ AMP przez wywołania tej funkcji i spowoduje to niezdefiniowane zachowanie. Ponadto jednoczesne wywołanie tej funkcji i innych interfejsów API amp jest nielegalne i spowodowałoby niezdefiniowane zachowanie.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

Niepodzielnie porównuje wartość przechowywaną w lokalizacji pamięci określonej w pierwszym argurze równości z wartością drugiego określonego argumentu, a jeśli wartości są takie same, wartość w lokalizacji pamięci zostanie zmieniona na wartość trzeciego określonego argumentu.

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
Lokalizacja, z której odczytywana jest jedna z wartości, które mają być porównywane, i do której ma być przechowywana nowa wartość, jeśli istnieje.

*_Expected_value*<br/>
Zostanie odczytana lokalizacja, z której zostanie porównana druga wartość do porównania.

*value*<br/>
Wartość, która ma być przechowywana `_Dest` w `_Dest` lokalizacji `_Expected_value`pamięci określonej przez if jest równa .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli operacja zakończy się pomyślnie; w przeciwnym razie **false**.

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>Funkcja atomic_exchange (C++ AMP)

Ustawia wartość lokalizacji docelowej jako operacji niepodzielnej.

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

*value*<br/>
Nowa wartość.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji docelowej.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>Funkcja atomic_fetch_add (C++ AMP)

Atomicznie dodać wartość do wartości lokalizacji pamięci.

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

*value*<br/>
Wartość dodana.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>Funkcja atomic_fetch_and (C++ AMP)

Atomically wykonuje działanie bitowe i wartości wartości lokalizacji pamięci.

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

*value*<br/>
Wartość używana w obliczeniach bitowych AND.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

Niepodzielnie zmniejsza wartość przechowywaną w określonej lokalizacji pamięci.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości, która ma zostać zdekrzecona.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

Niepotarcie zwiększa wartość przechowywaną w określonej lokalizacji pamięci.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości, która ma być zwiększana.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

Atomically oblicza maksymalną wartość między wartością przechowywaną w lokalizacji pamięci określonej w pierwszym argumentie a wartością określoną w drugim argum i przechowuje ją w tej samej lokalizacji pamięci.

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
Lokalizacja, z której odczytywana jest jedna z wartości, które mają być porównywane, i do której ma być przechowywana maksymalna z dwóch wartości.

*value*<br/>
Wartość, która ma być porównywana z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

Atomically oblicza wartość minimalną między wartością przechowywaną w lokalizacji pamięci określonej w pierwszym argumentie a wartością określoną w drugim argum i przechowuje ją w tej samej lokalizacji pamięci.

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
Lokalizacja, z której odczytywana jest jedna z wartości, które mają być porównywane, i do której ma być przechowywana minimalna z dwóch wartości.

*value*<br/>
Wartość, która ma być porównywana z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>Funkcja atomic_fetch_or (C++ AMP)

Niepodzielnie wykonuje działanie bitowe OR z wartością i wartością lokalizacji pamięci.

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

*value*<br/>
Wartość używana w obliczeniach bitowych OR.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>Funkcja atomic_fetch_sub (C++ AMP)

Niepodzielnie odejmuje wartość od lokalizacji pamięci.

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

*value*<br/>
Wartość do odjętej.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>Funkcja atomic_fetch_xor (C++ AMP)

Niepodzielnie wykonuje bitowe działanie XOR wartości i lokalizacji pamięci.

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

*value*<br/>
Wartość używana w obliczeniach XOR.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

## <a name="copy"></a><a name="copy"></a>Kopii

Kopiuje obiekt C++ AMP. Wszystkie wymagania dotyczące synchroniczowego transferu danych są spełnione. Nie można skopiować danych podczas uruchamiania kodu na akceleratorze. Ogólną formą tej `copy(src, dest)`funkcji jest .

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
Iterator wyjściowy do pozycji początkowej w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*Dane wyjścioweIterator*<br/>
Typ iteratora wyjściowego.

*_Rank*<br/>
Ranga obiektu do skopiowania lub obiektu do skopiowania.

*_Src*<br/>
Aby sprzeciwić się kopiowaniu.

*_SrcFirst*<br/>
Początkujący iterator do kontenera źródłowego.

*_SrcLast*<br/>
Iterator końcowy do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

Kopiuje obiekt C++ AMP i zwraca [completion_future](completion-future-class.md) obiekt, na który można czekać. Nie można skopiować danych podczas uruchamiania kodu na akceleratorze.  Ogólną formą tej `copy(src, dest)`funkcji jest .

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
Iterator wyjściowy do pozycji początkowej w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*Dane wyjścioweIterator*<br/>
Typ iteratora wyjściowego.

*_Rank*<br/>
Ranga obiektu do skopiowania lub obiektu do skopiowania.

*_Src*<br/>
Aby sprzeciwić się kopiowaniu.

*_SrcFirst*<br/>
Początkujący iterator do kontenera źródłowego.

*_SrcLast*<br/>
Iterator końcowy do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

### <a name="return-value"></a>Wartość zwracana

A, `future<void>` na które można czekać.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

Przerywa wykonywanie funkcji z klauzulą `restrict(amp)` ograniczeń. Gdy środowisko wykonawcze AMP wykryje wywołanie, wywołuje wyjątek [runtime_exception](runtime-exception-class.md) z komunikatem o błędzie "Reference Rasterizer: Shader abort instruction hit".

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

Drukuje sformatowany ciąg do okna wyjściowego programu Visual Studio. Jest wywoływana z funkcji `restrict(amp)` z klauzulą ograniczenia. Gdy środowisko wykonawcze AMP wykryje wywołanie, wywołuje [wyjątek runtime_exception](runtime-exception-class.md) z tym samym ciągiem formatowania.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

Drukuje sformatowany ciąg do okna wyjściowego programu Visual Studio. Jest wywoływana z funkcji `restrict(amp)` z klauzulą ograniczenia.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

Blokuje wykonywanie wszystkich wątków na kafelku, dopóki nie zostaną ukończone wszystkie dostępy do pamięci globalnej. Gwarantuje to, że dostęp do pamięci globalnej są widoczne dla innych wątków na kafelku wątku i są wykonywane w kolejności programu.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>Funkcja parallel_for_each (C++ AMP)

Uruchamia funkcję w domenie obliczeniowej. Aby uzyskać więcej informacji, zobacz [Omówienie amp języka C++](../../../parallel/amp/cpp-amp-overview.md).

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
Obiekt `accelerator_view` do uruchomienia obliczeń równoległych na.

*_Compute_domain*<br/>
Obiekt, `extent` który zawiera dane dla obliczeń.

*_Dim0*<br/>
Wymiar `tiled_extent` obiektu.

*_Dim1*<br/>
Wymiar `tiled_extent` obiektu.

*_Dim2*<br/>
Wymiar `tiled_extent` obiektu.

*_Kernel*<br/>
Lambda lub obiekt funkcji, który przyjmuje\<argument typu "indeks _Rank>" i wykonuje obliczenia równoległe.

*_Kernel_type*<br/>
Lambda lub functor.

*_Rank*<br/>
Ranga zakresu.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku, dopóki nie zostaną ukończone wszystkie zaległe `tile_static` dostępy do pamięci. Dzięki temu `tile_static` dostęp do pamięci są widoczne dla innych wątków na kafelku wątku i że dostępy są wykonywane w kolejności programu.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier.

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
