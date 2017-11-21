---
title: Efekty uboczne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 687a5ad1327e1a36a2b854c8a3fcb03d8f45e104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="side-effects"></a>Efekty uboczne
Kolejność ocen wyrażeń jest definiowana za pomocą konkretnej implementacji, z wyjątkiem, gdy język gwarantuje kolejność ocen (zgodnie z opisem w [hierarchia i kolejność obliczania](../c-language/precedence-and-order-of-evaluation.md)). Na przykład efekty uboczne wystąpić w następujących wywołania funkcji:  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 Argumenty wywołania funkcji może przyjąć w dowolnej kolejności. Wyrażenie `i + 1` może zostać obliczone przed `i = j + 2`, lub `i = j + 2` może zostać obliczone przed `i + 1`. Wynik różni się w każdym przypadku. Podobnie nie jest możliwe zapewnienie co znaki są przekazywane do `myproc`. Ponieważ jednoargumentowy inkrementacja i dekrementacja operacje obejmują przypisania, takich działań mogą powodować efekty uboczne, jak pokazano w poniższym przykładzie:  
  
```  
x[i] = i++;  
```  
  
 W tym przykładzie wartość `x` czyli zmodyfikowane będzie nieprzewidywalny. Wartość indeks dolny może być nowy lub Poprzednia wartość `i`. Wynik może się różnić w różnych kompilatory lub optymalizacji różnych poziomów.  
  
 Ponieważ C nie definiuje kolejność oceniania efekty uboczne, obu opisanych wyżej metod oceny są poprawne, i albo mogą być wykonywane. Aby upewnić się, że kod jest przenośnych i usuń zaznaczenie, należy unikać instrukcji, które są zależne od określonej kolejności szacowania dla efekty uboczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Szacowanie wyrażeń](../c-language/expression-evaluation-c.md)