---
title: norm_2, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
dev_langs:
- C++
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc1e6d499c5e02c32a7df02c91b012f9440e7cbb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104455"
---
# <a name="norm2-class"></a>norm_2 — Klasa
Reprezentuje krótki wektor dwóch normalnych liczb.  
  
## <a name="syntax"></a>Składnia  
  
```  
class norm_2;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[norm_2 Constructor](#ctor)|Przeciążone. Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|norm_2::get_x||  
|norm_2::get_xy||  
|norm_2::get_y||  
|norm_2::get_yx||  
|norm_2::ref_g||  
|norm_2::ref_r||  
|norm_2::ref_x||  
|norm_2::ref_y||  
|norm_2::set_x||  
|norm_2::set_xy||  
|norm_2::set_y||  
|norm_2::set_yx||  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|norm_2::operator-||  
|norm_2::operator--||  
|norm_2::operator * =||  
|norm_2::operator / =||  
|norm_2::operator ++||  
|norm_2::operator +=||  
|norm_2::operator =||  
|norm_2::operator-=||  
  
### <a name="public-constants"></a>Publiczne stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[rozmiar — stała](#norm_2__size)||  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|norm_2::g||  
|norm_2::GR||  
|norm_2::r||  
|norm_2::rg||  
|norm_2::x||  
|norm_2::xy||  
|norm_2::y||  
|norm_2::yx||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `norm_2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> norm_2 

 Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.  
  
```  
norm_2() restrict(amp,
    cpu);

 
norm_2(
    norm _V0,  
    norm _V1) restrict(amp,
    cpu);

 
norm_2(
    float _V0,  
    float _V1) restrict(amp,
    cpu);

 
norm_2(
    unorm _V0,  
    unorm _V1) restrict(amp,
    cpu);

 
norm_2(
    norm _V) restrict(amp,
    cpu);

 
explicit norm_2(
    float _V) restrict(amp,
    cpu);

 
norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline norm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
*_V0*<br/>
Wartość do zainicjowania elementu 0.  
  
*_V1*<br/>
Wartość do zainicjowania elementu 1.  
  
*_V*<br/>
Wartość inicjalizacji.  
  
*_Inne*<br/>
Obiekt używany do inicjowania.  
  
##  <a name="norm_2__size"></a> Rozmiar 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
