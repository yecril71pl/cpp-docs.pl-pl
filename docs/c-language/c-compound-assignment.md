---
title: "Przydział złożony języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8771aba4328cef785347712f037ea21c5a46cfad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-compound-assignment"></a>Przydział złożony języka C
Operatory przypisania złożone łączyć operator przypisania prostego z innego operatora binarnego. Operatory przypisania złożonej operacji określony przez operator dodatkowe, a następnie przypisz wynik Lewy argument operacji. Na przykład, wyrażenie złożone przypisania, takich jak  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 należy traktować jako  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 Jednak przypisania złożone wyrażenie nie jest odpowiednikiem rozszerzona wersja ponieważ przypisania złożone wyrażenie *wyrażenie1* tylko jeden raz, podczas gdy ocenia rozszerzona wersja  *wyrażenie1* dwa razy: operacja dodawania i w operacji przypisania.  
  
 Argumenty operacji operatora przypisania złożone musi być typu całkowitą lub zmiennoprzecinkową. Każdy operator przypisania złożone wykonuje konwersje, że odpowiedni operator binarny wykonuje i odpowiednio ograniczył typy argumentów. Przypisania dodawania (`+=`) i Przypisanie odejmowania (**-=**) operatory ma także lewy operand typu wskaźnika, w których przypadku prawostronny operand musi być typu całkowitego. Wynik operacji przypisania złożone ma wartość i typ Lewy argument operacji.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 W tym przykładzie bitowe włącznie i operacja została wykonana na `n` i `MASK`, a wynik jest przypisany do `n`. Stała manifestu `MASK` jest zdefiniowana z [#define](../preprocessor/hash-define-directive-c-cpp.md) dyrektywy preprocesora.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory przypisania w języku C](../c-language/c-assignment-operators.md)