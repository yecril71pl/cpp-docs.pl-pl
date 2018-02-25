---
title: "Funkcje przestrzeń nazw współbieżności (AMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 360c253860931f00e65575250d3944b05dc9c4a9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-functions-amp"></a>Funkcje przestrzeń nazw współbieżności (AMP)
||||  
|-|-|-|  
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize —](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|  
|[atomic_exchange, funkcja (C++ AMP)](#atomic_exchange)|[atomic_fetch_add, funkcja (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and, funkcja (C++ AMP)](#atomic_fetch_and)|  
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|  
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or, funkcja (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub, funkcja (C++ AMP)](#atomic_fetch_sub)|  
|[atomic_fetch_xor, funkcja (C++ AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|  
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|  
|[global_memory_fence](#global_memory_fence)|[parallel_for_each — funkcja (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|  
  
##  <a name="all_memory_fence"></a>  all_memory_fence —  
 Wykonanie bloki wszystkie wątki na kafelku ukończenie wszystkich uzyskuje dostęp do pamięci. Dzięki temu wszystkie uzyskuje dostęp do pamięci są widoczne dla innych wątków na kafelku wątku i są wykonywane w kolejności, program.  
  
```  
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 A `tile_barrier` obiektu.  
  
##  <a name="amp_uninitialize">amp_uninitialize —</a>  
 Uninitializes środowiska uruchomieniowego C++ AMP. Jest to niedozwolone wywołanie tej funkcji wiele razy w okresie istnienia aplikacji. Wywoływanie żadnych afer C++ AMP API wywołanie tej funkcji zostanie ponownie zainicjować środowiska uruchomieniowego C++ AMP. Zauważ, że jest niedozwolone w wywołań tej funkcji za pomocą obiektów C++ AMP i to tak spowoduje niezdefiniowane zachowanie. Ponadto jednocześnie wywołanie tej funkcji i wszelkich innych interfejsów API AMP jest niedozwolony i może spowodować niezdefiniowane zachowanie.  
  
```  
void __cdecl amp_uninitialize();
```  
  
##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange —  
 Automatycznie porównuje wartości przechowywane w lokalizacji pamięci określony w pierwszym argumencie równości na wartość drugiego argumentu określony, a jeśli wartości są takie same, wartość w lokalizacji pamięci jest zmieniana na trzeciej określony argument.  
  
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
 `_Dest`  
 Lokalizacja, z których jedna z wartości do porównania jest do odczytu i do którego nowa wartość, jeśli ma być przechowywany.  
  
 `_Expected_value`  
 Lokalizacja, z którego jest do odczytu druga wartość do porównania.  
  
 `value`  
 Wartość, które mają być przechowywane w lokalizacji pamięci określony w przez `_Dest` Jeśli `_Dest` jest równa `_Expected_value`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli operacja zakończy się pomyślnie; w przeciwnym razie `false`.  
  

##  <a name="atomic_exchange">atomic_exchange, funkcja (C++ AMP)</a>  
 Ustawia wartość lokalizacja docelowa jako niepodzielną operację.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji destionation.  
  
 `value`  
 Nowa wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji docelowej.  
  

##  <a name="atomic_fetch_add">atomic_fetch_add, funkcja (C++ AMP)</a>  
 Automatycznie Dodaj wartość do wartości lokalizacji pamięci.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji w pamięci.  
  
 `value`  
 Wartość do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji pamięci.  
  
##  <a name="atomic_fetch_and">atomic_fetch_and, funkcja (C++ AMP)</a>  
 Automatycznie wykonuje operacji i wartość i wartość lokalizacji w pamięci.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji w pamięci.  
  
 `value`  
 Wartość używana w obliczeniach i bitowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji pamięci.  
  
##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec —  
 Automatycznie zmniejsza wartość przechowywana w lokalizacji określonej pamięci.  
  
```  
inline int atomic_fetch_dec(_Inout_ int* _Dest  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Lokalizacja w pamięci zmniejszona wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość przechowywana w lokalizacji pamięci.  
  
##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc —  
 Automatycznie zwiększa wartość przechowywana w lokalizacji określonej pamięci.  
  
```  
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

 
inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Lokalizacja w pamięci wartości ma być zwiększany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość przechowywana w lokalizacji pamięci.  
  
##  <a name="atomic_fetch_max"></a>  atomic_fetch_max —  
 Automatycznie oblicza maksymalną wartość między wartość przechowywana w lokalizacji pamięci określony w pierwszym argumencie a wartością określoną w drugi argument, a następnie przechowuje je w tej samej lokalizacji pamięci.  
  
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
 `_Dest`  
 Lokalizacja, z których jedna z wartości do porównania jest do odczytu i do którego ma być przechowywane maksymalnie dwóch wartości.  
  
 `value`  
 Wartość do porównania z wartością w określonej lokalizacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość przechowywana w lokalizacji określonej lokalizacji.  
  
##  <a name="atomic_fetch_min"></a>  atomic_fetch_min —  
 Automatycznie oblicza minimalną wartość między wartość przechowywana w lokalizacji pamięci określony w pierwszym argumencie a wartością określoną w drugi argument, a następnie przechowuje je w tej samej lokalizacji pamięci.  
  
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
 `_Dest`  
 Lokalizacja, z których jedna z wartości do porównania jest do odczytu i do którego ma być przechowywany co najmniej dwóch wartości.  
  
 `value`  
 Wartość do porównania z wartością w określonej lokalizacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość przechowywana w lokalizacji określonej lokalizacji.  
  
##  <a name="atomic_fetch_or">atomic_fetch_or, funkcja (C++ AMP)</a>  
 Automatycznie wykonuje operację lub bitowe o wartości oraz wartości lokalizacji pamięci.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji w pamięci.  
  
 `value`  
 Wartość używana w obliczeniach bitowej OR.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji pamięci.  
  
##  <a name="atomic_fetch_sub">atomic_fetch_sub, funkcja (C++ AMP)</a>  
 Automatycznie odejmuje wartość z zakresu od lokalizacji pamięci.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji destionation.  
  
 `value`  
 Wartość jest odejmowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji pamięci.  
  
##  <a name="atomic_fetch_xor">atomic_fetch_xor, funkcja (C++ AMP)</a>  
 Automatycznie peforms operacji XOR wartość i lokalizacji w pamięci.  
  
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
 `_Dest`  
 Wskaźnik do lokalizacji w pamięci.  
  
 `value`  
 Wartość używana w obliczeniach XOR.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość lokalizacji pamięci.  
  
##  <a name="copy"></a>  Kopiuj  
 Kopiuje obiekt C++ AMP. Spełniono wszystkie wymagania transferu danych synchroniczne. Nie można skopiować danych, uruchamiając kod na akceleratora. Formularz ogólny tej funkcji jest `copy(src, dest)`.  
  
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
 `_Dest`  
 Obiekt przeznaczony do skopiowania do.  
  
 `_DestIter`  
 Dane wyjściowe iteratora położenie początku w miejscu docelowym.  
  
 `InputIterator`  
 Typ wejściowy interator.  
  
 `OutputIterator`  
 Typ iteratora danych wyjściowych.  
  
 `_Rank`  
 Ranga tego obiektu do skopiowania lub skopiować do.  
  
 `_Src`  
 Aby obiekt do skopiowania.  
  
 `_SrcFirst`  
 Iterator początek w kontenerze źródła.  
  
 `_SrcLast`  
 Końcowy iteratora w kontenerze źródła.  
  
 `value_type`  
 Typ danych elementów, które są kopiowane.  
  
##  <a name="copy_async"></a>  copy_async —  
 Kopiuje obiekt C++ AMP i zwraca [completion_future](completion-future-class.md) obiekt, który może być obsługiwane. Nie można skopiować danych, uruchamiając kod na akceleratora.  Formularz ogólny tej funkcji jest `copy(src, dest)`.  
  
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
 `_Dest`  
 Obiekt przeznaczony do skopiowania do.  
  
 `_DestIter`  
 Dane wyjściowe iteratora położenie początku w miejscu docelowym.  
  
 `InputIterator`  
 Typ wejściowy interator.  
  
 `OutputIterator`  
 Typ iteratora danych wyjściowych.  
  
 `_Rank`  
 Ranga tego obiektu do skopiowania lub skopiować do.  
  
 `_Src`  
 Aby obiekt do skopiowania.  
  
 `_SrcFirst`  
 Iterator początek w kontenerze źródła.  
  
 `_SrcLast`  
 Końcowy iteratora w kontenerze źródła.  
  
 `value_type`  
 Typ danych elementów, które są kopiowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `future<void>` który mogą być obsługiwane.  
  
##  <a name="direct3d_abort"></a>  direct3d_abort —  
 Przerywa wykonywanie funkcji z `restrict(amp)` Klauzula ograniczenia. Środowisko uruchomieniowe AMP wykrycie wywołanie zgłasza [runtime_exception —](runtime-exception-class.md) wyjątek z komunikatem o błędzie "rasteryzator odwołania: programu do cieniowania przerwać trafień instrukcji".  
  
```  
void direct3d_abort() restrict(amp);
```  
  
##  <a name="direct3d_errorf"></a>  direct3d_errorf —  
 Wyświetla ciąg formatowania w oknie danych wyjściowych programu Visual Studio. Jest ona wywoływana z funkcji z `restrict(amp)` Klauzula ograniczenia. Środowisko uruchomieniowe AMP wykrycie wywołanie zgłasza [runtime_exception —](runtime-exception-class.md) wyjątków o tym samym ciągu formatowania.  
  
```  
void direct3d_errorf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="direct3d_printf"></a>  direct3d_printf —  
 Wyświetla ciąg formatowania w oknie danych wyjściowych programu Visual Studio. Jest ona wywoływana z funkcji z `restrict(amp)` Klauzula ograniczenia.  
  
```  
void direct3d_printf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="global_memory_fence"></a>  global_memory_fence —  
 Bloki wykonywanie wszystkich wątków na kafelku, dopóki wszystkie pamięci globalnej uzyskuje dostęp do zostały zakończone. Dzięki temu uzyskuje dostęp do pamięci globalnej są widoczne dla innych wątków na kafelku wątku i są wykonywane w kolejności, program.  
  
```  
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 Tile_barrier — obiekt  
  
##  <a name="parallel_for_each">parallel_for_each — funkcja (C++ AMP)</a>  
 Funkcja znajduje się w domenie obliczeniowej. Aby uzyskać więcej informacji, zobacz [Przegląd C++ AMP](../../../parallel/amp/cpp-amp-overview.md).  
  
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
 `_Accl_view`  
 `accelerator_view` Obiektu do uruchomienia równoległego obliczeń na.  
  
 `_Compute_domain`  
 `extent` Obiekt zawierający dane do obliczenia.  
  
 `_Dim0`  
 Wymiar `tiled_extent` obiektu.  
  
 `_Dim1`  
 Wymiar `tiled_extent` obiektu.  
  
 `_Dim2`  
 Wymiar `tiled_extent` obiektu.  
  
 `_Kernel`  
 Obiekt lambda lub funkcji, które przyjmuje argument typu "indeksu\<_Rank >" i wykonuje obliczenia równoległych.  
  
 `_Kernel_type`  
 Lambda lub obiekt.  
  
 `_Rank`  
 Ranga tego zakresu.  
  
##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence —  
 Blokuje wykonywanie wszystkie wątki na kafelku, aż wszystkie oczekujące `tile_static` uzyskuje dostęp do pamięci zostały ukończone. Gwarantuje to, że `tile_static` uzyskuje dostęp do pamięci są widoczne dla innych wątków na kafelku wątku, a dostępu są wykonywane w kolejności, program.  
  
```  
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 Obiekt tile_barrier —.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
