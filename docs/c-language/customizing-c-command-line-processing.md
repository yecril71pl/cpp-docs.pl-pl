---
title: Dostosowywanie przetwarzania w wierszu polecenia C | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 00194acd1aa72db73f75a2cb5aa5700df02be0a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C
Jeśli program nie przyjmuje argumentów wiersza polecenia, można zapisać małej ilości miejsca, wyłączając użyj procedury biblioteki, który wykonuje przetwarzania w wierszu polecenia. Ta procedura jest wywoływana **_setargv —** (lub **_wsetargv** w środowisku znaków dwubajtowych), zgodnie z opisem w [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md). Aby pominąć jego użycia, zdefiniuj procedury, które nie działają w pliku zawierającego **głównego** funkcji i nadaj mu nazwę **_setargv —** (lub **_wsetargv** w znaków dwubajtowych Środowisko). Wywołanie **_setargv —** lub **_wsetargv** następnie spełniać definicja **_setargv —** lub **_wsetargv** , i jest w wersji biblioteki Nie załadowano.  
  
 Podobnie jeśli nigdy nie dostępu do tabeli środowiska za pośrednictwem `envp` argumentu, możesz podać własne pusty procedury do użycia zamiast **_setenvp —** (lub **_wsetenvp**), Procedura przetwarzania w środowisku.  
  
 Jeśli program wykonywania wywołań do **_spawn** lub **_exec —** rodziny procedury biblioteki wykonawcze języka C, możesz ma nie pomijać procedura przetwarzania w środowisku, ponieważ ta procedura służy do przekazania środowisko z procesu ikrę do nowego procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja Main i wykonywanie programu](../c-language/main-function-and-program-execution.md)