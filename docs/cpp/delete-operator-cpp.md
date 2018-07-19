---
title: delete — Operator (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
dev_langs:
- C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89ad061dc2be090abbcfbc147f1ea5fbddb8ae6a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947774"
---
# <a name="delete-operator-c"></a>delete — Operator (C++)
Zwalnia blok pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie cast* argument musi być wskaźnikiem do bloku pamięci uprzednio przydzielonej dla obiektu, który został utworzony za pomocą [operatora new](../cpp/new-operator-cpp.md). **Usuń** operator ma wynik o typie **void** i dlatego nie zwraca wartości. Na przykład:  
  
```cpp 
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 Za pomocą **Usuń** na wskaźnik do obiektu nie jest przydzielony za pomocą **nowe** daje nieprzewidziane wyniki. Można jednak użyć **Usuń** we wskaźniku o wartości 0. Postanowienie to oznacza, że gdy **nowe** zwraca wartość 0 w przypadku awarii, wynik nie powiodło się usunięcie **nowe** operacji jest nieszkodliwe. Zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md) Aby uzyskać więcej informacji.  
  
 **Nowe** i **Usuń** również można używać operatorów dla typów wbudowanych, łącznie z tablic. Jeśli `pointer` odwołuje się do tablicy miejscu puste nawiasy przed `pointer`:  
  
```cpp 
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 Za pomocą **Usuń** operator na obiekcie powoduje cofnięcie przydziału pamięci. Program, który wyłuskania wskaźnika, po usunięciu obiektu może mieć nieoczekiwane wyniki lub awarii.  
  
 Gdy **Usuń** jest używany, można cofnąć alokacji pamięci dla obiektu klasy C++, destruktor obiektu jest wywoływana przed pamięci obiektu cofnięciu przydziału (Jeśli obiekt ma destruktora).  
  
 Jeśli argument przekazywany do **Usuń** operator jest modyfikowalną l wartością, jego wartość jest niezdefiniowana, po usunięciu obiektu.  
  
## <a name="using-delete"></a>Używanie opcji usuwania  
 Istnieją dwa warianty składni dla [delete operator](../cpp/delete-operator-cpp.md): jeden dla pojedynczych obiektów, a drugi dla tablic obiektów. Poniższy fragment kodu przedstawia, jak różnią się one:  
  
```cpp 
// expre_Using_delete.cpp  
struct UDType   
{  
};  
  
int main()  
{  
   // Allocate a user-defined object, UDObject, and an object  
   //  of type double on the free store using the  
   //  new operator.  
   UDType *UDObject = new UDType;  
   double *dObject = new double;  
   // Delete the two objects.  
   delete UDObject;  
   delete dObject;   
   // Allocate an array of user-defined objects on the  
   // free store using the new operator.  
   UDType (*UDArr)[7] = new UDType[5][7];  
   // Use the array syntax to delete the array of objects.  
   delete [] UDArr;  
}  
```  
  
 Następujące dwa przypadki dać niezdefiniowane wyniki: użycia formularza tablicy DELETE (Usuń) []) do obiektu i za pomocą formularza nietablicowe DELETE w tablicy.  
  
## <a name="example"></a>Przykład  
 Aby uzyskać przykłady użycia **Usuń**, zobacz [operatora new](../cpp/new-operator-cpp.md).  
  
## <a name="how-delete-works"></a>Jak działa słowo kluczowe delete  
 Delete operator wywołuje funkcję **operatora delete**.  
  
 Dla obiektów nie typu klasy ([klasy](../cpp/class-cpp.md), [struktury](../cpp/struct-cpp.md), lub [Unii](../cpp/unions.md)), operatora delete globalny jest wywoływany. Dla obiektów typu klasy nazwą funkcji dezalokacji został rozwiązany w zakresie globalnym, jeśli wyrażenie usunięcia zaczyna się od jednoargumentowego operatora rozpoznawania zakresu (:). W przeciwnym razie operatora delete wywołuje destruktor obiektu przed cofanie przydziału pamięci (jeśli jest to wskaźnik nie jest równa null). Delete operator mogą być definiowane na podstawie klasy; Jeśli istnieje taka definicja dla danej klasy, globalny operator delete jest wywoływana. Jeśli wyrażenie usunięcia umożliwia cofnięcie przydziału obiektu klasy, którego typu statycznego ma destruktor wirtualny, dezalokacji funkcji jest rozpoznawane za pomocą destruktor wirtualny typu dynamicznego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [new i delete, operatory](../cpp/new-and-delete-operators.md)   
 
