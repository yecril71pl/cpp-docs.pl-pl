---
title: tiled_index — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ed19dd2a1b62a3682d96f8c9a596fa6a4b1b377
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209436"
---
# <a name="tiledindex-class"></a>tiled_index — Klasa
Dostarcza indeks [tiled_extent](tiled-extent-class.md) obiektu. Ta klasa posiada właściwości, aby uzyskać dostęp do elementów względem lokalnego fragmentu i pokrewny ze źródłem globalnego. Aby uzyskać więcej informacji na temat przestrzeni kafli, zobacz [kafelków za pomocą](../../../parallel/amp/using-tiles.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <
    int _Dim0,  
    int _Dim1 = 0,  
    int _Dim2 = 0  
>  
class tiled_index : public _Tiled_index_base<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;  
 
template <
    int _Dim0  
>  
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Dim0`  
 Długość najbardziej znaczącego wymiaru.  
  
 `_Dim1`  
 Długość następnego najbardziej znaczącego wymiaru.  
  
 `_Dim2`  
 Długość najmniej znaczącego wymiaru.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[tiled_index — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `tile_index` klasy.|  

  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_tile_extent](#tiled_index__get_tile_extent)|Zwraca [zakres](extent-class.md) obiekt, który ma wartości `tiled_index` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|  


  
### <a name="public-constants"></a>Publiczne stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[barrier — stała](#tiled_index__barrier)|Magazyny [tile_barrier](tile-barrier-class.md) obiekt reprezentujący barierę w bieżącym fragmencie wątków.|  
|||  
|[global Constant](#tiled_index__global)|Magazyny [indeksu](index-class.md) obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje globalny indeks w [siatki](https://msdn.microsoft.com/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) obiektu.|  
|[Stała lokalna](#tiled_index__local)|Magazyny `index` obiektu liczbie wymiarów 1, 2 lub 3, reprezentujący względny indeks w bieżącym fragmencie obiektu [tiled_extent](tiled-extent-class.md) obiektu.|  
|[Rank — stała](#tiled_index__rank)|Przechowuje rangę `tiled_index` obiektu.|  
|[Tile — stała](#tiled_index__tile)|Magazyny `index` obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje współrzędne bieżącego fragmentu obiektu `tiled_extent` obiektu.|  
|[tile_dim0 — stała](#tiled_index__tile_dim0)|Przechowuje długość najbardziej znaczącego wymiaru.|  
|[tile_dim1 — stała](#tiled_index__tile_dim1)|Przechowuje długość następnego najbardziej znaczącego wymiaru.|  
|[tile_dim2 — stała](#tiled_index__tile_dim2)|Przechowuje długość najmniej znaczącego wymiaru.|  
|[tile_origin — stała](#tiled_index__tile_origin)|Magazyny `index` obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje globalne współrzędne początku bieżącego fragmentu w `tiled_extent` obiektu.|  

  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Pobiera [zakres](extent-class.md) obiekt, który ma wartości `tiled_index` argumentów szablonu `tiled_index` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  


## <a name="tiled_index__ctor"></a>  tiled_index — Konstruktor  
Inicjuje nowe wystąpienie klasy `tiled_index` klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Global`  
 Globalna [indeksu](index-class.md) stworzonego elementu `tiled_index`.  
  
 `_Local`  
 Lokalny [indeksu](index-class.md) stworzonego elementu `tiled_index`  
  
 `_Tile`  
 Kafelek [indeksu](index-class.md) stworzonego elementu `tiled_index`  
  
 `_Tile_origin`  
 Pochodzenie kafelka [indeksu](index-class.md) stworzonego elementu `tiled_index`  
  
 `_Barrier`  
 [Tile_barrier](tile-barrier-class.md) obiektu stworzonego elementu `tiled_index`.  
  
 `_Other`  
 `tile_index` Obiekt ma być skopiowany do stworzonego elementu `tiled_index`.  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicjuje nowe wystąpienie klasy `tile_index` klasy z indeksu fragmentu w globalnych współrzędnych i względnego położenia w lokalnych współrzędnych fragmentu. `_Global` i `_Tile_origin` parametry są obliczane.|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicjuje nowe wystąpienie klasy `tile_index` klasy poprzez skopiowanie określonego `tiled_index` obiektu.|  


## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent —
Zwraca [zakres](extent-class.md) obiekt, który ma wartości `tiled_index` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.  
  
## <a name="syntax"></a>Składnia  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `extent` Obiekt, który ma wartości `tiled_index` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.  

## <a name="tiled_index__barrier"></a>  Barrier   
Magazyny [tile_barrier](tile-barrier-class.md) obiekt reprezentujący barierę w bieżącym fragmencie wątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
const tile_barrier barrier;  
```  

## <a name="tiled_index__global"></a>  Globalne   
Magazyny [indeksu](index-class.md) obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje globalny indeks obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
const index<rank> global;  
```  
  
## <a name="tiled_index__local"></a>  lokalne   
Magazyny [indeksu](index-class.md) obiektu liczbie wymiarów 1, 2 lub 3, reprezentujący względny indeks w bieżącym fragmencie obiektu [tiled_extent](tiled-extent-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
const index<rank> local;  
```  
  
## <a name="tiled_index__rank"></a>  Ranga   
Przechowuje rangę `tiled_index` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
static const int rank = _Rank;  
```  

## <a name="tiled_index__tile"></a>  Kafelek   
Magazyny [indeksu](index-class.md) obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje współrzędne bieżącego fragmentu obiektu [tiled_extent](tiled-extent-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
const index<rank> tile;  
```  
  
## <a name="tiled_index__tile_dim0"></a>  tile_dim0  
Przechowuje długość najbardziej znaczącego wymiaru.  
  
## <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="tiled_index__tile_dim1"></a>  tile_dim1   
Przechowuje długość następnego najbardziej znaczącego wymiaru.  
  
## <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_index__tile_dim2"></a>  tile_dim2   
Przechowuje długość najmniej znaczącego wymiaru.  
  
## <a name="syntax"></a>Składnia  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_index__tile_origin"></a>  tile_origin   
Magazyny [indeksu](index-class.md) obiektu liczbie wymiarów 1, 2 lub 3, który reprezentuje globalne współrzędne początku bieżącego fragmentu w ramach [tiled_extent](tiled-extent-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
const index<rank> tile_origin  
```  
## <a name="tile_extent"></a>  tile_extent —
  Pobiera [zakres](extent-class.md) obiekt, który ma wartości `tiled_index` argumentów szablonu `tiled_index` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
