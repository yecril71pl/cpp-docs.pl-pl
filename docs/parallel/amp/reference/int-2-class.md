---
title: "int_2 — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
dev_langs: C++
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2eb503747b9e3a8b8a630fccdbdd8b0da9428058
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="int2-class"></a>int_2 — Klasa
Reprezentuje krótki wektor dwóch liczb całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class int_2;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[int_2 — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor, inicjuje wszystkie elementy z 0.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|int_2::get_x||  
|int_2::get_xy||  
|int_2::get_y||  
|int_2::get_yx||  
|int_2::ref_g||  
|int_2::ref_r||  
|int_2::ref_x||  
|int_2::ref_y||  
|int_2::set_x||  
|int_2::set_xy||  
|int_2::set_y||  
|int_2::set_yx||  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|int_2::operator-||  
|int_2::operator--||  
|int_2::operator % =||  
|int_2::operator & =||  
|int_2::operator * =||  
|int_2::operator / =||  
|int_2::operator ^ =||  
|int_2::operator &#124; =||  
|int_2::operator ~||  
|int_2::operator ++||  
|int_2::operator +=||  
|int_2::operator <\<=||  
|int_2::operator =||  
|int_2::operator-=||  
|int_2::operator >> =||  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Size — stała](#int_2__size)||  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|int_2::g||  
|int_2::GR||  
|int_2::r||  
|int_2::RG||  
|int_2::x||  
|int_2::xy||  
|int_2::y||  
|int_2::yx||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `int_2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a>int_2 — 

 Domyślny konstruktor, inicjuje wszystkie elementy z 0.  
  
```  
int_2() restrict(amp,
    cpu);

 
int_2(
    int _V0,  
    int _V1) restrict(amp,
    cpu);

 
int_2(
    int _V) restrict(amp,
    cpu);

 
int_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
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
  
##  <a name="int_2__size"></a>rozmiar 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY::Graphics Namespace](concurrency-graphics-namespace.md)
