---
title: "Treść funkcji | Dokumentacja firmy Microsoft"
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
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a0c85ecf0752ff34bf5b61e42309360f2bc4d448
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="function-body"></a>Treść funkcji
"Treści funkcji" jest instrukcji złożonej zawierającej instrukcje, które określają, jak działa funkcja.  
  
## <a name="syntax"></a>Składnia  
 *Definicja funkcji*:  
 *Specyfikatory deklaracji* opt*seq atrybutu* opt*lista deklaracji deklarator* opt*złożonej instrukcji*  
  
 /\* *Atrybut seq* jest Specific Microsoft * /  
  
 *instrukcji złożonej*: /\* treść funkcji \*/  
 **{***lista deklaracji* opt*listy instrukcji* opt**}**   
  
 Zmienne zadeklarowane w treści funkcji "zmiennych lokalnych," mają **automatycznie** klasy magazynu, chyba że określono inaczej. Po wywołaniu funkcji magazynu jest tworzone dla zmiennych lokalnych i Inicjowanie lokalnych są wykonywane. Kontrola wykonywania przekazuje do pierwszej instrukcji w *instrukcji złożonej* i jest kontynuowane do `return` wykonać instrukcji lub napotkano koniec treści funkcji. Formant zwraca do punktu, w którym została wywołana funkcja.  
  
 A `return` instrukcji zawierającej wyrażenie musi zostać wykonana, jeśli funkcja znajduje się w celu zwrócenia wartości. Wartość zwracana funkcji jest niezdefiniowana, jeśli nie `return` wykonać instrukcji lub jeśli `return` instrukcji nie zawiera wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)