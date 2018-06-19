---
title: Klasa platform::STAThreadAttribute | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab58409bf86af77c9b1f751b9978b5e7103bd043
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089356"
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



## <a name="ctor"></a> Konstruktor elementu STAThreadAttribute
Inicjuje nowe wystąpienie klasy STAThreadAttribute.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:STAThreadAttribute()  
```  
  


## <a name="equals"></a> STAThreadAttribute::Equals
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
  


## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode
Zwraca kod skrótu dla tego wystąpienia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod skrótu dla tego wystąpienia.  
  


## <a name="tostring"></a> STAThreadAttribute::ToString
Zwraca ciąg, który reprezentuje bieżący obiekt.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg, który reprezentuje bieżący obiekt.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)