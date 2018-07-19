---
title: extern — Specyfikator klasy magazynowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 365f4cf424ee51c493859e1d79f733b2cfcf331c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964187"
---
# <a name="extern-storage-class-specifier"></a>extern — specyfikator klasy magazynowania

Zmienna zadeklarowana ze **extern** Specyfikator klasy magazynowania jest odwołanie do zmiennej o tej samej nazwie, które są zdefiniowane w innym pliku źródłowym. Jest on używany aby uwidocznić definicję zmiennej poziomu zewnętrznego. Zmienna zadeklarowana jako **extern** nie ma magazyn jest przydzielany dla siebie; jest tylko nazwę. 
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje deklaracje na poziomie wewnętrznym i zewnętrznym:  
  
```c  

// Source1.c  

int i = 1;


// Source2. c

#include <stdio.h>  

// Refers to the i that is defined in Source1.c:   
extern int i;

void func(void);

int main()
{
    // Prints 1:   
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:   
    int i = 16;

    // Prints 16, 1:  
    printf_s("%d\n%d\n", i, *external_i);
}
```  
  
 W tym przykładzie zmienna `i` jest zdefiniowany w Source1.c o początkowej wartości 1. **Extern** deklaracji w Source2.c to sprawia, że "i" widoczne w tym pliku. 

 W `func` funkcji, adres zmiennej globalnej `i` służy do inicjowania **statyczne** zmiennej wskaźnikowej `external_i`. To działa, ponieważ zmienna globalna ma **statyczne** okres istnienia, co oznacza jego adres nie zmienia się podczas wykonywania programu. Następnie, zmienna `i` jest zdefiniowany w zakresie `func` jako zmienna lokalna o wartości początkowej 16. Ta definicja nie ma wpływu na wartość poziomu zewnętrznego `i`, który jest ukryty przy użyciu jego nazwy zmiennej lokalnej. Wartość globalna `i` jest teraz dostępna wyłącznie za pośrednictwem wskaźnik `external_i`.   
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md)