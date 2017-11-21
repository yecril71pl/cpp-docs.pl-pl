---
title: "Powiązanie A.20 dyrektyw bariery | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8d88c431753d918c05866324dd6436a091d6057a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   Powiązanie dyrektyw określających bariery
Powiązania dyrektywy zasady wywołania dla **bariery** dyrektywy powiązać najbliższej otaczającej `parallel` dyrektywy. Aby uzyskać więcej informacji na powiązania dyrektywy, zobacz [2.8 sekcji](../../parallel/openmp/2-8-directive-binding.md) na stronie 32.  
  
 W poniższym przykładzie, wywołanie z *głównego* do *sub2* jest zgodny, ponieważ **bariery** (w *sub3*) wiąże równoległego regionu w *sub2*. Wywołania z *głównego* do *sub1* jest zgodny z ponieważ **bariery** wiąże równoległego regionu w podprocedury *sub2*.  Wywołania z *głównego* do *sub3* jest zgodny z ponieważ **bariery** nie jest powiązana z dowolnym równoległego regionu i jest ignorowana. Należy również zauważyć, że **bariery** synchronizuje tylko zespołu wątków w otaczającym równoległego regionu i nie wszystkie wątki utworzone w *sub1*.  
  
```  
int main()  
{  
    sub1(2);  
    sub2(2);  
    sub3(2);  
}  
  
void sub1(int n)  
{  
    int i;  
    #pragma omp parallel private(i) shared(n)  
    {  
        #pragma omp for  
        for (i=0; i<n; i++)  
            sub2(i);  
    }  
}  
  
void sub2(int k)  
{  
     #pragma omp parallel shared(k)  
     sub3(k);  
}  
  
void sub3(int n)  
{  
    work(n);  
    #pragma omp barrier  
    work(n);  
}  
```