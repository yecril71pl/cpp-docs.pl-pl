---
title: Klasa platform::STAThreadAttribute | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
dev_langs: C++
helpviewer_keywords: Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 54e4b7621879252b14fa0fe71c837439da147df5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformstathreadattribute-class"></a>Klasa platform::STAThreadAttribute
Wskazuje, że model wątkowy dla aplikacji jest jednowątkowego apartamentu (STA).  
  
## <a name="syntax"></a>Składnia  
  
```  
public ref class STAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Konstruktor elementu STAThreadAttribute 1](#ctor)|Inicjuje nowe wystąpienie klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
 Atrybut STAThreadAttribute dziedziczy [Platform::Object klasy](../cppcx/platform-object-class.md). STAThreadAttribute również overloads lub ma następujące elementy:  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[STAThreadAttribute::Equals](#equals)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|  
|[STAThreadAttribute::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|  
|[STAThreadAttribute::ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Platform`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** platformy  



## <a name="ctor"></a>Konstruktor elementu STAThreadAttribute
Inicjuje nowe wystąpienie klasy STAThreadAttribute.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:STAThreadAttribute()  
```  
  


## <a name="equals"></a>STAThreadAttribute::Equals
Określa, czy określony obiekt jest równy bieżącemu obiektowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Parametry  
 Obj  
 Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekty są równe; w przeciwnym razie `false`.  
  


## <a name="gethashcode"></a>STAThreadAttribute::GetHashCode
Zwraca kod skrótu dla tego wystąpienia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod skrótu dla tego wystąpienia.  
  


## <a name="tostring"></a>STAThreadAttribute::ToString
Zwraca ciąg, który reprezentuje bieżący obiekt.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg, który reprezentuje bieżący obiekt.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)