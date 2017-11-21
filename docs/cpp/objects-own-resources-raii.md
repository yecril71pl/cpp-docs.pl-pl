---
title: "Obiekty posiadają zasoby (RAII) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 03147ffe6d7a660469dae53944b2d62a4f08e6aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="objects-own-resources-raii"></a>Obiekty posiadają zasoby (RAII)
Upewnij się, które obiekty własnych. Ta zasada jest nazywane również "nabywania zasobów inicjowania" lub "RAII."  
  
## <a name="example"></a>Przykład  
 Przekaż każdy obiekt "new" jako argument konstruktora do innego obiektu o nazwie, posiadającym go (prawie zawsze unique_ptr).  
  
```cpp  
void f() {  
    unique_ptr<widget> p( new widget() );  
    my_class x( new widget() );  
    // ...  
} // automatic destruction and deallocation for both widget objects  
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"  
```  
  
 Zawsze natychmiast przekazać dowolnego nowego zasobu do innego obiektu, który jest jego właścicielem.  
  
```cpp  
void g() {  
    other_class y( OpenFile() );  
    // ...  
} // automatic closing and release for file resource  
  // automatic exception safety, as if "finally { y.file.dispose(); }"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)