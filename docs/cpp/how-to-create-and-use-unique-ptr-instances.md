---
title: "Porady: Tworzenie wystąpień unique_ptr i korzystanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08f597a160b3447743646c4cccfc2e05485a47b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Porady: tworzenie wystąpień unique_ptr i korzystanie z nich
A [unique_ptr](../standard-library/unique-ptr-class.md) udostępniaj go. Nie można skopiować do innego `unique_ptr`, przekazany przez wartość do funkcji lub używane w dowolny algorytm standardowa biblioteka C++ wymagającego kopie ma zostać wykonane. A `unique_ptr` tylko mogą zostać przeniesione. Oznacza to, że własności zasobów pamięci jest przenoszona do innego `unique_ptr` i oryginalny `unique_ptr` nie jest właścicielem. Zalecamy, aby ograniczyć obiekt do jednego właściciela, ponieważ wiele własności zwiększa złożoność logiki programu. W związku z tym wskaźnika inteligentnego dla obiekt zwykły C++, użyj `unique_ptr`, i kiedy utworzyć `unique_ptr`, użyj [make_unique](../standard-library/memory-functions.md#make_unique) funkcji pomocnika.  
  
 Na poniższym diagramie przedstawiono przeniesienie własności między dwiema `unique_ptr` wystąpień.  
  
 ![Przeniesienie własności unikatowego &#95; ptr](../cpp/media/unique_ptr.png "unique_ptr")  
  
 `unique_ptr`jest zdefiniowany w `<memory>` nagłówka w standardowej bibliotece C++. Jest dokładnie wydajnym jako wskaźnik pierwotnych i mogą być używane w kontenerach standardowa biblioteka C++. Dodanie `unique_ptr` wystąpień do kontenerów standardowa biblioteka C++ jest wydajne ponieważ Konstruktor przenoszenia obiektu `unique_ptr` eliminuje potrzebę stosowania operacji kopiowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia `unique_ptr` wystąpień i przekaż je pomiędzy funkcjami.  
  
 [!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]  
  
 W tych przykładach pokazano to podstawowe cech `unique_ptr`: go może być przeniesiony, ale nie został skopiowany. "Przeniesienie" przenosi prawo własności do nowego `unique_ptr` i przywraca stary `unique_ptr`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia `unique_ptr` wystąpień i używać ich w wektora.  
  
 [!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]  
  
 W zakresie pętli for, zwróć uwagę, że `unique_ptr` jest przekazywana przez odwołanie. Próba przekazania według wartości w tym miejscu kompilator zgłosi błąd, ponieważ `unique_ptr` Konstruktor kopiujący jest usuwany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować `unique_ptr` będący elementem członkowskim klasy.  
  
 [!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]  
  
## <a name="example"></a>Przykład  
 Można użyć [make_unique](../standard-library/memory-functions.md#make_unique) utworzyć `unique_ptr` do tablicy, ale nie można użyć `make_unique` zainicjować elementów tablicy.  
  
 [!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]  
  
 Aby uzyskać więcej przykładów, zobacz [make_unique](../standard-library/memory-functions.md#make_unique).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)   
 [make_unique](../standard-library/memory-functions.md#make_unique)