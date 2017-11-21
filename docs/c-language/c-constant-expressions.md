---
title: "Wyrażenia stałe języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e7b9beac4d87e0580279190cca005fc56c951af8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C
Wyrażenie stałe jest oceniane w czasie kompilacji w czasie wykonywania nie i można w dowolnym miejscu może służyć stałą. Stałe wyrażenia musi być stała, który znajduje się w zakresie można przedstawić wartości dla tego typu. Operandy wyrażenia stałego można być stałe całkowite, stałe znakowe, stałe zmiennoprzecinkowe, stałe wyliczenie typu rzutowania, `sizeof` wyrażenia i inne wyrażenia stałej.  
  
## <a name="syntax"></a>Składnia  
 *wyrażenia*:  
 *wyrażenia warunkowego*  
  
 *wyrażenia warunkowego*:  
 *wyrażenie logiczne OR*  
  
 *wyrażenia logicznego lub* **?**  *wyrażenie* **:***wyrażenia warunkowego*   
  
 *wyrażenie*:  
 *wyrażenia przypisania*  
  
 *wyrażenie* **,***wyrażenia przypisania*   
  
 *wyrażenia przypisania*:  
 *wyrażenia warunkowego*  
  
 *wyrażenie jednoargumentowe operator przypisania z wyrażenia przypisania*  
  
 *operator przypisania*: jeden z  
 **= \*= /= %= += -= <\<= >>= &= ^= &#124;=**  
  
 Zawierać symboli nieterminalnych deklarator struktury, moduł wyliczający, bezpośrednie deklarator, deklarator abstrakcyjny bezpośrednio i labeled — instrukcja *wyrażenia* nonterminal.  
  
 Wyrażeniu dającym stałą musi zostać użyty do określenia rozmiar pola bitowego członka struktury, wartość stała wyliczenia, rozmiaru tablicy lub wartość **przypadku** stałej.  
  
 Wyrażenia stałe używane w dyrektywy preprocesora obowiązują dodatkowe ograniczenia. W związku z tym są określane jako "ograniczone wyrażenia stałej". Ograniczone wyrażenie stałej nie może zawierać `sizeof` wyrażenia stałe wyliczenie typu rzutowania do dowolnego typu lub stałe typów zmiennoprzecinkowych. Może jednak zawierać specjalnych wyrażenie stałe `defined (` *identyfikator*`)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Operandy i wyrażenia](../c-language/operands-and-expressions.md)