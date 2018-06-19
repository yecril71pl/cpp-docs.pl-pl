---
title: Deklaratory i deklaracje zmiennych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0219c5eecda84f27411ee0dca9cc43a1b5c9148e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390609"
---
# <a name="declarators-and-variable-declarations"></a>Deklaratory i deklaracje zmiennych
Pozostałej części tej sekcji opisano formularza i znaczenie deklaracje zmiennych typów podsumowywane na tej liście. W szczególności pozostałych sekcjach wyjaśniono sposób zadeklarować następujące czynności:  
  
|Typ zmiennej|Opis|  
|----------------------|-----------------|  
|[Zmienne proste](../c-language/simple-variable-declarations.md)|Zmienne pojedynczą wartość z typu całkowitego lub liczb zmiennoprzecinkowych|  
|[Tablice](../c-language/array-declarations.md)|Zmienne składające się z kolekcji elementów tego samego typu|  
|[Wskaźniki](../c-language/pointer-declarations.md)|Zmienne, które zawierają lokalizacje zmiennej (w formie adresów) zamiast wartości i punktu do innych zmiennych|  
|[Wyliczenie zmiennych](../c-language/c-enumeration-declarations.md)|Proste zmiennych o całkowitym typu wstrzymywania jednej wartości z zestawu stałe całkowite nazwanego|  
|[Struktury](../c-language/structure-declarations.md)|Składające się z kolekcji wartości, które mogą mieć różne typy zmiennych|  
|[Unie](../c-language/union-declarations.md)|Zmienne składa się z kilku wartości różnych typów, które zajmują tego samego miejsca do magazynowania|  
  
 Deklaratorze jest częścią deklaracji, która określa nazwę, która ma być wprowadzane do programu. Modyfikatory może obejmować takie jak **\*** (wskaźnik-do) oraz innych słów kluczowych Konwencja wywoływania firmy Microsoft.  
  
 **Microsoft Specific**  
  
 W deklarator  
  
```  
__declspec(thread) char *var;  
```  
  
 `char` Specyfikator typu jest `__declspec(thread)` i `*` są modyfikatory, i `var` jest nazwą identyfikatora.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Deklaratory umożliwia zadeklarować tablice wartości, wskaźniki do wartości i funkcji zwracających wartości określonego typu. Deklaratory są wyświetlane w deklaracjach tablicy i wskaźnika w dalszej części tej sekcji.  
  
## <a name="syntax"></a>Składnia  
 *deklarator*:  
 &nbsp;&nbsp;*wskaźnik*<sub>opt</sub> *bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*:  
 &nbsp;&nbsp;*Identyfikator*  
 &nbsp;&nbsp;**(***deklarator***)**  
 &nbsp;&nbsp;*deklarator bezpośrednio***[***wyrażenia*<sub>opt</sub> **]**  
 &nbsp;&nbsp;*deklarator bezpośrednio***(***listy parametrów typu***)**  
 &nbsp;&nbsp;*deklarator bezpośrednio***(***listy identyfikatorów*<sub>opt</sub> **)**  
  
 *wskaźnik*:  
 &nbsp;&nbsp;**\*** *Lista typów kwalifikator*<sub>opcjonalnych</sub>  
 &nbsp;&nbsp;**\*** *Lista typów kwalifikator*<sub>opt</sub> *wskaźnika*  
  
 *Lista typów kwalifikator*:  
 &nbsp;&nbsp;*Kwalifikator typu*  
 &nbsp;&nbsp;*Kwalifikator typu listy kwalifikator — typ*  
  
> [!NOTE]
>  Zobacz składnię *deklaracji* w [Przegląd deklaracji](../c-language/overview-of-declarations.md) lub [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md) składni, który odwołuje się do *deklarator*.  
  
 Po deklaratorze składa się z identyfikatora zostały zmodyfikowane, element został zadeklarowany ma typ podstawowy. Jeśli znak gwiazdki (**\***) pojawi się na lewo od identyfikatora typu są modyfikowane w celu typu wskaźnika. Jeśli identyfikator następuje nawiasy (**[**), typ są modyfikowane w celu typem tablicy. Jeśli identyfikator następuje nawiasów, typ są modyfikowane w celu typu funkcji. Aby uzyskać więcej informacji na temat interpretacji pierwszeństwo w deklaracji, zobacz [interpretowanie Deklaratorów złożonych więcej](../c-language/interpreting-more-complex-declarators.md).  
  
 Każdy deklarator deklaruje co najmniej jeden identyfikator. Deklaratorze musi zawierać specyfikatora typu jako oświadczenie zakończenie. Specyfikator typu zawiera typ elementów typu tablicy, typ obiektu adresowane przez typ wskaźnika lub typ zwracany funkcji.  
  
 [Tablica](../c-language/array-declarations.md) i [wskaźnika](../c-language/pointer-declarations.md) deklaracje omówiono bardziej szczegółowo w dalszej części tej sekcji. Poniższe przykłady przedstawiają kilka prostych formularzy deklaratorów:  
  
```  
int list[20]; // Declares an array of 20 int values named list  
char *cp;     // Declares a pointer to a char value  
double func( void ); // Declares a function named func, with no   
                     // arguments, that returns a double value  
int *aptr[10] // Declares an array of 10 pointers  
```  
  
 **Microsoft Specific**  
  
 Kompilator Microsoft C nie ogranicza liczby deklaratorów, które można modyfikować arytmetyczne, struktury lub Unii. Liczba jest ograniczona tylko przez ilość dostępnej pamięci.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)