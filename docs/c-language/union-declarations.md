---
title: "Deklaracje złożeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4088aea4025e7c51aba75efe28978d05c0e48730
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="union-declarations"></a>Deklaracje złożeń
"Złożenia deklaracji" Określa zestaw wartości zmiennych i, opcjonalnie, tag nazewnictwa Unii. Wartości zmiennych są nazywane "Członkowie" Unii i mogą mieć różnych typów. Unie są podobne do "rekordy wariantów" w innych językach.  
  
## <a name="syntax"></a>Składnia  
 *Specyfikator Struct lub union*:  
 *Identyfikator struktury lub Unii* opt**{** *struktury deklaracji listy* **}**  
  
 *Identyfikator struktury lub związku*  
  
 *Struktura lub Unia*:  
 **struct**  
  
 **Unii**  
  
 *Struktura deklaracji listy*:  
 *Deklaracja — struktura*  
  
 *Deklaracja struktury deklaracjach — struktura*  
  
 Zawartość Unii jest zdefiniowany  
  
 *Deklaracja struktury*:  
 *Specyfikator kwalifikator listy w strukturze listy deklarator***;**   
  
 *Specyfikator kwalifikator listy*:  
 *Specyfikator typu w specyfikatorze listy kwalifikator* opcjonalnych  
  
 *Kwalifikator typu w specyfikatorze listy kwalifikator* opcjonalnych  
  
 *Struktura deklarator listy*:  
 *deklarator — struktura*  
  
 *Struktura deklarator listy***,***deklarator — struktura*   
  
 Zmienna o **Unii** typu przechowuje jedną z wartości zdefiniowanych przez tego typu. Te same zasady określają deklaracje struktury i Unii. Unie można również mieć bit pola.  
  
 Elementów członkowskich Unii nie może mieć niekompletnego typu, wpisz `void`, lub typu funkcji. W związku z tym elementów członkowskich nie może być wystąpieniem typu Unii, ale może być wskaźniki do typu union został zadeklarowany.  
  
 Deklaracja typu union jest tylko szablon. Pamięci nie jest przeznaczone do momentu zmienna została zadeklarowana.  
  
> [!NOTE]
>  Jeśli zadeklarowano złożenie dwóch typów jest przechowywany w jedną wartość, ale Unii jest dostępny z innym typem, wyniki są niepewna. Na przykład związek **float** i `int` jest zadeklarowany. A **float** wartość jest przechowywana, ale program później dostęp do wartości jako `int`. W takiej sytuacji, wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowita nie będzie wiarygodne.  
  
## <a name="examples"></a>Przykłady  
 Poniżej przedstawiono przykłady unie:  
  
```  
union sign   /* A definition and a declaration */  
{  
    int svar;  
    unsigned uvar;  
} number;  
```  
  
 W tym przykładzie definiuje zmienną Unii o `sign` wpisz i deklaruje zmienną o nazwie `number` która ma dwa elementy członkowskie: `svar`, podpisane liczby całkowite i `uvar`, liczbą całkowitą bez znaku. Ta deklaracja umożliwia bieżącą wartość `number` mają być przechowywane jako zalogowany lub wartość bez znaku. Tag skojarzone z tym typem Unii jest `sign`.  
  
```  
union               /* Defines a two-dimensional */  
{                   /*  array named screen */  
    struct      
    {   
      unsigned int icon : 8;    
      unsigned color : 4;  
    } window1;  
    int screenval;  
} screen[25][80];  
```  
  
 `screen` Tablica zawiera elementy 2000. Każdy element tablicy jest poszczególnych związek z dwóch elementów: `window1` i `screenval`. `window1` Element członkowski jest strukturą z dwóch członków pola bitowego, `icon` i `color`. `screenval` Element członkowski jest `int`. W dowolnym momencie, każdy element złożenia przechowuje albo `int` reprezentowany przez `screenval` lub struktury reprezentowany przez `window1`.  
  
 **Dotyczące firmy Microsoft**  
  
 Unie zagnieżdżonych mogą być deklarowane anonimowo, gdy są oni członkami innego struktury lub związku. To jest przykład typ Unii:  
  
```  
struct str  
{  
    int a, b;  
    union            / * Unnamed union */  
    {  
      char c[4];  
      long l;  
      float f;  
   };  
   char c_array[10];  
} my_str;  
.  
.  
.  
my_str.l == 0L;  /* A reference to a field in the my_str union */  
```  
  
 Unie często są zagnieżdżone w ramach struktury zawierającej pole, podając typu danych zawartych w Unii w dowolnym momencie konkretnego. To jest przykład deklaracji dla takiej Unii:  
  
```  
struct x  
{  
    int type_tag;  
    union  
    {  
      int x;  
      float y;  
    }  
}  
```  
  
 Zobacz [struktury i elementów członkowskich Unii](../c-language/structure-and-union-members.md) informacji o odwołujące się do złożenia.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)