---
title: Klasa platform::Box | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
dev_langs:
- C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 813ba26333cb73212db966a0446d722eb4e0795d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformbox-class"></a>Klasa platform::Box
Włącza typu wartości, takich jak `Windows::Foundation::DateTime` lub typem skalarnym, takich jak `int` mają być przechowywane w `Platform::Object` typu. Zazwyczaj nie jest konieczne użycie `Box` jawnie, ponieważ pakującej sytuacji niejawnie podczas rzutowania typu wartości do `Object^`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
ref class Box abstract;  
```  
  ### <a name="remarks"></a>Uwagi  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** vccorlib.h  
  
 **Namespace:** platformy
|Element członkowski|Opis|  
|------------|-----------------|
|[Box](#ctor)|Tworzy `Box` które hermetyzują wartość określonego typu.|
|[Operator pole&lt;const T&gt;^](#box-const-t)|Włącza konwersji pakującej z `const` klasę wartości `T` lub `enum` klasy `T` do `Box<T>`.|
|[Operator pole&lt;stała nietrwałe T&gt;^](#box-const-volatile-t)|Włącza konwersji pakującej z `const volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`. |
|[Operator pole&lt;T&gt;^](#box-t)|Włącza konwersji pakującej z klasą wartości `T` do `Box<T>`.|
|[Operator pole&lt;T nietrwałe&gt;^](#box-volatile-t)|Włącza konwersji pakującej z `volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`.|
|[Box::operator T](#t)|Włącza konwersji pakującej z klasą wartości `T` lub `enum` klasy `T` do `Box<T>`.| 
## <a name="ctor"></a> Konstruktor Box::Box
Tworzy `Box` które hermetyzują wartość określonego typu. | |[ Wartość właściwości](#value)| Zwraca wartość, która jest hermetyzowany w `Box` obiektu. |  
### <a name="syntax"></a>Składnia  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>Parametry  
 `valueArg`  
 Typ wartości, aby zostać opakowany — na przykład `int`, `bool`, `float64`, `DateTime`.  
  

## <a name="box-const-t"></a> Pole Box::operator&lt;const T&gt;^ — Operator
Włącza konwersji pakującej z `const` klasę wartości `T` lub `enum` klasy `T` do `Box<T>`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Wszystkie klasy wartości, wartość struktury lub typu wyliczeniowego. Zawiera wbudowane typy w [domyślny obszar nazw](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::Box<T>^` wystąpienia, który reprezentuje oryginalnej wartości opakowany w klasie ref.  
  
## <a name="box-const-volatile-t"></a> Pole Box::operator&lt;stała nietrwałe T&gt;^ — Operator
Włącza konwersji pakującej z `const volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ wyliczenia, klasy wartości lub wartość struktury. Zawiera wbudowane typy w [domyślny obszar nazw](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::Box<T>^` wystąpienia, który reprezentuje oryginalnej wartości opakowany w klasie ref.  
  
## <a name="box-t"></a> Pole Box::operator&lt;T&gt;^ — Operator
Włącza konwersji pakującej z klasą wartości `T` do `Box<T>`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ wyliczenia, klasy wartości lub wartość struktury. Zawiera wbudowane typy w [domyślny obszar nazw](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::Box<T>^` wystąpienia, który reprezentuje oryginalnej wartości opakowany w klasie ref.  
  
## <a name="box-volatile-t"></a> Pole Box::operator&lt;volatile T&gt;^ — Operator
Włącza konwersji pakującej z `volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ wyliczenia, klasy wartości lub wartość struktury. Zawiera wbudowane typy w [domyślny obszar nazw](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::Box<T>^` wystąpienia, który reprezentuje oryginalnej wartości opakowany w klasie ref.  
  
## <a name="t"></a>  Operator Box::operator T
Włącza konwersji pakującej z klasą wartości `T` lub `enum` klasy `T` do `Box<T>`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ wyliczenia, klasy wartości lub wartość struktury. Zawiera wbudowane typy w [domyślny obszar nazw](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::Box<T>^` wystąpienia, który reprezentuje oryginalnej wartości opakowany w klasie ref.  
  

## <a name="value"></a> Właściwość Box::Value
Zwraca wartość, która jest hermetyzowany w `Box` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwotnie była przed jego został opakowany wartości spakowanej tego samego typu.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)   
 [OPAKOWYWANIE](../cppcx/boxing-c-cx.md)