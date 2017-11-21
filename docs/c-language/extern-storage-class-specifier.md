---
title: "extern Specyfikator klasy składującej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f11789f985c67b59b076bed7ec849a864688743
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="extern-storage-class-specifier"></a>extern — specyfikator klasy magazynowania
Zmienna zadeklarowana ze specyfikatorem klasy magazynu `extern` jest odwołaniem do zmiennej o tej samej nazwie, zdefiniowanej na poziomie zewnętrznym w dowolnym z plików źródłowych programu. Wewnętrzna deklaracja `extern` jest używana, aby uwidocznić definicję zmiennej poziomu zewnętrznego w bloku. O ile nie została zgłoszona na poziomie zewnętrznym, zmienna zadeklarowana ze słowem kluczowym `extern` jest widoczna tylko w bloku, w którym jest zadeklarowana.  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje deklaracje na poziomie wewnętrznym i zewnętrznym:  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 W tym przykładzie zmienna `i` jest zdefiniowana na poziomie zewnętrznym z wartością początkową 1. Deklaracja `extern` w funkcji `main` jest używana do zadeklarowania odwołania do poziomu zewnętrznego `i`. **Statycznych** zmiennej `a` jest ustawiana na 0 domyślnie, ponieważ pominięto inicjatora. Wywołanie `printf` drukuje wartości 1, 0, 0 i 0.  
  
 W `other` funkcja, adres zmiennej globalnej `i` służy do inicjowania **statycznych** zmiennej wskaźnikowej `external_i`. To działa, ponieważ ma zmiennej globalnej **statycznych** okres istnienia, co oznacza jego adres nie zmienia się podczas wykonywania programu. Następnie, zmienna `i` jest ponownie definiowana jako zmienna lokalna o wartości początkowej 16. To ponowne zdefiniowanie nie wpływa na wartość poziomu zewnętrznego `i`, który jest ukryty przy użyciu jego nazwy zmiennej lokalnej. Wartość globalna `i` jest teraz dostępna tylko pośrednio w ramach tego bloku, poprzez wskaźnik `external_i`. Spróbuje przypisać adres **automatycznie** zmiennej `i` na wskaźnik nie działa, ponieważ może być inny zawsze jest wprowadzana bloku. Zmienna `a` jest zadeklarowany jako **statycznych** zmiennej i została zainicjowana na 2. To `a` nie powoduje konfliktu z `a` w `main`, ponieważ **statycznych** zmienne na poziomie wewnętrznym są widoczne tylko w bloku, w którym je zadeklarowano.  
  
 Zmienna `a` jest zwiększana o 2, dając w wyniku 4. Jeśli funkcja `other` była nazywana ponownie w tym samym programie, początkowa wartość `a` wynosi 4. Wewnętrzny **statycznych** zmienne zachować ich wartości, gdy program kończy działanie, a następnie reenters bloku, w którym je zadeklarowano.  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md)