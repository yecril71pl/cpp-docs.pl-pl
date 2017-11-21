---
title: "Dostosowywanie przetwarzania w wierszu polecenia języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _setenvp
- _setargv
dev_langs: C++
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9a804d38fa14fd77a68c53504814503042c2234a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Jeśli program nie przyjmuje argumentów wiersza polecenia, można zapisać małej ilości miejsca, wyłączając użyj procedury biblioteki, który wykonuje przetwarzania w wierszu polecenia. Ta procedura jest wywoływana **_setargv —** i jest opisany w [rozwijanie symbolu wieloznacznego](../cpp/wildcard-expansion.md). Aby pominąć jego użycia, zdefiniuj procedury, które nie działają w pliku zawierającego **głównego** funkcji i nadaj mu nazwę **_setargv —**. Wywołanie **_setargv —** następnie spełniać definicja **_setargv —**, i nie jest załadowana wersja biblioteki.  
  
 Podobnie jeśli nigdy nie dostępu do tabeli środowiska za pośrednictwem `envp` argumentu, możesz podać własne pusty procedury do użycia zamiast **_setenvp —**, procedura przetwarzania w środowisku. Tylko jako z **_setargv —** funkcji **_setenvp —** musi być zadeklarowany jako **zewnętrzne "C"**.  
  
 Program może wykonywać wywołania do **spawn** lub `exec` rodziny procedur biblioteki wykonawcze języka C. Jeśli tak jest, nie ma pomijać procedura przetwarzania w środowisku, ponieważ ta procedura służy do przekazywania środowisko z procesu nadrzędnego do procesu podrzędnego.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)