---
title: short_vector_traits — Struktura
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: c407c42e5c6a7035e911218ecb41c2da62967787
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289614"
---
# <a name="shortvectortraits-structure"></a>short_vector_traits — Struktura

short_vector_traits umożliwia retrival bazowego długość wektora i typowi krótkiego wektora typie skalarnym lub typem skalarnym

## <a name="syntax"></a>Składnia

```
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

#### <a name="parameters"></a>Parametry

`T`

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[short_vector_traits::short_vector_traits Constructor](#ctor)||

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[short_vector_traits::size — stała](#size)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`short_vector_traits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors.h

**Namespace:** CONCURRENCY::Graphics

##  <a name="ctor"></a>  short_vector_traits::short_vector_traits — Konstruktor

```
short_vector_traits();
```

##  <a name="size"></a>  short_vector_traits::size — stała

```
static int const size = 1;
```

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
