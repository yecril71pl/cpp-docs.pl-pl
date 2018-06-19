---
title: Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfdae4791b89ffd78661a983fdc8c1beec77edea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392120"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym (C)
Zmienne zewnętrzne są zmiennymi w zakresie pliku. Są zdefiniowane poza jakąkolwiek funkcją i są potencjalnie dostępne dla wielu funkcji. Funkcje mogą być definiowane tylko na poziomie zewnętrznym i dlatego nie mogą być zagnieżdżane. Domyślnie wszystkie odwołania do zmiennych zewnętrznych i funkcji o tej samej nazwie są odwołaniami do tego samego obiektu, co oznacza, że mają one „powiązanie zewnętrzne”. (Można użyć **statycznych** słowo kluczowe, aby zastąpić. Informacje w dalszej części tej sekcji, aby uzyskać więcej informacji o **statycznych**.)  
  
 Deklaracje zmiennych na poziomie zewnętrznym są definicjami zmiennych („deklaracje definiujące”) lub odwołaniami do zmiennych określonych gdzie indziej („deklaracje odwołaniowe”).  
  
 Zewnętrzna deklaracja zmiennej, która również inicjuje zmienną (jawnie lub niejawnie) jest deklaracją definiującą zmienną. Definicja na poziomie zewnętrznym może przybierać różne formy:  
  
-   Zmienna, która deklaruje z **statycznych** Specyfikator klasy magazynowania. Można jawnie zainicjować **statycznych** zmiennej z wyrażeniem stałym, zgodnie z opisem w [inicjowania](../c-language/initialization.md). Jeżeli pominięto inicjator, zmienna jest inicjowana domyślnie na wartość 0. Na przykład, następujące dwie instrukcje są rozważane jako definicje zmiennej `k`.  
  
    ```  
    static int k = 16;  
    static int k;  
    ```  
  
-   Zmienna jawnie zainicjowana na poziomie zewnętrznym. Na przykład, `int j = 3;` jest definicją zmiennej `j`.  
  
 W deklaracji zmiennej na poziomie zewnętrzne (oznacza to, poza wszystkie funkcje), można użyć **statycznych** lub `extern` Specyfikator klasy magazynu lub całkowicie pominąć specyfikator klasy magazynowania. Nie można użyć **automatycznie** i **zarejestrować** *Specyfikator klasy magazynu* terminale na poziomie zewnętrznych.  
  
 Gdy zmienna jest zdefiniowana na poziomie zewnętrznym, jest widoczna w pozostałej części jednostki translacji. Zmienna nie jest widoczna przed jej deklaracją, w tym samym pliku źródłowym. Ponadto, nie jest widoczna w innych plikach źródłowych programu, chyba że deklaracja odwołaniowa sprawia, że staje się widoczna, jak opisano poniżej.  
  
 Zasady dotyczące **statycznych** obejmują:  
  
-   Zmienne zadeklarowane poza wszystkie bloki bez **statycznych** — słowo kluczowe zawsze zachowują swoje wartości w programie. Aby ograniczyć ich dostęp do jednostki tłumaczenia określonego, należy użyć **statycznych** — słowo kluczowe. To daje im „powiązanie wewnętrzne”. Aby stworzyć je globalnie dla całego programu, należy pominąć jawną klasę magazynu lub użyć słowa kluczowego `extern` (patrz zasady na następnej liście). To daje im „powiązanie zewnętrzne”. Połączenie wewnętrzne i zewnętrzne omówiono także w [połączenie](../c-language/linkage.md).  
  
-   Można zdefiniować zmienną na poziomie zewnętrznym tylko raz w programie. Można zdefiniować inna zmienna o takiej samej nazwie i **statycznych** Specyfikator klasy magazynu w jednostce tłumaczenia inny. Ponieważ każdy **statycznych** definicji jest widoczna tylko w obrębie własnej jednostce tłumaczenia, konflikt nie występuje. Zapewnia to przydatny sposób ukrywania nazw identyfikatorów, które muszą być udostępnione wśród funkcji pojedynczej jednostki translacji, ale nie są widoczne dla innych jednostek translacji.  
  
-   **Statycznych** Specyfikator klasy magazynowania może dotyczyć również funkcje. Jeśli zadeklarowania funkcji **statycznych**, jego nazwa jest niewidoczny poza pliku, w którym jest zadeklarowany.  
  
 Reguły korzystania z `extern` są:  
  
-   Specyfikator klasy magazynu `extern` deklaruje odwołanie do zmiennej zdefiniowanej w innym miejscu. Można użyć deklaracji `extern`, aby uwidocznić definicję w innym pliku źródłowym lub uwidocznić zmienną przed jej definicją w tym samym pliku źródłowym. Po zadeklarowaniu odwołania do zmiennej na poziomie zewnętrznym, zmienna jest widoczna w pozostałej części jednostki translacji, w której występuje zadeklarowane odwołanie.  
  
-   Aby odwołanie `extern` było prawidłowe, zmienna do której się odnosi, musi być zdefiniowana raz i tylko raz, na poziomie zewnętrznym. Ta definicja (bez klasy magazynu `extern`) może być w dowolnej jednostce translacji, tworzącej program.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje deklaracje zewnętrzne:  
  
```  
/******************************************************************  
                      SOURCE FILE ONE   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;                // Reference to i, defined below   
void next( void );           // Function prototype              
  
int main()  
{  
    i++;  
    printf_s( "%d\n", i );   // i equals 4   
    next();  
}  
  
int i = 3;                  // Definition of i  
  
void next( void )  
{  
    i++;  
    printf_s( "%d\n", i );  // i equals 5  
    other();  
}  
  
/******************************************************************  
                      SOURCE FILE TWO   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;              // Reference to i in   
                           // first source file   
void other( void )  
{  
    i++;  
    printf_s( "%d\n", i ); // i equals 6   
}  
```  
  
 Dwa pliki źródłowe w tym przykładzie zawierają łącznie trzy zewnętrzne deklaracje `i`. Tylko jedna deklaracja jest „deklaracją definiującą”. Deklaracja,  
  
```  
int i = 3;  
```  
  
 definiuje zmienną globalną `i` oraz inicjuje ją początkową wartością 3. Deklaracja „odwołaniowa” `i` w górnej części pierwszego pliku źródłowego używająca `extern` sprawia, że zmienna globalna jest widoczna przed jej deklaracją definiującą w pliku. Deklaracja odwołaniowa `i` w drugim pliku źródłowym również sprawia, że zmienna jest widoczna w tym pliku źródłowym. Jeśli wystąpienie definiujące zmiennej nie jest dostarczone w jednostce tłumaczenia, kompilator zakłada deklarację odwołaniową  
  
```  
extern int x;  
```  
  
 deklaracja odwołaniowa i oraz odwołanie definiujące  
  
```  
int x = 0;  
```  
  
 pojawia się w innej jednostce translacji programu.  
  
 Wszystkie trzy funkcje `main`, `next` i `other`, wykonują to samo zadanie: zwiększają `i` oraz drukują. Drukowane są wartości 4, 5 i 6.  
  
 Jeśli zmienna `i` nie była zainicjowana, to zostanie automatycznie ustawiona na 0. W tym przypadku byłyby wypisane wartości 1, 2 i 3. Zobacz [inicjowania](../c-language/initialization.md) informacji o zmiennych inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy magazynu w języku C](../c-language/c-storage-classes.md)