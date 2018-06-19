---
title: Proste deklaracje zmiennej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bbda7ff9a22a42ce4a6b8c3de10d0d6f0d03f77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389770"
---
# <a name="simple-variable-declarations"></a>Proste deklaracje zmiennej
Deklaracja prostej zmiennej najprostsza forma deklaratorze bezpośredniego Określa nazwę i typ zmiennej. Określa również klasy magazynu w zmiennej i typu danych.  
  
 Klasy magazynu lub typy (lub obie) są wymagane w deklaracji zmiennych. Bez typu zmienne (takie jak `var;`) generowanie ostrzeżenia.  
  
## <a name="syntax"></a>Składnia  
 `declarator`:  
 *wskaźnik* opcjonalnych  
  
 *bezpośrednie deklarator*  
  
 *deklarator bezpośrednio*:  
 *Identyfikator*  
  
 *Identyfikator*:  
 *cyfrą*  
  
 *Identyfikator cyfrą*  
  
 *Identyfikator cyfrowy*  
  
 Arytmetyczny, struktury, Unii, wyliczeń i typy void i typy reprezentowane przez `typedef` nazwy, proste deklaratorów mogą być używane w deklaracji, ponieważ Specyfikator typu dostarcza wpisywania danych. Wskaźnik, tablic i typy funkcji wymagają deklaratorów bardziej złożonych.  
  
 Można użyć listy identyfikatorów rozdzielonych przecinkami (**,**) do określenia kilku zmiennych w tej samej deklaracji. Wszystkie zmienne zdefiniowane w deklaracji mają ten sam typ podstawowy. Na przykład:  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 Zmienne `x` i `y` może zawierać żadnej wartości zdefiniowane przez zestaw `int` typu dla konkretnej implementacji. Prosty obiekt `z` jest ustawiana na wartość 1, a nie można modyfikować.  
  
 Jeśli w deklaracji `z` niezainicjowanej zmiennej statyczne lub w zakresie pliku otrzyma początkowej wartości 0, a ta wartość będzie unmodifiable.  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 W tym przykładzie zarówno zmienne, `reply` i `flag`, ma `unsigned long` typu która przechowuje wartości całkowitych bez znaku.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)