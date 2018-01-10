---
title: Deklaracja tablicy CLR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3f263227d437ddafb65ac3da0829414e4af05855
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-clr-array"></a>Deklaracja tablicy CLR
Składnia deklaracji, tworzenie wystąpień i Inicjowanie tablicy zarządzanej zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Deklaracja obiektu CLR tablicy w zarządzanych rozszerzeń zostało rozszerzenie deklaracji standardowe tablicy, w którym `__gc` umieszczenia między nazwą obiektu array i jego wymiaru prawdopodobnie wypełnione przecinkami, tak jak z następującą parą — słowo kluczowe Przykłady:  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 To jest teraz prostszy w nowej składni, w której używamy deklaracji szablonu przypominającej podobne do standardowej biblioteki C++ `vector` deklaracji. Pierwszy parametr określa typ elementu. Drugi parametr określa wymiar tablicy (z domyślną wartość 1, dlatego tylko wielu wymiarów wymagają drugi argument). Sam obiekt tablicy jest dojścia śledzenia i dlatego należy podać hat. Jeśli typ elementu również jest typem referencyjnym, wymagany jest również hat. Na przykład powyższy przykład wyrażone w nowej składni wygląda następująco:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 Ponieważ śledzenie dojścia zamiast obiektu jest typ odwołania, jest można określić tablicy CLR jako zwracany typ funkcji. (Z kolei go nie jest możliwe określenie natywna tablica jako zwracany typ funkcji.) Aby to zrobić w zarządzanych rozszerzeń było nieco nieintuicyjnych. Na przykład:  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 W programie Visual C++ deklaracji jest znacznie prostsze. Na przykład  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 Inicjowanie skrócona lokalnej tablicy jest obsługiwana w obu wersjach językowych. Na przykład:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 znacznie upraszcza w nowej składni (należy pamiętać, że ponieważ opakowanie jest niejawne w nowej składni `__box` operator został wyeliminowany — zobacz [typów wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) omówienie):  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 Ponieważ tablicy jest typu odwołania CLR, deklaracja każdego obiektu tablicy jest śledzenie dojścia. W związku z tym tablicy obiektów musi zostać przydzielone na stercie CLR. (Skróconej notacji ukrywa alokacji sterty zarządzanej). Oto jawnej postaci inicjowanie obiektu tablicy w obszarze rozszerzeń zarządzanych:  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 W obszarze nowej składni `new` wyrażenie jest zastępowany `gcnew`. Rozmiary wymiaru są przekazywane jako parametry `gcnew` wyrażenie w następujący sposób:  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 W nowej składni, można wykonać listy Jawne inicjowanie `gcnew` wyrażenie; to nie jest obsługiwana w zarządzanych rozszerzeń. Na przykład:  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Tablice](../windows/arrays-cpp-component-extensions.md)