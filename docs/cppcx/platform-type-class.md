---
title: Klasa platform::type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs:
- C++
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc70f0a0f714cb6f5a2f4b28d922308d8fe4d645
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="platformtype-class"></a>Klasa platform::type
Zawiera informacje czasu wykonywania o typie — w szczególności ciąg nazwy i elementu typecode. Można uzyskać przez wywołanie [Object::GetType](../cppcx/platform-object-class.md#gettype) dowolnego obiektu lub lub przy użyciu [typeid](../windows/typeid-cpp-component-extensions.md) operator na nazwę klasy lub struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class Platform::Type :      
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable  
```  
  
### <a name="remarks"></a>Uwagi  
 `Type` Klasy jest przydatne w aplikacjach, które należy przekierować przetwarzania przy użyciu `if` lub `switch` instrukcji, która gałęzie na podstawie czasu wykonywania typu obiektu. Kod typu, który opisuje kategorii typu są pobierane przy użyciu [Type::GetTypeCode](#gettypecode) funkcję elementu członkowskiego.  
  
## <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[Type::GetTypeCode — metoda](#gettypecode)|Zwraca [wyliczenie Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) wartość dla obiekt.| 
|[Type::toString — metoda](#tostring)|Zwraca nazwę typu, jak określono w jego metadanych.| 

 
## <a name="public-properties"></a>Właściwości publiczne  
  
|||  
|-|-|  
|[Type::FullName](#fullname)|Zwraca [klasy Platform::String](../cppcx/platform-string-class.md)^ reprezentuje w pełni kwalifikowana nazwa typu, a używa. (kropka) jako separator, nie:: (podwójny dwukropek) — na przykład `MyNamespace.MyClass`.|  
  
## <a name="conversion-operators"></a>Operatory konwersji  
  
|||  
|-|-|  
|[operator typu ^](../cppcx/operator-type-hat.md)|Konwersja z umożliwia `Windows::UI::Xaml::Interop::TypeName` do `Platform::Type`.|  
|[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Konwersja z umożliwia `Platform::Type` do `Windows::UI::Xaml::Interop::TypeName`.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

 
## <a name="fullname"></a> Właściwość Type::FullName
Pobiera pełną nazwę bieżącego typu w formularzu `Namespace.Type`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
String^ FullName();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa typu.  
### <a name="example"></a>Przykład  
  
```  
  
//  namespace is TestApp  
MainPage::MainPage()  
{  
    InitializeComponent();  
    Type^ t = this->GetType();  
    auto s = t->FullName; // returns "TestApp.MainPage"  
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"  
}  
```  
  


## <a name="gettypecode"></a> Type::GetTypeCode — metoda
Pobiera typy wbudowane kategorię typu numerycznego.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden z Platform::TypeCode wyliczyć wartości.  
  
### <a name="remarks"></a>Uwagi  
 Jest odpowiednikiem metodą member GetTypeCode() `typeid` właściwości.

## <a name="tostring"></a> Type::toString — metoda
Pobiera nazwę typu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::String^ ToString();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa typu, jak określono w jego metadanych.    
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)