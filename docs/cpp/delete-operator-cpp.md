---
title: "delete — Operator (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: delete_cpp
dev_langs: C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9b12d0e20ebb355eb8422784ae0921f693279117
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="delete-operator-c"></a>delete — Operator (C++)
Zwalnia blok pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie cast* argument musi być wskaźnik do bloku pamięci przydzielona wcześniej utworzone za pomocą obiektu [operatora new](../cpp/new-operator-cpp.md). **Usunąć** operator ma wynik typu `void` i dlatego nie zwraca wartości. Na przykład:  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 Przy użyciu **usunąć** na wskaźnik do obiektu nie jest przydzielony z **nowe** daje nieprzewidziane wyniki. Można jednak użyć **usunąć** na wskaźnika o wartości 0. Postanowienie to oznacza, że podczas **nowe** zwraca wartość 0 w przypadku niepowodzenia usuwania wynik nieudanej **nowe** operacji jest bezpieczne. Zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md) Aby uzyskać więcej informacji.  
  
 **Nowe** i **usunąć** operatorów można używać dla wbudowanych typów, w tym tablic. Jeśli `pointer` odwołuje się do tablicy, miejsce puste nawiasy przed `pointer`:  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 Przy użyciu **usunąć** operator obiektu zwalnia jego pamięci. Program, który wyłuskań wskaźnik po usunięciu obiektu może mieć nieprzewidywalne skutki lub awarii.  
  
 Gdy **usunąć** jest używana, można cofnąć alokacji pamięci dla obiekt klasy C++, destruktor obiektu jest wywoływany przed (Jeśli obiekt ma destruktor) cofnięciu przydziału pamięci obiektu.  
  
 Jeśli argument operacji do **usunąć** operator jest modyfikowalną l wartość, a jego wartość nie jest zdefiniowana, po usunięciu obiektu.  
  
## <a name="using-delete"></a>Używanie opcji usuwania  
 Istnieją dwie odmiany składni dla [delete operator](../cpp/delete-operator-cpp.md): jeden dla pojedynczych obiektów, a drugą dla tablic obiektów. Poniższy fragment kodu przedstawia, jak różnią się one:  
  
```  
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
  
 Gdy dwa dać niezdefiniowane wyniki: użycia formularza tablicy DELETE (delete []) w obiekcie i za pomocą formularza nietablicowe DELETE na tablicy.  
  
## <a name="example"></a>Przykład  
 Przykłady użycia **usunąć**, zobacz [operatora new](../cpp/new-operator-cpp.md).  
  
## <a name="how-delete-works"></a>Jak działa słowo kluczowe delete  
 Delete operator wywołuje funkcję **operatora delete**.  
  
 Dla obiektów klasy innego typu ([klasy](../cpp/class-cpp.md), [struktury](../cpp/struct-cpp.md), lub [Unii](../cpp/unions.md)), operatora delete globalny jest wywoływany. W przypadku obiektów typu klasy nazwa funkcja cofania alokacji zostanie rozwiązana w zakresie globalnym, jeśli wyrażenie usunięcia rozpoczyna się od Jednoargumentowy operator rozpoznawania zakresów (:). W przeciwnym razie operatora delete wywołuje destruktor obiektu przed cofanie przydziału pamięci (jeśli jest to wskaźnik nie jest pusta). Delete operator można zdefiniować na podstawie na klasy; Jeśli nie taka definicja dla danej klasy, Usuń operator globalny jest wywoływany. Użycie wyrażenia usuwania można cofnąć alokacji obiektu klasy, których typ statyczny ma destruktor wirtualny funkcja dezalokacji został rozwiązany przez destruktor wirtualny dynamicznych typu obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [nowe i delete — operatory](../cpp/new-and-delete-operators.md)   
 
