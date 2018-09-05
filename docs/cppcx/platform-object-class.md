---
title: Platform::Object, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6f4eed4cefba16d95baabe38fc5268c0ae8512
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752329"
---
# <a name="platformobject-class"></a>Platform::Object, klasa
Zapewnia zachowanie wspólnej klasy i struktury ref w aplikacjach Windows Runtime odwołania. Wszystkie klasy referencyjnej i wystąpienia struktury ref są niejawnie konwertowane na Platform::Object ^, można zmienić jego metody ToString wirtualnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class Object : Object  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Object::Object](#ctor)|Inicjuje nowe wystąpienie klasy obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Object::Equals](#equals)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|  
|[Object::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|  
|[Object::ReferenceEquals](#referenceequals)|Określa, czy określone wystąpienia obiektów są tego samego wystąpienia.|  
|[ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt. Można zastąpić.|  
|[GetType](#gettype)|Pobiera [Platform::Type](../cppcx/platform-type-class.md) opisujący bieżącego wystąpienia.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Object`  
  
 `Object`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** vccorlib.h  
  
 **Namespace:** platformy  

  
## <a name="equals"></a> Metoda Object::Equals
Określa, czy określony obiekt jest równy bieżącemu obiektowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool Equals(  
    Object^ obj  
)  
```  
  
### <a name="parameters"></a>Parametry  
 obj  
 Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli obiekty są równe, w przeciwnym razie `false`.  
  


## <a name="gethashcode"></a>  Metoda Object::GetHashCode
Zwraca `IUnknown`* wartość tożsamości dla tego wystąpienia, jeśli jest to obiekt COM lub obliczona wartość skrótu, jeśli nie jest obiektem COM.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość liczbowa, która unikatowo identyfikuje ten obiekt.  
  
### <a name="remarks"></a>Uwagi  
 GetHashCode służy do tworzenia kluczy dla obiektów w społeczności maps. Możesz porównać kodów wartości skrótu, za pomocą [Object::Equals](#equals). Jeśli ścieżka kodu jest bardzo krytyczne i `GetHashCode` i `Equals` nie są wystarczająco szybko, możesz lista rozwijana umożliwiająca odpowiedniej warstwy modelu COM i czy natywnych `IUnknown` porównania wskaźnika.  
  


## <a name="gettype"></a>  Object::gettype — metoda
Zwraca [Platform::Type](../cppcx/platform-type-class.md) obiekt, który opisuje typ środowiska uruchomieniowego obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Object::GetType()  
```  

  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 A [Platform::Type](../cppcx/platform-type-class.md) obiekt, który opisuje typ środowiska uruchomieniowego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Statyczne [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) pozwala uzyskać [Platform::TypeCode, wyliczenie](../cppcx/platform-typecode-enumeration.md) wartość, która reprezentuje bieżący typ. Najczęściej jest to użyteczne dla wbudowanych typów. Kod typu dla każdej klasy ref, oprócz [Platform::String](../cppcx/platform-string-class.md) jest obiektem (1).  
  
 [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) klasa jest używana w interfejsach API Windows jako niezależny od języka sposób przekazywania informacji o typie między składnikami Windows i aplikacji. T[Platform::Type, klasa](../cppcx/platform-type-class.md) ma operatory konwersji między `Type` i `TypeName`.  
  
 Użyj [typeid](../windows/typeid-cpp-component-extensions.md) operator, aby zwrócić `Platform::Type` obiektu dla nazwy klasy, na przykład podczas przechodzenia między stronami XAML:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::type, klasa](../cppcx/platform-type-class.md)   
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)   
 [System typów] (.. /cppcx/Type-System-c-CX.MD
  
## <a name="ctor"></a>  Konstruktor Object::Object
Inicjuje nowe wystąpienie klasy obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:Object()  
```  

## <a name="referenceequals"></a>  Metoda Object::ReferenceEquals
Określa, czy określone wystąpienia obiektów są tego samego wystąpienia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
### <a name="parameters"></a>Parametry  
 obj1  
 Pierwszy obiekt, który ma zostać porównany.  
  
 obj2  
 Drugi obiekt, który będzie porównywany.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli dwa obiekty są takie same; w przeciwnym razie `false`.  
 
## <a name="tostring"></a>  Metoda Object::toString (C + +/ CX)
Zwraca ciąg, który reprezentuje bieżący obiekt.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg, który reprezentuje bieżący obiekt. Możesz zastąpić tę metodę, aby podać niestandardowy ciąg wiadomości w swojej klasy ref lub struktury:  
  
```cpp  
public ref class Tree sealed  
{  
public:  
    Tree(){}  
    virtual Platform::String^ ToString() override  
    {  
      return "I’m a Tree";  
    };  
};  
```  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)