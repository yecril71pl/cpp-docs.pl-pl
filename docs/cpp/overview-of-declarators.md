---
title: Przegląd Deklaratorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe5866c3e945d55722a4cf8530c543b0e8ca5163
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947775"
---
# <a name="overview-of-declarators"></a>Przegląd deklaratorów
Deklaratory są składnikami deklaracji, które określają nazwy obiektów lub funkcji. Deklaratory określają również, czy nazwany obiekt jest obiektem, wskaźnikiem, odwołaniem lub tablicą.  Deklaratory nie określają typu podstawowego, ale modyfikują informacje o typie w obrębie typu podstawowego w celu określenia typów pochodnych, takich jak wskaźniki, odwołania i tablice.  Deklarator w zastosowaniu do funkcji współpracuje ze specyfikatorem typu, aby w pełni określić, że typ zwracany funkcji jest obiektem, wskaźnikiem lub odwołaniem. (Specyfikatory omówione w [deklaracje i definicje](declarations-and-definitions-cpp.md), przekazują właściwości, takie jak typ i Klasa magazynu. Modyfikatory omówione w tej sekcji i w [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md), modyfikowania deklaratorów.) Na poniższej ilustracji pokazano pełną deklarację `MyFunction` i wywołano składniki deklaracji.  
  
 ![Modyfikatory, Specyfikatory i deklaratory](../cpp/media/vc38qy1.gif "vc38QY1")  
Specyfikatory, modyfikatory i deklaratory  
  
 **Microsoft Specific**  
  
 Większość słów kluczowych rozszerzonych przez Microsoft może być użyta jako modyfikatory do tworzenia typów pochodnych; nie są one specyfikatorami ani deklaratorami. (Zobacz [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md).)  
  
 **END specyficzny dla Microsoft**  
  
 Deklaratory pojawiają się w składni deklaracji po opcjonalnej liście specyfikatorów. Te specyfikatory omówiono w [deklaracji.](declarations-and-definitions-cpp.md) Deklaracja może składać się z więcej niż jednego deklaratora, ale każdy deklarator deklaruje tylko jedną nazwę.  
  
 Poniższa przykładowa deklaracja pokazuje, jak specyfikatory i deklaratory są połączone, tworząc pełną deklarację:  
  
```cpp 
const char *pch, ch;  
```  
  
 W powyższej deklaracji, słowa kluczowe **const** i **char** składają się na liście specyfikatorów. Wymienione są dwa deklaratory: `*pch` i `ch`.  Deklaracja, która deklaruje wiele jednostek składa się ze specyfikatora typu, po którym następuje lista deklaratorów oddzielonych przecinkami, zakończona średnikiem.  
  
 **Deklaratory dla prostych obiektów**  
  
 Deklarator prostego obiektu, takiego jak int lub double, jest po prostu jego nazwą z opcjonalnymi nawiasami.  
  
 `int i; // declarator is i`  
  
 `int (i); // declarator is (i)`  
  
 **Deklaratory dla wskaźników, odwołań i tablic**  
  
 Operatory wskaźników wstawione przed nazwą powodują, że obiekt jest wskaźnikiem lub odwołaniem.  **\*** Operator deklaruje nazwę jako wskaźnik; **&** operator deklaruje ją jako odwołanie.  
  
```cpp 
int *i; // declarator is *i  
int **i; // declarator is **i;  
int &i = x; // declaratory is &i  
```  
  
 Dołączanie **const** lub **volatile** nadaje wskaźnikowi specjalne właściwości.  Użycie tych specyfikatorów w deklaratorze (w przeciwieństwie do użycia w specyfikatorze typu) modyfikuje właściwości wskaźnika, a nie obiektu wskazywanego:  
  
```cpp 
char *const cpc; // const pointer to char   
const char *pcc; // pointer to const char   
const char *const cpcc; // const pointer to const char  
```  
  
 Dodatkowe informacje można znaleźć w [wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md).  
  
 Wskaźnik do składowej klasy lub struktury jest zadeklarowany z odpowiednim zagnieżdżonym specyfikatorem nazwy:  
  
```cpp 
int X::* pIntMember;   
int ::X::* pIntMember; // the initial :: specifies X is in global scope  
char Outer::Inner::* pIntMember; // pointer to char in a nested class  
```  
  
 Nawiasy otaczające opcjonalne wyrażenie stałe po nazwie powodują, że obiekt jest tablicą.  Kolejne nawiasy deklarują dodatkowe wymiary dla tablicy.  
  
```cpp 
int i[5]; // array with five elements of type int numbered from 0 to 4  
int i[]; // array of unknown size  
char *s[4]; // array of pointers to char  
int i[2][2]; // two dimensional array  
```  
  
 **Deklaratory dla funkcji**  
  
 Nawiasy zawierające listę argumentów są używane po jej nazwie, aby zadeklarować funkcję.  Poniżej zadeklarowano funkcję o typie zwracanym **int** i trzema argumentami typu **int**.  
  
```cpp 
int f(int a, int b, int c);  
```  
  
 Wskaźniki i odwołania do funkcji deklarowane są poprzez dodawanie przed nazwą funkcji wskaźnika lub operatora odwołania, jak pokazano poniżej.  Nawiasy, normalnie opcjonalne, są wymagane w celu rozróżnienia wskaźnika do funkcji od funkcji, która zwraca wskaźnik:  
  
