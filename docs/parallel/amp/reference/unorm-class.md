---
title: "unorm — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfd4ed2b4aad398e1206d0e3b786742841aa189b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="unorm-class"></a>unorm — Klasa
Reprezentuje numer unorm —. Każdy element jest liczbą zmiennoprzecinkową wskaż liczbę z zakresu [0.0f, 1,0 f].  
  
## <a name="syntax"></a>Składnia  
  
```  
class unorm;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[unorm — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor. Zainicjuj do 0,0.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|unorm::operator--||  
|unorm::operator float|Operator konwersji. Konwertowanie liczby unorm — zmiennoprzecinkowej wartości.|  
|unorm::operator*=||  
|unorm::operator / =||  
|unorm::operator ++||  
|unorm::operator +=||  
|unorm::operator=||  
|unorm::operator-=||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `unorm`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> unorm — 

 Domyślny konstruktor. Zainicjuj do 0,0.  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_V`  
 Wartość używaną do inicjalizacji.  
  
 `_Other`  
 Obiekt normy używaną do inicjalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
