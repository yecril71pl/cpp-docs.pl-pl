---
title: Funkcja Main i wykonywanie programu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7635595adedf961c014bf8792316ca4943dc84a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="main-function-and-program-execution"></a>Funkcja main i wykonywanie programu
Każdy program C ma podstawowej funkcji (głównego), która musi mieć nazwę **głównego**. Jeśli kod jest zgodna z modelem programowania Unicode, można użyć znaków dwubajtowych wersja **głównego**, **wmain**. **Głównego** funkcji służy jako punkt początkowy dla wykonania programu. Zwykle kontroluje wykonywanie programu przez kierowanie wywołań do innych funkcji programu. Program przestanie zazwyczaj wykonywane na końcu **głównego**, chociaż może obsłużyć w innych punktach programu z różnych przyczyn. Niekiedy po wykryciu określonego błędu, możesz chcieć wymusić przerwanie programu. Aby to zrobić, użyj **zakończyć** funkcji. Zobacz *odwołanie do biblioteki wykonawczej* informacji na temat i przykład za pomocą [zakończyć](../c-runtime-library/reference/exit-exit-exit.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
main( int argc, char *argv[ ], char *envp[ ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcje w kodzie źródłowym programu wykonują co najmniej jedno określone zadanie. **Głównego** funkcji można wywoływać te funkcje do wykonywania odpowiednich zadań. Gdy **głównego** wywołuje funkcję innego przekazaniem kontroli wykonania funkcji, dzięki czemu wykonanie zaczyna się od pierwszą instrukcją w funkcji. Funkcja sterowania **głównego** podczas `return` wykonać instrukcji lub po osiągnięciu końca funkcji.  
  
 Można zadeklarować dowolnej funkcji, łącznie z **głównego**, aby mieć parametrów. Termin „parametr” lub „parametr formalny” dotyczy identyfikatora, który otrzymuje wartość przekazaną do funkcji. Zobacz [parametry](../c-language/parameters.md) informacji na przekazywanie argumentów do parametrów. Gdy jedna funkcja wywołuje drugą, wywoływana funkcja otrzymuje wartości swoich parametrów od funkcji wywołującej. Wartości te są nazywane „argumentami”. Można zadeklarować parametrów formalnych do **głównego** , dzięki czemu może odbierać argumenty wiersza polecenia, używając następującego formatu:  
  
 Jeśli chcesz przekazać informacje do **głównego** funkcji parametry tradycyjnie są nazywane `argc` i `argv`, mimo że kompilator języka C nie wymaga te nazwy. Typy dla `argc` i `argv` są zdefiniowane przez język C. Tradycyjnie, jeśli innej parametr jest przekazywany do **głównego**, nosi nazwę parametru `envp`. Przykłady w dalszej części sekcji pokazują, w jaki sposób używać tych trzech parametrów, aby uzyskać dostęp do argumentów wiersza polecenia. W poniższych sekcjach opisano te parametry.  
  
 Zobacz [korzystanie z wmain](../c-language/using-wmain.md) opis wersji znaków dwubajtowych **głównego**.  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)