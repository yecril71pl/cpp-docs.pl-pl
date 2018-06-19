---
title: Lokalizacja klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdfb555375df4b9f791db25fa2dee47222f79063
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688027"
---
# <a name="location-class"></a>location — Klasa
Abstrakcja lokalizację fizyczną na sprzęcie.  
  
## <a name="syntax"></a>Składnia  
  
```
class location;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Lokalizacja](#ctor)|Przeciążone. Konstruuje `location` obiektu.|  
|[~ location — destruktor](#dtor)|Niszczy `location` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Bieżący](#current)|Zwraca `location` obiekt reprezentujący specyficzny miejsca wątek wywołujący jest wykonywany.|  
|[from_numa_node](#from_numa_node)|Zwraca `location` obiekt reprezentujący podany Węzeł NUMA.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Określa, czy dwa `location` reprezentować innej lokalizacji.|  
|[operator=](#operator_eq)|Przypisuje zawartość innym `location` obiektu do tego.|  
|[operator==](#operator_eq_eq)|Określa, czy dwa `location` reprezentować tej samej lokalizacji.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `location`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ lokalizacji 

 Niszczy `location` obiektu.  
  
```
~location();
```  
  
##  <a name="current"></a> Bieżący 

 Zwraca `location` obiekt reprezentujący specyficzny miejsca wątek wywołujący jest wykonywany.  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Lokalizację reprezentujący specyficzny miejscu wątek wywołujący jest wykonywany.  
  
##  <a name="from_numa_node"></a> from_numa_node 

 Zwraca `location` obiekt reprezentujący podany Węzeł NUMA.  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumaNodeNumber`  
 Numer węzła NUMA do skonstruowania lokalizację.  
  
### <a name="return-value"></a>Wartość zwracana  
 Lokalizację reprezentujący Węzeł NUMA, określony przez `_NumaNodeNumber` parametru.  
  
##  <a name="ctor"></a> Lokalizacja 

 Konstruuje `location` obiektu.  
  
```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>Uwagi  
 Lokalizacji domyślnej skonstruowany reprezentuje system jako całość.  
  
##  <a name="operator_neq"></a> operator! = 

 Określa, czy dwa `location` reprezentować innej lokalizacji.  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli dwie lokalizacje są różne, `false` inaczej.  
  
##  <a name="operator_eq"></a> operator = 

 Przypisuje zawartość innym `location` obiektu do tego.  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Źródło `location` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq_eq"></a> operator == 

 Określa, czy dwa `location` reprezentować tej samej lokalizacji.  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli dwie lokalizacje są identyczne, i `false` inaczej.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
