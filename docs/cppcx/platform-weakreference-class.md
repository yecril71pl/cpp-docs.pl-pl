---
title: Klasa platform::WeakReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c161bf901b0e055885858d8570925f58e2eb971a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformweakreference-class"></a>Klasa platform::WeakReference
Reprezentuje słabe odwołanie do wystąpienia klasy ref.  
  
## <a name="syntax"></a>Składnia  
  
```cpp 
class WeakReference  
```  
  
#### <a name="parameters"></a>Parametry  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Weakreference::weakreference —](#ctor)|Inicjuje nowe wystąpienie klasy weakreference —.|  
  
### <a name="methods"></a>Metody  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[WeakReference::Resolve](#resolve)|Zwraca uchwyt do podstawowej klasy referencyjnej lub nullptr, jeśli ten obiekt już istnieje.|  
  
### <a name="operators"></a>Operatory  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[WeakReference::operator =](#operator-assign)|Przypisuje nową wartość do obiektu weakreference —.|  
|[WeakReference::operator BoolType](#booltype)|Implementuje wzorzec bool bezpieczne.|  
  
### <a name="remarks"></a>Uwagi  
 Weakreference — klasa nie jest klasa ref i dlatego nie dziedziczy on Platform::Object ^ i nie można używać w podpisie metody publicznej.  

## <a name="operator-assign"></a>WeakReference::operator =
Przypisuje wartość do weakreference —.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));    
WeakReference& operator=(const WeakReference& otherArg);   
WeakReference& operator=(WeakReference&& otherArg);    
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg); 
```  
  
### <a name="remarks"></a>Uwagi  
 Ostatni przeciążenia na powyższej liście umożliwia przypisanie klasy ref ze zmienną weakreference —. W takim przypadku klasa ref jest przypisanie elementu podrzędnego do [Platform::Object](../cppcx/platform-object-class.md)^. Później przywrócić oryginalny typ określając jako argumentu dla parametru typu w [WeakReference::Resolve\<T >](#resolve) funkcję elementu członkowskiego.  
  
## <a name="booltype"></a>WeakReference::operator BoolType
Implementuje wzorzec bezpieczne bool weakreference — klasa. Nie można wywoływać bezpośrednio w kodzie.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
BoolType BoolType()  
```  

## <a name="resolve"></a>WeakReference::Resolve — metoda (przestrzeń nazw platformy)
Zwraca dojście do oryginalnej klasy ref lub `nullptr` Jeśli ten obiekt już istnieje.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
template<typename T>  
T^ Resolve() const  
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Dojście do obiektu weakreference — został poprzednio powiązany z klasy ref lub nullptr.  
  
### <a name="example"></a>Przykład  
 Jest to opis przykładowego kodu.  
  
```  
  
Bar^ bar = ref new Bar();  
//use bar...  
  
if (bar != nullptr)  
{  
    WeakReference wr(bar);  
    Bar^ newReference = wr.Resolve<Bar>();  
}  
```  
  
 Należy pamiętać, że parametr typu T, T nie ^.  
  
 
## <a name="ctor"></a>Weakreference::weakreference — Konstruktor
Udostępnia różne sposoby tworzenia weakreference —.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
WeakReference();  
WeakReference(decltype(__nullptr));  
WeakReference(const WeakReference& otherArg);  
WeakReference(WeakReference&& otherArg);  
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);  
```  
### <a name="example"></a>Przykład  
  
```cpp    
MyClass^ mc = ref new MyClass();  
WeakReference wr(mc);  
MyClass^ copy2 = wr.Resolve<MyClass>();    
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)