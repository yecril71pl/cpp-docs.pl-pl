---
title: "Definicje funkcji języka C | Dokumentacja firmy Microsoft"
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
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a58adfefc5e2b3b5085a44c38dd392d3369421c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-function-definitions"></a>Definicje funkcji języka C
Definicja funkcji Określa nazwę funkcji, typy i liczby parametrów, które oczekuje na odbieranie i jej typu zwracanego. Definicja funkcji obejmuje również treść funkcji z deklaracji jego zmiennych lokalnych i instrukcje, które określają, jak działa funkcja.  
  
## <a name="syntax"></a>Składnia  
 *jednostki tłumaczenia*:  
 *Deklaracja zewnętrzne*  
  
 *Deklaracja zewnętrznej jednostki tłumaczenia*  
  
 *Deklaracja zewnętrzne*: /\* dozwolone tylko w zakresie zewnętrzne (plik)\*/  
 *Definicja funkcji*  
  
 `declaration`  
  
 *Definicja funkcji*: /\* Deklaratora w tym miejscu jest deklarator funkcji\*/  
 *Specyfikatory deklaracji* opt*seq atrybutu* opt*lista deklaracji deklarator* opt*złożonej instrukcji*  
  
 /\**seq atrybutu* jest Specific Microsoft * /  
  
 Prototyp parametry są:  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *Lista deklaracji*:  
 *Deklaracja*  
  
 *Lista deklaracji deklaracji*  
  
 `declarator`:  
 *wskaźnik* opt*bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*: /\* deklarator funkcji\*/  
 *deklarator bezpośrednio***(***listy parametrów typu***)** / * nowy styl deklarator      \*/  
  
 *deklarator bezpośrednio***(***listy identyfikatorów* opt**)** / * przestarzały styl deklarator    \*/  
  
 Lista parametrów w definicji używa następującej składni:  
  
 *listy parametrów typu*: /\* listy parametrów\*/  
 *listy parametrów*  
  
 *Lista parametrów* **,...**  
  
 *Lista parametrów*:  
 *Deklaracja parametru*  
  
 *Lista parametrów* **,***deklaracji parametru*   
  
 *Deklaracja parametru*:  
 *Specyfikatory deklaracji deklarator*  
  
 *Specyfikatory deklaracji abstrakcji deklarator* opcjonalnych  
  
 Lista parametrów w definicji funkcji w starym stylu używa następującej składni:  
  
 *Lista identyfikatorów*: /\* używany w funkcji przestarzały styl definicje i deklaracje\*/  
 *Identyfikator*  
  
 *Lista identyfikatorów* **,***identyfikator*   
  
 Składnia treści funkcji to:  
  
 *instrukcji złożonej*: /\* treść funkcji\*/  
 **{**`declaration`-*listy* opt*listy instrukcji* opt**}**   
  
 Są tylko specyfikatory klasy magazynowania, które można modyfikować deklaracji funkcji `extern` i **statycznych**. `extern` Specyfikator oznacza, że funkcja mogą być przywoływane z innych plików; oznacza to, że nazwa funkcji są eksportowane do konsolidatora. **Statycznych** specyfikator oznacza, że funkcja nie może być przywoływany z innych plików; oznacza to, że nazwa nie jest eksportowany przez konsolidator. Jeśli klasa magazynu nie znajduje się w definicji funkcji `extern` zakłada, że. W każdym przypadku funkcji jest zawsze widoczne z punktu definicji na końcu pliku.  
  
 Opcjonalny *specyfikatory deklaracji* i obowiązkowe `declarator` jednocześnie określić typ zwracany funkcji i nazwę. `declarator` Jest kombinacją identyfikatora nazwy funkcji i nawiasy po nazwie funkcji. Opcjonalny *seq atrybutu* nonterminal specyficzne dla firmy Microsoft jest zdefiniowany w funkcji [atrybuty funkcji](../c-language/function-attributes.md).  
  
 *Deklarator bezpośrednio* (w `declarator` składni) Określa nazwę definiowanego funkcji i identyfikatory jego parametrów. Jeśli *deklarator bezpośrednio* obejmuje *listy parametrów typu*, listy określa typy wszystkich parametrów. Takie deklaratorze służy również jako prototyp funkcji nowsze wywołania funkcji.  
  
 A `declaration` w *lista deklaracji* w funkcji nie mogą zawierać definicji *Specyfikator klasy magazynu* innych niż **zarejestrować**. *Specyfikatora typu* w *specyfikatory deklaracji* składni można pominąć tylko wtedy, gdy **zarejestrować** Klasa magazynu jest określony dla wartości `int` typu.  
  
 *Instrukcji złożonej* treść funkcja zawierająca deklaracje zmiennej lokalnej, odwołania do elementów zewnętrznie zadeklarowane oraz instrukcje.  
  
 Sekcje [atrybuty funkcji](../c-language/function-attributes.md), [Klasa magazynu](../c-language/storage-class.md), [typu zwracanego](../c-language/return-type.md), [parametry](../c-language/parameters.md), i [treści funkcji](../c-language/function-body.md) opisano składniki wynikającego z definicji funkcji szczegółowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../c-language/functions-c.md)