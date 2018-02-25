---
title: "norm — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs:
- C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d462b023d85222601d0f5c59b6b256ff525c7985
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="norm-class"></a>norm — Klasa
Reprezentuje numer normy. Każdy element jest liczbą zmiennoprzecinkową wskaż liczbę z zakresu [-1,0 f, 1,0 f].  
  
## <a name="syntax"></a>Składnia  
  
```  
class norm;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[norm — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor. Zainicjuj do 0,0.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|norm::operator-||  
|norm::operator--||  
|norm::operator float|Operator konwersji. Konwertowanie liczby normy zmiennoprzecinkowej wartości.|  
|norm::operator * =||  
|norm::operator / =||  
|norm::operator ++||  
|norm::operator +=||  
|norm::operator=||  
|norm::operator-=||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `norm`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> norm — 

 Domyślny konstruktor. Zainicjuj do 0,0.  
  
```  
norm(
    void) restrict(amp,
    cpu);

 
explicit norm(
    float _V) restrict(amp,
    cpu);

 
explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit norm(
    int _V) restrict(amp,
    cpu);

 
explicit norm(
    double _V) restrict(amp,
    cpu);

 
norm(
    const norm& _Other) restrict(amp,
    cpu);

 
norm(
    const unorm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_V`  
 Wartość używaną do inicjalizacji.  
  
 `_Other`  
 Obiekt używany do inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
