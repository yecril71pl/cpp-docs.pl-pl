---
title: Funkcje przestrzeni nazw współbieżności (AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 211005f273500992440c0e95d2c3c4e3adcef581
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163416"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkcje przestrzeni nazw współbieżności (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange — funkcja (C++ AMP)](#atomic_exchange)|[atomic_fetch_add, funkcja (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and, funkcja (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or, funkcja (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub, funkcja (C++ AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor, funkcja (C++ AMP)](#atomic_fetch_xor)|[Kopiuj](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each — funkcja (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

##  <a name="all_memory_fence"></a>  all_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich dostępów do pamięci. Zapewnia to, że wszystkie dostępy do pamięci są widoczne dla innych wątków w pliku wątku i zostały wykonane w porządku program.

```
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Element `tile_barrier` obiektu.

##  <a name="amp_uninitialize"></a>  amp_uninitialize —

Deinicjuje środowisko wykonawcze C++ AMP. Jest legalne, aby wywołać tę funkcję wiele razy w okresie istnienia aplikacji. Wywołanie dowolnego po C++ AMP API wywołaniu tej funkcji będzie ponownie zainicjować środowisko wykonawcze C++ AMP. Należy pamiętać, że jest to dozwolone obiektów C++ AMP przez wywołania tej funkcji i takie działanie spowoduje niezdefiniowane zachowanie. Ponadto jednoczesne wywoływanie tej funkcji i wszelkich innych API AMP jest niedozwolone i mogłoby spowodować niezdefiniowane zachowanie.

```
void __cdecl amp_uninitialize();
```

##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange —

Niepodzielnie porównuje wartość przechowywaną w określonej lokalizacji w pamięci określonej w pierwszym argumencie równości z wartością drugiego określonego argumentu, a jeśli wartości są takie same, wartość w lokalizacji pamięci zostanie zmieniona na trzeci określony argument.

```
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
Lokalizacja, z jedną z wartości, które mają być porównane jest odczytywana i do której nowa wartość, jeśli ma być przechowywany.

*_Expected_value*<br/>
Lokalizacja, z którego jest do odczytu druga wartość do porównania.

*value*<br/>
Wartość ma być przechowywany w lokalizacji pamięci określonej w przez `_Dest` Jeśli `_Dest` jest równa `_Expected_value`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli operacja się powiodła się; w przeciwnym razie **false**.

##  <a name="atomic_exchange"></a>  atomic_exchange — funkcja (C++ AMP)

Ustawia wartości docelowej lokalizacji co operacja niepodzielna.

```
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
Wskaźnik do lokalizacji, docelowy adres.

*value*<br/>
Nowa wartość.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji docelowej.

##  <a name="atomic_fetch_add"></a>  atomic_fetch_add, funkcja (C++ AMP)

Niepodzielnie Dodaj wartość do wartości lokalizacji w pamięci.

```
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
Wskaźnik do lokalizacji w pamięci.

*value*<br/>
Wartość do dodania.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

##  <a name="atomic_fetch_and"></a>  atomic_fetch_and, funkcja (C++ AMP)

Niepodzielne wykonuje bitową operację i wartość i wartość lokalizacji w pamięci.

```
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
Wskaźnik do lokalizacji w pamięci.

*value*<br/>
Wartość używana w obliczeniach bitowe AND.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec —

Niepodzielnie zmniejsza wartość przechowywaną w określonej lokalizacji pamięci.

```
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości do zmniejszenia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc —

Niepodzielnie zwiększa wartość przechowywaną w określonej lokalizacji pamięci.

```
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Lokalizacja w pamięci wartości do zwiększenia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w lokalizacji pamięci.

##  <a name="atomic_fetch_max"></a>  atomic_fetch_max —

Niepodzielnie oblicza maksymalną wartość między wartością przechowywaną w podanej lokalizacji pamięci w pierwszym argumencie i wartością określoną w drugim argumencie i zapisuje ją w tym samym miejscu pamięci.

```
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
Lokalizacja, z jedną z wartości, które mają być porównane jest odczytywana i do której ma być przechowywane maksymalnie dwie wartości.

*value*<br/>
Wartość do porównania z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji.

##  <a name="atomic_fetch_min"></a>  atomic_fetch_min —

Niepodzielnie oblicza minimalną wartość między wartością przechowywaną w podanej lokalizacji pamięci w pierwszym argumencie i wartością określoną w drugim argumencie i zapisuje ją w tym samym miejscu pamięci.

```
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
Lokalizacja, z jedną z wartości, które mają być porównane jest odczytywana i do której ma znajdować się co najmniej dwóch wartości.

*value*<br/>
Wartość do porównania z wartością w określonej lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość przechowywana w określonej lokalizacji.

##  <a name="atomic_fetch_or"></a>  atomic_fetch_or, funkcja (C++ AMP)

Niepodzielnie wykonuje operację lub bitowego, za pomocą wartości i wartości lokalizacji pamięci.

```
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
Wskaźnik do lokalizacji w pamięci.

*value*<br/>
Wartość do wykorzystania w obliczeniach bitowe OR.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

##  <a name="atomic_fetch_sub"></a>  atomic_fetch_sub, funkcja (C++ AMP)

Niepodzielnie odejmuje wartość z lokalizacji w pamięci.

```
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
Wskaźnik do lokalizacji, docelowy adres.

*value*<br/>
Wartość do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

##  <a name="atomic_fetch_xor"></a>  atomic_fetch_xor, funkcja (C++ AMP)

Niepodzielnie peforms bitowe XOR operacji o wartości i lokalizacji w pamięci.

```
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
Wskaźnik do lokalizacji w pamięci.

*value*<br/>
Wartość można użyć w obliczeniach XOR.

### <a name="return-value"></a>Wartość zwracana

Oryginalna wartość lokalizacji pamięci.

##  <a name="copy"></a>  Kopiuj

Kopiuje obiekt C++ AMP. Spełnione są wszystkie wymagania synchronicznego transferu danych. Nie można skopiować danych, podczas uruchamiania kodu na akceleratorze. Ogólna postać tej funkcji jest `copy(src, dest)`.

```
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
Obiekt, który można skopiować do.

*_DestIter*<br/>
Iterator danych wyjściowych pozycję początkową w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora wyjściowego.

*_Rank*<br/>
Ranga obiektu do skopiowania albo ten obiekt do skopiowania do.

*_Src*<br/>
Obiekt do skopiowania.

*_SrcFirst*<br/>
Początkowy iterator do kontenera źródłowego.

*_SrcLast*<br/>
Końcowy iterator do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

##  <a name="copy_async"></a>  copy_async —

Kopiuje obiekt C++ AMP i zwraca [completion_future](completion-future-class.md) obiekt, który może być oczekiwany. Nie można skopiować danych, podczas uruchamiania kodu na akceleratorze.  Ogólna postać tej funkcji jest `copy(src, dest)`.

```
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
Obiekt, który można skopiować do.

*_DestIter*<br/>
Iterator danych wyjściowych pozycję początkową w miejscu docelowym.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora wyjściowego.

*_Rank*<br/>
Ranga obiektu do skopiowania albo ten obiekt do skopiowania do.

*_Src*<br/>
Obiekt do skopiowania.

*_SrcFirst*<br/>
Początkowy iterator do kontenera źródłowego.

*_SrcLast*<br/>
Końcowy iterator do kontenera źródłowego.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

### <a name="return-value"></a>Wartość zwracana

A `future<void>` , może być oczekiwany.

##  <a name="direct3d_abort"></a>  direct3d_abort —

Przerywa wykonywanie funkcji z atrybutem `restrict(amp)` klauzulą ograniczenia. Gdy środowisko wykonawcze AMP wykryje wywołanie, zgłasza [runtime_exception](runtime-exception-class.md) wyjątek z komunikatem o błędzie "odwołanie rasteryzatora: programu do cieniowania przerwać trafień instrukcji".

```
void direct3d_abort() restrict(amp);
```

##  <a name="direct3d_errorf"></a>  direct3d_errorf —

Drukuje sformatowany ciąg w oknie danych wyjściowych programu Visual Studio. Jest wywoływane z funkcji z `restrict(amp)` klauzulą ograniczenia. Gdy środowisko wykonawcze AMP wykryje wywołanie, zgłasza [runtime_exception](runtime-exception-class.md) wyjątków o tym samym ciąg formatowania.

```
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

##  <a name="direct3d_printf"></a>  direct3d_printf —

Drukuje sformatowany ciąg w oknie danych wyjściowych programu Visual Studio. Jest wywoływane z funkcji z `restrict(amp)` klauzulą ograniczenia.

```
void direct3d_printf(
    const char *,
...) restrict(amp);
```

##  <a name="global_memory_fence"></a>  global_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie do momentu dostępów do pamięci globalnej wszystkie zostały zakończone. Zapewnia to, że dostępy do pamięci globalnej są widoczne dla innych wątków w pliku wątku i zostały wykonane w porządku program.

```
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier

##  <a name="parallel_for_each"></a>  parallel_for_each — funkcja (C++ AMP)

Uruchamia funkcję w całej domenie obliczeń. Aby uzyskać więcej informacji, zobacz [Przegląd C++ AMP](../../../parallel/amp/cpp-amp-overview.md).

```
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
`accelerator_view` Obiektu systemem obliczeń równoległych.

*_Compute_domain*<br/>
`extent` Obiekt, który zawiera dane do obliczeń.

*_Dim0*<br/>
W wymiarze `tiled_extent` obiektu.

*_Dim1*<br/>
W wymiarze `tiled_extent` obiektu.

*_Dim2*<br/>
W wymiarze `tiled_extent` obiektu.

*_Kernel*<br/>
Obiekt wyrażenia lambda lub funkcji, która przyjmuje argument typu "index\<_Rank >" i wykonuje obliczenia równoległe.

*_Kernel_type*<br/>
Wyrażenie lambda lub funktor.

*_Rank*<br/>
Ranga zakresu.

##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie, aż wszystkie zaległe `tile_static` dostępy do pamięci zostały ukończone. Gwarantuje to, że `tile_static` dostępy do pamięci są widoczne dla innych wątków w pliku wątku, i zostały wykonane w porządku program.

```
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Obiekt tile_barrier.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
