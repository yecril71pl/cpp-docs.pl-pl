---
title: Funkcja Main i wykonywanie programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca08ecc5be82ec256320c87a9a49e354dccd40f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387502"
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