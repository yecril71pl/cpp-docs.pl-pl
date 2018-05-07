---
title: Klasa platform::Object | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7fc6dc1df1d1e22032dbe7322b9a6ead8334ddc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformobject-class"></a>Klasa platform::Object
Zapewnia zachowanie typowych ref klas i struktur ref w aplikacjach środowiska wykonawczego systemu Windows. Wszystkie klasy referencyjnej i ref struct wystąpienia są umożliwiają niejawnej konwersji na Platform::Object ^, można zmienić jego metody ToString wirtualnej.  
  
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
|[ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt. Może zostać zastąpiona.|  
|[GetType](#gettype)|Pobiera [Platform::Type](../cppcx/platform-type-class.md) opisujący bieżącego wystąpienia.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Object`  
  
 `Object`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** vccorlib.h  
  
 **Namespace:** platformy  

  
## <a name="equals"></a> Object::Equals — metoda
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
 `true` Jeśli obiekty są takie same, w przeciwnym razie `false`.  
  


## <a name="gethashcode"></a>  Object::GetHashCode — metoda
Zwraca `IUnknown`* wartości tożsamości dla tego wystąpienia, jeśli jest to obiekt COM lub jeśli nie jest obiektem COM. wartość obliczoną wartość mieszania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość liczbowa unikatowo identyfikujący ten obiekt.  
  
### <a name="remarks"></a>Uwagi  
 GetHashCode służy do tworzenia kluczy dla obiektów w społeczności maps. Możesz porównać skrótu za pomocą [Object::Equals](#equals). Jeśli ścieżka kodu jest bardzo krytyczne i `GetHashCode` i `Equals` nie są wystarczająco szybkie, możesz listy rozwijanej do odpowiedniej warstwy modelu COM i czy natywnego `IUnknown` porównania wskaźnika.  
  


## <a name="gettype"></a>  Object::gettype — metoda
Zwraca [Platform::Type](../cppcx/platform-type-class.md) obiektu, który opisuje typ obiektu środowiska wykonawczego.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Object::GetType()  
```  

  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 A [Platform::Type](../cppcx/platform-type-class.md) obiektu, który opisuje typ środowiska uruchomieniowego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Statycznych [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) może służyć do pobrania [wyliczenie Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) wartość, która reprezentuje bieżący typ. Najczęściej jest to przydatne dla wbudowanych typów. Kod typu dla klasy ref oprócz [Platform::String](../cppcx/platform-string-class.md) obiektu (1).  
  
 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) klasa jest używana w interfejsów API systemu Windows jako niezależny od języka umożliwia przekazywanie informacji o typie między składniki systemu Windows i aplikacjami. T[klasy Platform::Type](../cppcx/platform-type-class.md) ma operatory konwersji między `Type` i `TypeName`.  
  
 Użyj [typeid](../windows/typeid-cpp-component-extensions.md) operatora, aby zwrócić `Platform::Type` obiektu dla nazwy klasy, na przykład podczas nawigowania między stronami XAML:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa platform::type](../cppcx/platform-type-class.md)   
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)   
 [Systemu typów] (.. /cppcx/Type-System-c-CX.MD
  
## <a name="ctor"></a>  Konstruktor Object::Object
Inicjuje nowe wystąpienie klasy obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:Object()  
```  

## <a name="referenceequals"></a>  Object::ReferenceEquals — metoda
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
 Ciąg, który reprezentuje bieżący obiekt. Można zastąpić tę metodę, aby podać niestandardowy ciąg wiadomości w swojej klasy referencyjnej lub struktury:  
  
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