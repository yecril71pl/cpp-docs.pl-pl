---
title: "tiled_extent — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
dev_langs: C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d2aa225c579eb5d9a1412218a287252c5f076dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tiledextent-class"></a>tiled_extent — Klasa
A `tiled_extent` obiekt jest `extent` obiektu wymiarów jednej do trzech dzielący miejsca zakresu w jednej, dwóch lub trójwymiarowy Kafelki.  
  
### <a name="syntax"></a>Składnia  
  
```  
template <
    int _Dim0,  
    int _Dim1,  
    int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
 
template <
    int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Dim0`  
 Długość najważniejszych wymiaru.  
  
 `_Dim1`  
 Długość dalej do najbardziej znaczących wymiaru.  
  
 `_Dim2`  
 Długość najmniej znaczący wymiaru.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[tiled_extent — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `tiled_extent` klasy.|  

  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_tile_extent](#get_tile_extent)|Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|  
|[Konsola](#pad)|Zwraca nowy `tiled_extent` obiektu z zakresów dostosowana się być podzielna przez wymiary kafelka.|  
|[TRUNCATE](#truncate)|Zwraca nowy `tiled_extent` obiektu z zakresów dostosowana w dół do być podzielna przez wymiary kafelka.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Kopiuje zawartość określonego `tiled_index` obiektu do tego.|  

  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Stała tile_dim0](#tile_dim0)|Przechowuje długość najważniejszych wymiaru.|  
|[Stała tile_dim1](#tile_dim1)|Przechowuje długość dalej do najbardziej znaczących wymiaru.|  
|[Stała tile_dim2](#tile_dim2)|Przechowuje długość najmniej znaczący wymiaru.|  

  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[tile_extent —](#tile_extent)|Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  

## <a name="ctor"></a> tiled_extent — Konstruktor  
Inicjuje nowe wystąpienie klasy `tiled_extent` klasy.  
  
### <a name="syntax"></a>Składnia  
  
```  
tiled_extent();  
  
tiled_extent(  
    const Concurrency::extent<rank>& _Other );  
  
tiled_extent(  
    const tiled_extent& _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `extent` Lub `tiled_extent` obiektu do skopiowania.  
  

  

## <a name="get_tile_extent"></a> get_tile_extent   
Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.  
  
### <a name="syntax"></a>Składnia  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiekt, który przechwytuje wymiary to `tiled_extent` wystąpienia.  
  

## <a name="pad"></a> konsoli   
Zwraca nowy `tiled_extent` obiektu z zakresów dostosowana się być podzielna przez wymiary kafelka.  
  
### <a name="syntax"></a>Składnia  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe `tiled_extent` obiektu przez wartość. 
## <a name="truncate"></a> obcięcia   
Zwraca nowy `tiled_extent` obiektu z zakresów dostosowana w dół do być podzielna przez wymiary kafelka.  
  
### <a name="syntax"></a>Składnia  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nowy `tiled_extent` obiektu z zakresów dostosowana w dół do być podzielna przez wymiary kafelka.  

## <a name="operator_eq"></a> operatora =   
Kopiuje zawartość określonego `tiled_index` obiektu do tego.  
  
### <a name="syntax"></a>Składnia  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `tiled_index` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `tiled_index` wystąpienia.  

## <a name="tile_dim0"></a> tile_dim0   
Przechowuje długość najważniejszych wymiaru.  
  
### <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tile_dim1"></a> tile_dim1   
Przechowuje długość dalej do najbardziej znaczących wymiaru.  
  
### <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tile_dim2"></a> tile_dim2   
Przechowuje długość najmniej znaczący wymiaru.  
  
### <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tile_extent"></a> tile_extent —   
  Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
