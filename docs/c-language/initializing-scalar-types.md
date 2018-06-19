---
title: Inicjowanie typów skalarnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fef7356768a594694e0fcf3415c66ef63568a7cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392364"
---
# <a name="initializing-scalar-types"></a>Inicjowanie typów skalarnych
Podczas inicjowania skalarną typy, wartość *wyrażenia przypisania* jest przypisany do zmiennej. Zastosuj reguły konwersji dla przypisania. (Zobacz [konwersje typów](../c-language/type-conversions-c.md) Aby uzyskać informacje dotyczące reguły konwersji.)  
  
## <a name="syntax"></a>Składnia  
 `declaration`:  
 *Specyfikatory deklaracji w init listy deklarator* opt **;**  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init — deklarator — lista***,***init deklarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *deklarator***=***inicjatora* / * dla inicjowania skalarne \*/  
  
 *Inicjator*:  
 *assignment-expression*  
  
 Należy zainicjować zmienne dowolnego typu, pod warunkiem, że należy przestrzegać następujących reguł:  
  
-   Można zainicjować zmienne zadeklarowane na poziomie zakresu pliku. Jeśli jawnie nie zainicjować zmiennej na poziomie zewnętrznych, domyślnie jest inicjowany do 0.  
  
-   Wyrażenie stałe może służyć do zainicjowania wszelkie globalne Zmienna zadeklarowana ze **statycznych** *Specyfikator klasy magazynu*. Zmienne zadeklarowane jako **statycznych** są inicjowane po rozpoczęciu wykonywania programu. Jeśli użytkownik nie jawnie zainicjować globalnym **statycznych** zmiennej, jest inicjowany do 0 domyślnie i każdego elementu, który ma typ wskaźnika jest przypisany wskaźnika o wartości null.  
  
-   Zmiennych zadeklarowano za **automatycznie** lub **zarejestrować** Specyfikator klasy magazynowania są inicjowane zawsze przekazuje wykonywania kontroli do bloku, w którym je zadeklarowano. W przypadku pominięcia inicjatora z deklaracji **automatycznie** lub **zarejestrować** zmiennej, początkowej wartości zmiennej jest niezdefiniowany. Automatyczne i wartości rejestru, Inicjator nie jest ograniczone do jest stałą; może być dowolne wyrażenie obejmujące wcześniej zdefiniowanymi wartościami, wywołania funkcji nawet.  
  
-   Wartości początkowe dla zewnętrznych deklaracji zmiennych i wszystkie **statycznych** zmiennych, czy zewnętrznym lub wewnętrznym, musi być wyrażenia stałe. (Aby uzyskać więcej informacji, zobacz [wyrażenia stałe](../c-language/c-constant-expressions.md).) Ponieważ adresu żadnych zewnętrznie zadeklarowane lub statycznej zmiennej jest stałe, może służyć do zainicjowania wewnętrznie zadeklarowane **statycznych** zmiennej wskaźnikowej. Jednak adres **automatycznie** nie można użyć zmiennej jako inicjator statyczny, ponieważ mogą być różne dla każdego wykonywania bloku. Aby zainicjować można użyć wartości stałej lub zmiennej **automatycznie** i **zarejestrować** zmiennych.  
  
-   Jeśli deklarację identyfikatora ma zasięg bloku, a identyfikator ma połączenie zewnętrzne, deklaracja nie może mieć inicjowania.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają inicjalizacji:  
  
```  
int x = 10;   
```  
  
 Zmienna całkowitoliczbowa `x` jest ustawiana na wyrażeniu stałym `10`.  
  
```  
register int *px = 0;  
```  
  
 Wskaźnik `px` jest ustawiana na 0, tworzenie wskaźnika o "wartości null".  
  
```  
const int c = (3 * 1024);  
```  
  
 W tym przykładzie użyto wyrażenia stałego `(3 * 1024)` zainicjować `c` wartość stałą, której nie można modyfikować z powodu **const** — słowo kluczowe.  
  
```  
int *b = &x;  
```  
  
 Ta instrukcja inicjuje wskaźnik `b` adres innej zmiennej `x`.  
  
```  
int *const a = &z;  
```  
  
 Wskaźnik `a` jest inicjowany z adresu zmiennej o nazwie `z`. Jednakże, ponieważ jest określony jako **const**, zmienna `a` można zainicjować tylko, nigdy nie został zmodyfikowany. Zawsze punktów w tej samej lokalizacji.  
  
```  
int GLOBAL ;  
  
int function( void )  
{  
    int LOCAL ;  
    static int *lp = &LOCAL;   /* Illegal initialization */  
    static int *gp = &GLOBAL;  /* Legal initialization   */  
    register int *rp = &LOCAL; /* Legal initialization   */  
}  
```  
  
 Zmienna globalna `GLOBAL` zadeklarowano na poziomie zewnętrzny, co powoduje globalny okres istnienia. Zmienna lokalna `LOCAL` ma **automatycznie** Klasa magazynu i adres jest tylko podczas wykonywania funkcji, w którym jest zadeklarowany. W związku z tym próby zainicjowania **statycznych** zmiennej wskaźnikowej `lp` adres `LOCAL` nie jest dozwolone. **Statycznych** zmiennej wskaźnikowej `gp` mogą być inicjowane z adresem `GLOBAL` ponieważ ten adres jest zawsze taki sam. Podobnie `*rp` mogą być inicjowane, ponieważ `rp` jest zmienną lokalną i może mieć inicjatora nieunikatowego. Każdym wprowadzeniu bloku `LOCAL` ma nowy adres, który następnie jest przypisany `rp`.  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie](../c-language/initialization.md)