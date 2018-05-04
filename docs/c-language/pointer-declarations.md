---
title: Deklaracje wskaźników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d9600c27f40a43105ae9a8fc2fd1579907891cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pointer-declarations"></a>Deklaracje wskaźników
Deklaracji"wskaźnik" nazwy zmiennej wskaźnikowej i określa typ obiektu, na które wskazuje zmiennej. Zmienna zadeklarowana jako wskaźnik przechowuje adres pamięci.  
  
## <a name="syntax"></a>Składnia  
 *deklarator*:  
 &nbsp;&nbsp;*wskaźnik*<sub>opt</sub> *bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*:  
 &nbsp;&nbsp;*Identyfikator*  
  
 &nbsp;&nbsp;**(** *deklarator* **)**  
  
 &nbsp;&nbsp;*deklarator bezpośrednio* **[** *wyrażenia*<sub>opt</sub> **]**  
  
 &nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**  
  
 &nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>opt</sub> **)**  
  
 *wskaźnik*:  
 &nbsp;&nbsp;**\*** *Lista typów kwalifikator*<sub>opcjonalnych</sub>  
  
 &nbsp;&nbsp;**\*** *Lista typów kwalifikator*<sub>opt</sub> *wskaźnika*  
  
 *Lista typów kwalifikator*:  
 &nbsp;&nbsp;*Kwalifikator typu*  
  
 &nbsp;&nbsp;*Lista typów kwalifikator* *kwalifikator typu*  
  
 *Specyfikatora typu* zawiera typ obiektu, który może mieć żadnych podstawowych, struktury lub Unii. Zmienne wskaźnika może także wskazywać funkcje, tablic i innych wskaźników. (Informacji na temat deklarowanie i interpretacji bardziej złożonych typów wskaźnikowych, można znaleźć w [interpretowanie Deklaratorów złożonych więcej](../c-language/interpreting-more-complex-declarators.md).)  
  
 Tworząc *specyfikatora typu* **void**, można opóźnić Specyfikacja typu, do którego odwołuje się wskaźnik myszy. Element taki jest nazywany "wskaźnik do **void**" i jest zapisywany jako `void *`. Zmienna zadeklarowana jako wskaźnik do *void* można wskazać obiekt dowolnego typu. Jednak do wykonywania większości operacji na wskaźnik lub obiekt, który wskazuje, na które wskazuje typ musi być jawnie określona dla każdej operacji. (Zmiennych typu **char \***  i typ **void \***  są zgodne przypisania bez typu rzutowania.) Można wykonywać takie konwersji typu rzutowania (zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) Aby uzyskać więcej informacji).  
  
 *Kwalifikator typu* mogą być **const** lub **volatile**, lub obie. Określają one, czy wskaźnik nie można zmodyfikować przez sam program (**const**), lub który legalnie wskaźnik może być modyfikowany w procesie poza kontrolą programu (**volatile**). (Zobacz [kwalifikatory typu](../c-language/type-qualifiers.md) Aby uzyskać więcej informacji na temat **const** i **volatile**.)  
  
 *Deklarator* nazwy zmiennej i może zawierać modyfikatora typu. Na przykład jeśli *deklarator* reprezentuje tablicy, typ wskaźnika są modyfikowane w celu być wskaźnikiem do tablicy.  
  
 Wskaźnik do struktury, Unią lub typ wyliczenia mogą zadeklarować przed zdefiniowaniem struktury, Unią lub typem wyliczenia. Należy zadeklarować wskaźnika przy użyciu tagu struktury lub związku, jak pokazano w poniższych przykładach. Oświadczenia są dozwolone, ponieważ kompilator nie trzeba znać rozmiar struktury lub Unii, aby przydzielić miejsce dla zmiennej wskaźnikowej.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają deklaracje wskaźników.  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 *Komunikat* wskazuje wskaźnik do zmiennej o **char** typu.  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 *Wskaźniki* tablica zawiera 10 elementów; każdy element jest wskaźnik do zmiennej o **int** typu.  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 *Wskaźnika* zmienna odwołuje się do tablicy o 10 elementów. Każdy element tej tablicy ma **int** typu.  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 Wskaźnik *x* można zmodyfikować, aby wskazać inną **int** wartość, ale wartość, do których nie można modyfikować punkty.  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 Zmienna *y* w deklaracjach jest zadeklarowany jako stałej wskaźnika do **int** wartość. Wartość wskazuje można modyfikować, ale sam wskaźnik zawsze musi wskazywać na tej samej lokalizacji: adres *fixed_object*. Podobnie *z* stałej wskaźnika, ale jest również zadeklarowany wskaż **int** wartość, której nie można zmodyfikować przez program. Specyfikator dodatkowe **volatile** wskazuje, że chociaż wartość **const int** wskazywanej przez *z* nie może być modyfikowana w programie legalnie możliwe zmodyfikowane przez proces uruchomiony równocześnie z programu. Deklaracja *w* Określa, że program nie można zmienić wartości wskazywał i że program nie można zmodyfikować wskaźnik.  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 W tym przykładzie deklaruje dwie zmienne wskaźnika, *dalej* i *poprzedniej*, wskazujących na typ struktury *listy*. Ta deklaracja może wystąpić przed definicją *listy* struktura typu (patrz następnym przykładzie), tak długo, jak *listy* definicji typu ma taką samą widoczność jak deklaracji.  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 Zmienna *wiersza* ma typ struktury o nazwie *listy*. *Listy* typ struktury ma trzy elementy członkowskie: pierwszego elementu członkowskiego jest wskaźnikiem do **char** , druga wartość **int** wartości, a trzeci jest wskaźnikiem do innego *listy* struktury.  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 Zmienna *rekordu* ma typ struktury *identyfikator*. Należy pamiętać, że *pname* jest zadeklarowany jako wskaźnik do innego typu struktury o nazwie *nazwa*. Ta deklaracja może występować przed *nazwa* typ jest zdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)