---
title: "Błąd cxx0036 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0036
dev_langs: C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdf6ddf412786a53ec8da995c2824274da2da3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0036"></a>Błąd CXX0036 programu Expression Evaluator
Zły kontekst {...} specyfikacja  
  
 Ten komunikat może zostać wygenerowany przez żadnego kilka błędów w przypadku użycia operatora kontekstu (**{}**).  
  
-   Składnia operatora kontekstu (**{}**) podano niepoprawnie.  
  
     Składnia operatora kontekstu jest następująca:  
  
     {*funkcja*,*modułu*,*dll*}*wyrażenia*  
  
     Określa kontekst *wyrażenia*. Operator kontekstu ma taką samą pierwszeństwo i użycia jako rzutowanie typu.  
  
     Można je pominąć końcowe przecinkami. Jeśli dowolny z *funkcja*, *modułu*, lub *biblioteki dll* zawiera literał przecinek całą nazwę należy ująć w nawias.  
  
-   Nazwa funkcji została błędnie wpisana lub nie istnieje w określonym module lub biblioteki dll.  
  
     Ponieważ C jest rozróżniana wielkość liter języka, *funkcja* musi być podany w dokładnej zdefiniowane w źródle.  
  
-   Nie można odnaleźć modułu lub biblioteki DLL.  
  
     Sprawdź pełną nazwę ścieżki określonego modułu lub biblioteki DLL.  
  
 Ten błąd jest taki sam jak CAN0036.