---
title: "Przestarzałe formy deklaracji i definicji funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7de356abb7078b7dd50f0d90bf4ecb0a046945b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Przestarzałe formy deklaracji i definicji funkcji
Deklaracje funkcji w starym stylu i definicje deklarowanie parametrów niż składni zalecane standardu ANSI C przy użyciu nieco inne reguły. Po pierwsze deklaracje w starym stylu nie ma listy parametrów. Po drugie w definicji funkcji parametry są wyświetlane, ale ich typy nie są zadeklarowane w liście parametrów. Deklaracje typu poprzedzać złożonej instrukcji stanowiące treści funkcji. Składnia stary styl jest przestarzały i nie powinna być używana w nowy kod. Kod przy użyciu składni w starym stylu jest nadal obsługiwany, jednak. W tym przykładzie przedstawiono przestarzałe formy deklaracji i definicji:  
  
```  
double old_style();           /* Obsolete function declaration */  
  
double alt_style( a , real )  /* Obsolete function definition */  
    double *real;   
    int a;   
{  
    return ( *real + a ) ;  
}  
```  
  
 Funkcji zwracających liczbą całkowitą lub wskaźnik z taki sam rozmiar jak `int` nie muszą mieć deklaracji deklaracja jest zalecane.  
  
 Aby zgodny ze standardem ANSI C, deklaracje funkcji w starym stylu przy użyciu wielokropek teraz wygenerować wystąpił błąd podczas kompilowania za pomocą opcji /Za i poziom 4 ostrzeżenie podczas kompilowania przy użyciu /Ze. Na przykład:  
  
```  
void funct1( a, ... )  /* Generates a warning under /Ze or */  
int a;                 /* an error when compiling with /Za */  
{  
}  
```  
  
 Ta deklaracja jako prototyp powinien edycji:  
  
```  
void funct1( int a, ... )  
{  
}  
```  
  
 Deklaracje funkcji w starym stylu także wygenerować ostrzeżenia, jeśli następnie zadeklarować lub definiować taką samą funkcję z albo wielokropkiem lub parametrem typu, który nie jest taka sama jak jego awansowana typu.  
  
 Następna sekcja [definicje funkcji języka C](../c-language/c-function-definitions.md), przedstawiono składnię definicje funkcji, łącznie z składnią w starym stylu. Jest nonterminal listę parametrów w składni w starym stylu *listy identyfikatorów*.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd funkcji](../c-language/overview-of-functions.md)