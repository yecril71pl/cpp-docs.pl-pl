---
title: "float_2 — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
dev_langs: C++
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 992dbb8150f8fc85ffb0bb56e58a855fa9144e52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="float2-class"></a>float_2 — Klasa
Reprezentuje krótki wektor dwóch elementów przestawnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class float_2;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[float_2 — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor, inicjuje wszystkie elementy z 0.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|float_2::get_x||  
|float_2::get_xy||  
|float_2::get_y||  
|float_2::get_yx||  
|float_2::ref_g||  
|float_2::ref_r||  
|float_2::ref_x||  
|float_2::ref_y||  
|float_2::set_x||  
|float_2::set_xy||  
|float_2::set_y||  
|float_2::set_yx||  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|float_2::operator-||  
|float_2::operator--||  
|float_2::operator * =||  
|float_2::operator / =||  
|float_2::operator ++||  
|float_2::operator +=||  
|float_2::operator =||  
|float_2::operator-=||  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Size — stała](#float_2__size)||  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|float_2::g||  
|float_2::GR||  
|float_2::r||  
|float_2::RG||  
|float_2::x||  
|float_2::xy||  
|float_2::y||  
|float_2::yx||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `float_2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a>float_2 — 

 Domyślny konstruktor, inicjuje wszystkie elementy z 0.  
  
```  
float_2() restrict(amp,
    cpu);

 
float_2(
    float _V0,  
    float _V1) restrict(amp,
    cpu);

 
float_2(
    float _V) restrict(amp,
    cpu);

 
float_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_V0`  
 Wartość do zainicjowania elementu 0.  
  
 `_V1`  
 Wartość zainicjować element 1.  
  
 `_V`  
 Wartość dla inicjowania.  
  
 `_Other`  
 Obiekt używany do inicjowania.  
  
##  <a name="float_2__size"></a>rozmiar 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY::Graphics Namespace](concurrency-graphics-namespace.md)
