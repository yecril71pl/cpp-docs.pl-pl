---
title: Interpretowanie Deklaratorów bardziej złożonych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dd51e4e8a3c6805b9facfef54565368252e87df
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="interpreting-more-complex-declarators"></a>Interpretowanie deklaratorów bardziej złożonych
Wszelkie deklarator można ująć w nawiasy, aby określić konkretnego interpretacja "deklaratorów złożonych". Deklarator złożonych jest identyfikatorem kwalifikowana przez więcej niż jeden tablicy, wskaźnika lub modyfikator funkcji. Różne kombinacje tablicy, wskaźnik i Modyfikatory funkcji można zastosować do jednego identyfikatora. Ogólnie rzecz biorąc `typedef` może służyć do uproszczenia deklaracji. Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).  
  
 W interpretowanie deklaratorów złożonych, nawiasy i nawiasy (to znaczy Modyfikatory prawo identyfikatora) pierwszeństwo gwiazdki (to znaczy Modyfikatory na lewo od identyfikatora). Nawiasy i nawiasy mają ten sam priorytet i skojarzyć od lewej do prawej. Po w pełni interpretowane deklarator specyfikatora typu jest stosowany jako ostatni krok. Za pomocą nawiasów można zastąpić domyślną kolejność skojarzenia i wymuszanie konkretnego interpretacji. Nigdy nie używaj nawiasów, jednak wokół nazwy identyfikatora samodzielnie. To może być błędnie z zinterpretowana jako listy parametrów.  
  
 Interpretowanie deklaratorów złożonych prosty sposób jest je odczytać "od wewnątrz," przy użyciu następujących czterech krokach:  
  
1.  Uruchom z identyfikatorem i wyglądać po prawej, nawiasy kwadratowe lub nawiasy (jeśli istnieje).  
  
2.  Interpretowanie te nawiasy kwadratowe lub nawiasy, a następnie sprawdź do lewej dla gwiazdki.  
  
3.  Jeśli wystąpią prawego nawiasu okrągłego na każdym etapie, przejdź wstecz i stosowania reguł 1 i 2 do wszystkie elementy w nawiasach.  
  
4.  Zastosuj specyfikatora typu.  
  
    ```  
    char *( *(*var)() )[10];  
     ^   ^  ^ ^ ^   ^    ^  
     7   6  4 2 1   3    5  
    ```  
  
W tym przykładzie kroki są numerowane kolejno i może zostać zinterpretowany w następujący sposób:  
  
1.  Identyfikator `var` jest zadeklarowany jako  
  
2.  wskaźnik do  
  
3.  funkcja zwracająca  
  
4.  wskaźnik do  
  
5.  Tablica 10 elementów, które są  
  
6.  wskaźniki do  
  
7.  `char` wartości.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady ilustrują innych złożonych deklaracje i Pokaż wpływ znaczenie deklaracji nawiasów.  
  
```  
int *var[5]; /* Array of pointers to int values */  
```  
  
 Modyfikator tablicy ma wyższy priorytet niż modyfikator wskaźnika, więc `var` został zadeklarowany jako tablicy. Modyfikator wskaźnika dotyczy typ elementów tablicy; w związku z tym elementy tablicy są wskaźnikami do `int` wartości.  
  
```  
int (*var)[5]; /* Pointer to array of int values */  
```  
  
 W tej deklaracji dla `var`, nawiasów nadać wskaźnika modyfikator wyższy priorytet niż modyfikator tablicy i `var` został zadeklarowany jako wskaźnik do tablicy pięć `int` wartości.  
  
```  
long *var( long, long ); /* Function returning pointer to long */  
```  
  
 Modyfikatory funkcji również mają wyższy priorytet niż Modyfikatory wskaźnika, więc tej deklaracji dla `var` deklaruje `var` jako funkcji zwracającej wskaźnik do **długi** wartość. Funkcja jest zadeklarowana, aby podjąć dwie **długi** wartości jako argumenty.  
  
```  
long (*var)( long, long ); /* Pointer to function returning long */  
```  
  
 W tym przykładzie jest podobny do poprzedniego. Nawiasów nadać wskaźnika modyfikator wyższy priorytet niż modyfikator funkcji i `var` został zadeklarowany jako wskaźnik do funkcji, która zwraca **długi** wartość. Ponownie, funkcja przyjmuje dwa **długi** argumentów.  
  
```  
struct both       /* Array of pointers to functions */  
{                 /*   returning structures         */  
    int a;  
    char b;  
} ( *var[5] )( struct both, struct both );  
```  
  
 Elementy tablicy nie może być funkcji, ale ta deklaracja pokazano, jak zamiast zadeklarować tablicy wskaźników do funkcji. W tym przykładzie `var` został zadeklarowany jako tablicę pięć wskaźniki do funkcji zwracających struktury o dwóch członków. Argumenty funkcji są uznane za dwie struktury z tym samym typem struktury `both`. Należy pamiętać, że nawiasy otaczające `*var[5]` są wymagane. Bez nich deklaracja jest niedozwolona próba zadeklarować tablicę funkcje, jak pokazano poniżej:  
  
```  
/* ILLEGAL */  
struct both *var[5](struct both, struct both);  
```  
  
 Następująca instrukcja deklaruje tablicę wskaźników.  
  
```  
unsigned int *(* const *name[5][10] ) ( void );  
```  
  
 `name` Tablicy ma 50 elementów w tablicy wielowymiarowej. Elementy są wskaźnikami do wskaźnika, który jest stałą. Wskazuje to stałej wskaźnik do funkcji, która nie ma parametrów i zwraca wskaźnik do typu bez znaku.  
  
 W tym przykładzie dalej jest funkcji zwracającej wskaźnik do tablicy trzech **podwójne** wartości.  
  
```  
double ( *var( double (*)[3] ) )[3];  
```  
  
 W tej deklaracji funkcja zwraca wskaźnik do tablicy, od funkcji przekazujących tablice są niedozwolone. W tym miejscu `var` został zadeklarowany jako funkcji zwracającej wskaźnik do tablicy trzech **podwójne** wartości. Funkcja `var` przyjmuje jeden argument. Argument, takich jak wartość zwracana jest wskaźnik do tablicy trzech **podwójne** wartości. Typ argumentu jest określany przez złożony *deklarator abstrakcyjny*. Nawiasy otaczające gwiazdki w typ argumentu są wymagane; bez obawy, typ argumentu byłoby tablicy wskaźników trzy do **podwójne** wartości. Omówienie i przykłady deklaratory abstrakcyjne języka, zobacz [deklaratory abstrakcyjne języka](../c-language/c-abstract-declarators.md).  
  
```  
union sign         /* Array of arrays of pointers */  
{                  /* to pointers to unions       */  
     int x;  
     unsigned y;  
} **var[5][5];  
```  
  
 Jak pokazano na powyższym przykładzie, wskaźnik może wskazywać innego wskaźnika, a Tablica może zawierać tablic jako elementy. W tym miejscu `var` jest tablicą pięć elementów. Każdy element jest tablicą element pięciu wskaźników do wskaźników do złożenia z dwóch członków.  
  
```  
union sign *(*var[5])[5]; /* Array of pointers to arrays  
                             of pointers to unions        */  
```  
  
 Ten przykład przedstawia sposób umieszczania nawiasów zmienia znaczenie deklaracji. W tym przykładzie `var` jest tablicą element pięciu wskaźników do elementu pięciu tablic wskaźników do złożenia. Przykłady dotyczące używania `typedef` w celu uniknięcia deklaracji złożonych, zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)
