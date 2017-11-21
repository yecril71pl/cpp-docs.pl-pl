---
title: Funkcje rekursywne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cca28b41b15ae14504ac5692a3e8a7063a11e862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recursive-functions"></a>Funkcje rekursywne
Dowolnej funkcji programu C można wywołać rekursywnie; oznacza to, że może wywołać się. Liczba wywołań cyklicznych jest ograniczona do rozmiaru stosu. Zobacz [/STACK (twórz stos z alokacji)](../build/reference/stack-stack-allocations.md) (/ STACK) — opcja konsolidatora informacji o konsolidatora opcje tego Ustaw rozmiar stosu. Każdorazowo po wywołaniu funkcji nowego magazynu jest przydzielona dla parametrów i **automatycznie** i **zarejestrować** zmienne, tak aby ich wartości w poprzedniej, niedokończone wywołania nie zostaną zastąpione. Parametry są tylko bezpośrednio dostępny dla wystąpienia funkcji, w którym są tworzone. Poprzednie parametry nie są bezpośrednio dostępne dla następujących wystąpień funkcji.  
  
 Należy pamiętać, że zmienne zadeklarowane z **statycznych** magazynu nowego magazynu z każde wywołanie cykliczne nie jest wymagana. Okres istnienia program istnieje ich magazyn. Każde odwołanie do zmiennej takie uzyskuje dostęp do tego samego obszaru magazynu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wywołania cykliczne:  
  
```  
int factorial( int num );      /* Function prototype */  
  
int main()  
{  
    int result, number;  
    .  
    .  
    .  
    result = factorial( number );  
}  
  
int factorial( int num )      /* Function definition */  
{  
    .  
    .  
    .  
    if ( ( num > 0 ) || ( num <= 10 ) )  
        return( num * factorial( num - 1 ) );  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji](../c-language/function-calls.md)