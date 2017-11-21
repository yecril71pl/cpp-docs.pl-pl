---
title: "Przykłady A.19 przedstawiający niepoprawne zagnieżdżanie dyrektywy podziału pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1cc5ed3a3a5ddd4117a3332703613a8d525853a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Przykłady pokazujące nieprawidłowe zagnieżdżanie dyrektyw podziału pracy
Przykłady w tej sekcji przedstawiono dyrektywy reguły zagnieżdżenia. Aby uzyskać więcej informacji na zagnieżdżanie dyrektywy, zobacz [2.9 sekcji](../../parallel/openmp/2-9-directive-nesting.md) na stronie 33.  
  
 Poniższy przykład jest niezgodne ponieważ wewnętrznych i zewnętrznych `for` dyrektywy są zagnieżdżone i ich powiązania do tej samej `parallel` dyrektywy:  
  
```  
void wrong1(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
      int i, j;  
      #pragma omp for  
      for (i=0; i<n; i++) {  
          #pragma omp for  
              for (j=0; j<n; j++)  
                 work(i, j);  
     }  
   }  
}  
```  
  
 Następująca wersja dynamicznie zagnieżdżonych poprzedniego przykładu jest również niezgodne:  
  
```  
void wrong2(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++)  
        work1(i, n);  
  }  
}  
  
void work1(int i, int n)  
{  
  int j;  
  #pragma omp for  
    for (j=0; j<n; j++)  
      work2(i, j);  
}  
```  
  
 Poniższy przykład jest niezgodne ponieważ `for` i `single` dyrektywy są zagnieżdżone i powiązania tego samego równoległego regionu:  
  
```  
void wrong3(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        #pragma omp single  
          work(i);  
      }  
  }  
}  
```  
  
 Poniższy przykład jest niezgodne ponieważ `barrier` dyrektywy wewnątrz `for` może spowodować zakleszczenie:  
  
```  
void wrong4(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        work1(i);  
        #pragma omp barrier  
        work2(i);  
      }  
  }  
}  
```  
  
 Poniższy przykład jest niezgodne ponieważ `barrier` powoduje zakleszczenie z faktu, że tylko jeden wątek jednocześnie można wprowadzić sekcji krytycznej:  
  
```  
void wrong5()  
{  
  #pragma omp parallel  
  {  
    #pragma omp critical  
    {  
       work1();  
       #pragma omp barrier  
       work2();  
    }  
  }  
}  
```  
  
 Poniższy przykład jest niezgodne ponieważ `barrier` powoduje zakleszczenie z faktu, że tylko jeden wątek wykonuje `single` sekcji:  
  
```  
void wrong6()  
{  
  #pragma omp parallel  
  {  
    setup();  
    #pragma omp single  
    {  
      work1();  
      #pragma omp barrier  
      work2();  
    }  
    finish();  
  }  
}  
```