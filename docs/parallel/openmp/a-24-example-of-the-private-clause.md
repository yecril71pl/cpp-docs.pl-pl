---
title: "Przykład A.24 klauzuli prywatnej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e0abd7aa296a16e54e2ec5e5ce7b2c49a93c45e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a24---example-of-the-private-clause"></a>A.24   Przykład klauzuli prywatnej
`private` Klauzuli ([sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25) równoległego regionu działa tylko w dla zakresu leksykalne regionu, a nie dla zakresu dynamicznego regionu.  W związku z tym w następującym przykładzie, wszelkie używa zmiennej *a* w `for` pętli w procedurze *f* odwołuje się do prywatnej kopii *a*, podczas użycia w Procedura *g* odwołuje się do globalnej *a*.  
  
```  
int a;  
  
void f(int n)   
{  
    a = 0;  
  
    #pragma omp parallel for private(a)  
    for (int i=1; i<n; i++)   
    {  
        a = i;  
        g(i, n);  
        d(a);     // Private copy of "a"  
        ...  
    }  
    ...  
  
void g(int k, int n)   
{  
    h(k,a); // The global "a", not the private "a" in f  
}  
```