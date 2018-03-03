---
title: "Odwołania (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7453fbab0ade6cfe2cbdd836d7d59ba49c3ccfd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="references-c"></a>Odwołania (C++)
Odwołanie, takie jak wskaźnik, przechowuje adres obiektu, który znajduje się w innym miejscu w pamięci. W przeciwieństwie do wskaźnika, po jego inicjowania nie można odwołać się do odwoływać się do innego obiektu lub wartość null. Istnieją dwa rodzaje odwołań: odwołania l-wartości, których dotyczą odwołania o nazwie zmiennej i r-wartości, które odnoszą się do [tymczasowy obiekt](../cpp/temporary-objects.md). & — Operator oznacza, że odwołania do wartości i & & — operator oznacza, że odwołanie do r-wartości lub uniwersalnych odwołanie (r-wartości lub l-wartością) w zależności od kontekstu.  
  
 Odwołania mogą być deklarowane przy użyciu następującej składni:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator [= expression];  
```  
  
 Mogą być używane wszystkie nieprawidłowy deklarator określenie odwołania. Chyba, że odwołanie jest odwołanie do funkcji lub dotyczy następującej składni uproszczoną typu tablicy:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&]   
[cv-qualifiers] identifier [= expression];  
```  
  
 Odwołania są zadeklarowane za pomocą następującej kolejności:  
  
 1. Specyfikatory deklaracji:  
  
-   Specyfikator klasy magazynu opcjonalne.  
  
-   Opcjonalne **const** i/lub `volatile` kwalifikatorów.  
  
-   Specyfikator typu: Nazwa typu.  
  
-   2. Deklarator:  
  
-   Opcjonalne Microsoft określonych modyfikatora. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   & — Operator lub & & — operator.  
  
-   Opcjonalne **const** i/lub `volatile` kwalifikatorów.  
  
-   Identyfikator.  
  
 3. Opcjonalne inicjatora.  
  
 Bardziej złożone formularze deklarator wskaźniki do tablic i funkcje mają też zastosowanie do odwołania do tablic i funkcji, zobacz [wskaźniki](../cpp/pointers-cpp.md) i [deklaratorów](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
 Wiele deklaratorów i inicjatory może pojawić się na liście rozdzielanej przecinkami po specyfikator jednej deklaracji. Na przykład:  
  
```  
int &i;   
int &i, &j;   
```  
  
 Odwołania, wskaźniki i obiekty mogą być zadeklarowane jednocześnie:  
  
```  
int &ref, *ptr, k;   
```  
  
 Odwołanie przechowuje adres obiektu, ale składniowo zachowuje się jak obiektu.  
  
 W programie następujące, zwróć uwagę, że nazwa obiektu, `Today`i odwołania do obiektu, `TodayRef`, można używać tak samo w programach:  
  
## <a name="example"></a>Przykład  
  
```  
// references.cpp  
#include <stdio.h>  
struct S {  
   short i;  
};  
  
int main() {  
   S  s;   // Declare the object.  
   S& SRef = s;   // Declare the reference.  
   s.i = 3;  
  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
  
   SRef.i = 4;  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
}  
```  
  
```Output  
3  
3  
4  
4  
```  
  
## <a name="comment"></a>Komentarz  
 Tematy w tej sekcji:  
  
-   [Argumenty funkcji będące odwołaniami](../cpp/reference-type-function-arguments.md)  
  
-   [Wartości zwracane przez funkcje będące odwołaniami](../cpp/reference-type-function-returns.md)  
  
-   [Odwołania do wskaźników](../cpp/references-to-pointers.md)  
  
