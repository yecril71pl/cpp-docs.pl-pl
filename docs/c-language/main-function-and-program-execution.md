---
title: Funkcja main i wykonywanie programu
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: d16f8a5b7b6b23ad90aad886bbb9654e706549cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325822"
---
# <a name="main-function-and-program-execution"></a>Funkcja main i wykonywanie programu

Każdy program języka C ma funkcję (główną) podstawowy musi mieć nazwę **głównego**. Jeśli w swoim kodzie przestrzegasz modelu programowania Unicode, możesz użyć wersja znaków dwubajtowych **głównego**, **wmain**. **Głównego** funkcji służy jako punkt początkowy podczas wykonywania programu. Zwykle kontroluje wykonywanie programu przez kierowanie wywołań do innych funkcji programu. Program zwykle zatrzymuje wykonywanie na końcu **głównego**, chociaż może zostać przerwany w innych punktach programu różnych powodów. Niekiedy po wykryciu określonego błędu, możesz chcieć wymusić przerwanie programu. Aby to zrobić, należy użyć **wyjść** funkcji. Zobacz *odwołanie do biblioteki wykonawczej* informacji na temat i przykłady dotyczące używania [wyjść](../c-runtime-library/reference/exit-exit-exit.md) funkcji.

## <a name="syntax"></a>Składnia

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Uwagi

Funkcje w kodzie źródłowym programu wykonują co najmniej jedno określone zadanie. **Głównego** funkcja może wywołać te funkcje, aby wykonać poszczególne zadania. Gdy **głównego** wywołuje inną funkcję, przekazuje jej sterowanie wykonaniem funkcji, dzięki czemu zaczyna się od pierwszej instrukcji danej funkcji. Funkcja zwraca sterowanie do **głównego** podczas `return` zostaje wykonana instrukcja lub po osiągnięciu końca funkcji.

Można zadeklarować dowolną funkcję, w tym **głównego**, aby miała parametry. Termin „parametr” lub „parametr formalny” dotyczy identyfikatora, który otrzymuje wartość przekazaną do funkcji. Zobacz [parametry](../c-language/parameters.md) instrukcje dotyczące przekazywania argumentów do parametrów. Gdy jedna funkcja wywołuje drugą, wywoływana funkcja otrzymuje wartości swoich parametrów od funkcji wywołującej. Wartości te są nazywane „argumentami”. Możesz deklarować Parametry formalne dla **głównego** tak, że może ona otrzymywać argumenty z wiersza polecenia, używając następującego formatu:

Jeśli chcesz przekazać informacje do **głównego** funkcji, parametry są tradycyjnie nazywane `argc` i `argv`, mimo że kompilator języka C nie wymaga tych nazw. Typy dla `argc` i `argv` są zdefiniowane przez język C. Tradycyjnie, jeśli trzeci parametr jest przekazywany do **głównego**, ten parametr nosi nazwę `envp`. Przykłady w dalszej części sekcji pokazują, w jaki sposób używać tych trzech parametrów, aby uzyskać dostęp do argumentów wiersza polecenia. W poniższych sekcjach opisano te parametry.

Zobacz [korzystanie z wmain](../c-language/using-wmain.md) opis wersja znaków dwubajtowych **głównego**.

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)<br/>
[Analizowanie argumentów wiersza polecenia języka C](../c-language/parsing-c-command-line-arguments.md)
