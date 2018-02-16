---
title: Klasa platform::MTAThreadAttribute | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 626d80a40c24f81b8723c4e1b8d916f5a3ba2bd6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformmtathreadattribute-class"></a>Klasa platform::MTAThreadAttribute
Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).  
  
## <a name="syntax"></a>Składnia  
  
```  
public ref class MTAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[1 konstruktora MTAThreadAttribute](#ctor) — Konstruktor|Inicjuje nowe wystąpienie klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
 Dziedziczy atrybut MTAThreadAttribute [Platform::Object klasy](../cppcx/platform-object-class.md). MTAThreadAttribute również overloads lub ma następujące elementy:  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[MTAThreadAttribute::Equals](#equals)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|  
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|  
|[MTAThreadAttribute::ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Platform`  
  
### <a name="requirements"></a>Wymagania  
 **Metadane:** platform.winmd  
  
 **Namespace:** platformy  



## <a name="ctor"></a> Konstruktor MTAThreadAttribute
Inicjuje nowe wystąpienie klasy MTAThreadAttribute.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:MTAThreadAttribute()  
```  
  


## <a name="equals"></a> MTAThreadAttribute::Equals
Określa, czy określony obiekt jest równy bieżącemu obiektowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Parametry  
 obj  
 Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli obiekty są równe; w przeciwnym razie `false`.  
  


## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode
Zwraca kod skrótu dla tego wystąpienia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod skrótu dla tego wystąpienia.  
  


## <a name="tostring"></a> MTAThreadAttribute::ToString
Zwraca ciąg, który reprezentuje bieżący obiekt.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg, który reprezentuje bieżący obiekt.  
    
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)