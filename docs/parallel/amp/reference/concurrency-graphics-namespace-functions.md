---
title: Concurrency::graphics, funkcje przestrzeni nazw
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::fast_math::copy_async
- amp_graphics/Concurrency::fast_math::copy
ms.assetid: ace01cd5-29d3-4356-930e-c81a61c5f934
ms.openlocfilehash: 46b8a171acd3b125749b4e2c519909b82c76dc39
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883749"
---
# <a name="concurrencygraphics-namespace-functions"></a>Concurrency::graphics, funkcje przestrzeni nazw

|||
|-|-|
|[kopiowane](#copy)|[copy_async](#copy_async)|

## <a name="copy"></a>copy — Funkcja (przestrzeń nazw Concurrency:: Graphics)

Kopiuje teksturę źródłową do buforu docelowego lub kopiuje bufor źródłowy do bufora docelowego. Ogólna forma tej funkcji jest `copy(src, dest)`.

```cpp
template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type>
>
void copy (
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size,
    _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>void copy(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent, OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture,
    void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>Parametry

*_Copy_extent*<br/>
Zakres sekcji tekstury, która ma zostać skopiowana.

*_Dst*<br/>
Obiekt do skopiowania.

*_Dst_byte_size*<br/>
Liczba bajtów w miejscu docelowym.

*_Dst_type*<br/>
Typ obiektu docelowego.

*_Dst_offset*<br/>
Przesunięcie do lokalizacji docelowej, w której ma się rozpocząć kopiowanie.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora danych wyjściowych.

*_Src*<br/>
Na obiekt do skopiowania.

*_Src_byte_size*<br/>
Liczba bajtów w źródle.

*_Src_type*<br/>
Typ obiektu źródłowego.

*_Src_offset*<br/>
Przesunięcie do źródła, od którego należy rozpocząć kopiowanie.

*pierwszego*<br/>
Początkowy iterator do kontenera źródłowego.

*ostatniego*<br/>
Końcowy iterator do kontenera źródłowego.

## <a name="copy_async"></a>Funkcja copy_async (przestrzeń nazw Concurrency:: Graphics)

Asynchronicznie kopiuje teksturę źródłową do bufora docelowego lub kopiuje bufor źródłowy do buforu docelowego, a następnie zwraca obiekt [completion_future](completion-future-class.md) , który może być oczekiwany. Nie można skopiować danych, gdy kod jest uruchomiony na akceleratorze. Ogólna forma tej funkcji jest `copy(src, dest)`.

```cpp
template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type &_Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>Parametry

*_Copy_extent*<br/>
Zakres sekcji tekstury, która ma zostać skopiowana.

*_Dst*<br/>
Obiekt do skopiowania.

*_Dst_byte_size*<br/>
Liczba bajtów w miejscu docelowym.

*_Dst_type*<br/>
Typ obiektu docelowego.

*_Dst_offset*<br/>
Przesunięcie do lokalizacji docelowej, w której ma się rozpocząć kopiowanie.

*InputIterator*<br/>
Typ iteratora wejściowego.

*OutputIterator*<br/>
Typ iteratora danych wyjściowych.

*_Src*<br/>
Na obiekt do skopiowania.

*_Src_byte_size*<br/>
Liczba bajtów w źródle.

*_Src_type*<br/>
Typ obiektu źródłowego.

*_Src_offset*<br/>
Przesunięcie do źródła, od którego należy rozpocząć kopiowanie.

*pierwszego*<br/>
Początkowy iterator do kontenera źródłowego.

*ostatniego*<br/>
Końcowy iterator do kontenera źródłowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
