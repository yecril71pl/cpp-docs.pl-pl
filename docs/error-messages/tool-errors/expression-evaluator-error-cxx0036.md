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
ms.openlocfilehash: 58d5fa976306c6e8a2545ce852bf3e808bc5b2d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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