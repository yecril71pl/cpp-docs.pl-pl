---
title: unorm_2, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
dev_langs:
- C++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f49d51fc939df8fc26000627552afc19a0208d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106210"
---
# <a name="unorm2-class"></a>unorm_2 — Klasa
Reprezentuje krótki wektor dwóch liczb normalnych bez znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class unorm_2;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[unorm_2 — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|unorm_2::get_x||  
|unorm_2::get_xy||  
|unorm_2::get_y||  
|unorm_2::get_yx||  
|unorm_2::ref_g||  
|unorm_2::ref_r||  
|unorm_2::ref_x||  
|unorm_2::ref_y||  
|unorm_2::set_x||  
|unorm_2::set_xy||  
|unorm_2::set_y||  
|unorm_2::set_yx||  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|unorm_2::operator--||  
|unorm_2::operator * =||  
|unorm_2::operator / =||  
|unorm_2::operator ++||  
|unorm_2::operator +=||  
|unorm_2::operator =||  
|unorm_2::operator-=||  
  
### <a name="public-constants"></a>Publiczne stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|unorm_2::size — Stała||  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|unorm_2::g||  
|unorm_2::GR||  
|unorm_2::r||  
|unorm_2::rg||  
|unorm_2::x||  
|unorm_2::xy||  
|unorm_2::y||  
|unorm_2::yx||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `unorm_2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> unorm_2 

 Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.  
  
```  
unorm_2() restrict(amp,
    cpu);

 
unorm_2(
    unorm _V0,  
    unorm _V1) restrict(amp,
    cpu);

 
unorm_2(
    float _V0,  
    float _V1) restrict(amp,
    cpu);

 
unorm_2(
    unorm _V) restrict(amp,
    cpu);

 
explicit unorm_2(
    float _V) restrict(amp,
    cpu);

 
unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline unorm_2(
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
  
##  <a name="unorm_2__size"></a> Rozmiar 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
