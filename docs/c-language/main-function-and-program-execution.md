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
ms.openlocfilehash: 28b0d826dc02376f952d3522f2f037eacd298b8e
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123945"
---
# <a name="main-function-and-program-execution"></a>Funkcja main i wykonywanie programu

Każdy program C ma podstawową (główną) funkcję, która musi mieć nazwę **Main**. Jeśli kod jest zgodny z modelem programowania **Unicode, można**użyć szerokiej wersji **wmain**. Funkcja **Main** służy jako punkt wyjścia do wykonywania programu. Zwykle kontroluje wykonywanie programu przez kierowanie wywołań do innych funkcji programu. Program zwykle zatrzymuje wykonywanie na końcu **głównej**, chociaż może zakończyć się w innych punktach w programie z różnych powodów. Niekiedy po wykryciu określonego błędu, możesz chcieć wymusić przerwanie programu. Aby to zrobić, użyj funkcji **Exit** . Zobacz *odwołanie do biblioteki wykonawczej* , aby uzyskać informacje na temat i przykład przy użyciu funkcji [Exit](../c-runtime-library/reference/exit-exit-exit.md) .

## <a name="syntax"></a>Składnia

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Uwagi

Funkcje w kodzie źródłowym programu wykonują co najmniej jedno określone zadanie. Funkcja **Main** może wywoływać te funkcje, aby wykonać odpowiednie zadania. Gdy **Główne** wywołuje inną funkcję, przekazuje sterowanie wykonywaniem do funkcji, tak aby wykonywanie rozpoczyna się od pierwszej instrukcji w funkcji. Funkcja zwraca sterowanie do elementu **głównego** , gdy zostanie wykonana instrukcja `return` lub gdy zostanie osiągnięty koniec funkcji.

Można zadeklarować dowolną funkcję, w tym **Main**, w celu posiadania parametrów. Termin „parametr” lub „parametr formalny” dotyczy identyfikatora, który otrzymuje wartość przekazaną do funkcji. Aby uzyskać informacje na temat przekazywania argumentów do parametrów, zobacz [Parametry](../c-language/parameters.md) . Gdy jedna funkcja wywołuje drugą, wywoływana funkcja otrzymuje wartości swoich parametrów od funkcji wywołującej. Wartości te są nazywane „argumentami”. Można zadeklarować formalne parametry do **Main** , aby można było odbierać argumenty z wiersza polecenia przy użyciu tego formatu:

Gdy chcesz przekazać informacje do funkcji **Main** , parametry są tradycyjnie nazwane `argc` i `argv`, chociaż kompilator języka C nie wymaga tych nazw. Typy dla `argc` i `argv` są zdefiniowane przez język C. Tradycyjnie, jeśli trzeci parametr jest przesyłany do **Main**, ten parametr ma nazwę `envp`. Przykłady w dalszej części sekcji pokazują, w jaki sposób używać tych trzech parametrów, aby uzyskać dostęp do argumentów wiersza polecenia. W poniższych sekcjach opisano te parametry.

Aby uzyskać opis szerokiej **wersji programu,** zobacz [using wmain](../c-language/using-wmain.md) .

## <a name="see-also"></a>Zobacz także

[Funkcja Main i argumenty wiersza poleceniaC++()](../cpp/main-function-command-line-args.md)\
[Analizowanie argumentów wiersza polecenia języka C](../c-language/parsing-c-command-line-arguments.md)
