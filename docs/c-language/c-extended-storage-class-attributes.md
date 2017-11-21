---
title: C rozszerzone atrybuty klasy magazynu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 119de1e705a0e3de93aadc61d38ecdde2fc43fe9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-extended-storage-class-attributes"></a>Rozszerzone atrybuty klasy magazynu języka C
**Dotyczące firmy Microsoft**  
  
 Więcej aktualne informacje na ten temat można znaleźć w [__declspec (C++ — dokumentacja)](../cpp/declspec.md).  
  
 Atrybut rozszerzony składni upraszcza i standaryzuje rozszerzenia specyficzne dla firmy Microsoft dla języka C. Atrybuty klasy magazynu, które należy użyć składni rozszerzonych atrybutów obejmują wątku naked dllimport i dllexport.  
  
 Składnia atrybutu rozszerzonego służący do określania informacji o klasie magazynu używa __declspec — słowo kluczowe, które określa, że wystąpienie podanego typu do przechowania atrybuty klasy magazynu specyficzne dla firmy Microsoft (wątek naked dllimport i dllexport). Przykładami innych modyfikatorów klasy magazynowania statyczne i zewnętrzne słów kluczowych. Jednak te słowa kluczowe są częścią ANSI C standard i jako takie nie są objęte składni rozszerzonych atrybutów.  
  
## <a name="syntax"></a>Składnia  
 *Specyfikator klasy magazynu*:  
 `__declspec`( *rozszerzony decl — modyfikator seq* ) / * Specific firmy Microsoft\*/  
  
 *rozszerzony decl — modyfikator seq*:  
 *rozszerzony decl — modyfikator* opcjonalnych  
  
 *rozszerzony rozszerzony decl — modyfikator seq — decl — modyfikator*  
  
 *rozszerzony decl — modyfikator*:  
 **Wątek**  
  
 **naked**  
  
 **DllImport**  
  
 `dllexport`  
  
 Biały znak oddziela Modyfikatory deklaracji. Należy pamiętać, że *rozszerzony decl — modyfikator seq* może być pusta; w takim przypadku __declspec nie ma wpływu.  
  
 Wątek naked dllimport i dllexport atrybuty klasy magazynu są właściwościami tylko deklaracji danych lub funkcji, do której są stosowane; nie one ponownie zdefiniować atrybuty typu samej funkcji. Atrybut wątku dotyczy tylko danych. Atrybut naked dotyczy tylko funkcji. Atrybut dllimport i dllexport dotyczą funkcji i danych.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)