```cpp 
int (*pf)(int); // pointer to function returning int  
int *f(int i); // function returning pointer to int  
int (&pf)(int); // reference to function   
```  
  
 Wskaźniki do funkcji członkowskich są rozróżniane przez zagnieżdżone specyfikatory nazwy:  
  
```cpp 
int (X::* pmf)(); // pointer to member function of X returning int  
int* (X::* pmf)(); // pointer to member function returning pointer to int  
```  
  
 Zobacz też [wskaźników do elementów członkowskich](../cpp/pointers-to-members.md).  
  
 **Funkcje i obiekty w tej samej deklaracji**  
  
 Funkcje i obiekty mogą być zadeklarowane w tej samej deklaracji w następujący sposób:  
  
```cpp 
int i, *j, f(int k);  // int, pointer to int, function returning int  
```  
  
 Składnia może być myląca w pewnych okolicznościach.  Następująca deklaracja  
  
```cpp 
int* i, f(int k);  // pointer to int, function returning int (not int*)  
```  
  
 może wyglądać jak deklaracja **int** wskaźnik i funkcja zwracająca `int*`, ale nie jest.  To dlatego, że * jest częścią deklaratora dla `i`, a nie częścią deklaratora dla `f`.  
  
 **Upraszczanie składni deklaratora z użyciem typedef**  
  
 Jednak lepszą techniką jest użycie **typedef** lub kombinacji nawiasów i **typedef** — słowo kluczowe. Należy rozważyć deklarowanie tablicy wskaźników do funkcji:  
  
```cpp 
//  Function returning type int that takes one   
//   argument of type char *.  
typedef int (*PIFN)( char * );  
//  Declare an array of 7 pointers to functions   
//   returning int and taking one argument of type   
//   char *.  
PIFN pifnDispatchArray[7];  
```  
  
 Można zapisać równoważną deklarację bez **typedef** deklaracji, ale to na tyle skomplikowane, że możliwość błędu przekracza wszelkie korzyści:  
  
```cpp 
int ( *pifnDispatchArray[7] )( char * );  
```  
  
 Aby uzyskać więcej informacji dotyczących typedef, zobacz [aliasy i definicje typów](aliases-and-typedefs-cpp.md).  
  
 Wskaźniki, odwołania i tablice pojedynczego typu podstawowego mogą być łączone w jednej deklaracji (rozdzielonej przecinkami), jako  
  
```cpp 
int a, *b, c[5], **d, &e=a;  
```  
  
 **Bardziej złożona składnia deklaratora**  
  
- Deklaratory wskaźników, odwołań, tablic i funkcji mogą być łączone do określenia takich obiektów jak tablice wskaźników do funkcji, wskaźniki do tablic, itp.  
  
- Następująca gramatyka cykliczna w pełni opisuje składnię deklaratora wskaźnika.  
  
- `declarator` jest zdefiniowany jako jeden z:  

  - identyfikator   
  - kwalifikowana nazwa   
  - deklarator (-listy argumentów) [cv-qualfiers] [wyjątek Specyfikacja]  
  - deklarator [[wyrażenie stałe]]
  - deklarator wskaźnik-— operator   
  - (specyfikator)  

  
- i *operator wskaźnika* jest jednym z:  
  
  - * [kwalifikatory cv]  
  - & [kwalifikatory cv]:: zagnieżdżone name-specifier * [kwalifikatory cv]  

  
 Ponieważ deklarator może składać się z deklaratorów, istnieje możliwość konstruowania bardziej złożonych typów pochodnych, takich jak tablice wskaźników, funkcji zwracających tablice wskaźników do funkcji, używając powyższych reguł.  Aby wykonać każdy krok konstrukcji, rozpocznij od identyfikatora reprezentującego podstawowy typ danych i zastosuj powyższą regułę dotyczącą składni, przy poprzednim wyrażeniu będącym `declarator`.  Kolejność stosowania reguł dotyczących składni powinna być odwrotnością sposobu, w jaki określono wyrażenie w języku angielskim.  Jeśli zastosowanie *operator wskaźnika* reguły składni wyrażenia tablicy lub funkcji, Użyj nawiasów, jeśli chcesz, aby wskaźnik do tablicy lub funkcji, jak ostatni wiersz w tabeli poniżej.  
  
 W poniższym przykładzie pokazano konstrukcję „wskaźnika do tablicy 10 wskaźników do int”.  
  
|Ustne wyrażenie|Deklarator|Zastosowana reguła składni|  
|-----------------------|----------------|-------------------------|  
||`i`|1|  
|wskaźnik(i) do|`*i`|5|  
|tablicy 10|`(*i)[10]`|4|  
|wskaźnik do|`*((*i)[10])`|6, a następnie 5|  
  
 Gdy używa się wielokrotnych modyfikatorów wskaźników, odwołań, tablic lub funkcji, deklaratory mogą stać się dość skomplikowane.  Temat [interpretowanie Deklaratorów bardziej złożonych](../c-language/interpreting-more-complex-declarators.md) opisuje jak odczytywać bardziej złożoną składnię deklaratorów.  Temat ma zastosowanie do C i C++, mimo że w języku C++ wszędzie * jest używany do wskazania wskaźnika, kwalifikowana nazwa taka jak MyClass::\* może służyć do określenia wskaźnika do składowej klasy.