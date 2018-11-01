---
title: Makra i język C++
ms.date: 11/04/2016
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: cd5d1237bc025cceb25cc290509b929b595a215f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499895"
---
# <a name="macros-and-c"></a>Makra i język C++
C++ zawiera nowe funkcje, niektóre z nich ograniczyć te udostępniane przez ANSI C preprocesora. Te nowe możliwości zwiększenia bezpieczeństwa i stabilności języka:

- W języku C++, obiekty zadeklarowane jako **const** mogą być używane w wyrażeniach stałych. Dzięki temu programy do deklarowania stałych, które mają typ i informacje o wartości i wyliczenia, które mogą być wyświetlane symbolicznie za pomocą debugera. Za pomocą preprocesora `#define` dyrektywy do definiowania stałych nie jest tak dokładny. Magazyn nie jest przydzielany dla **const** obiektu, chyba że wyrażenie, które przyjmuje adres znajduje się w programie.

- Możliwości funkcji wbudowanych C++ otrzymuje makra typu funkcji. Zalety korzystania z funkcji śródwierszowych za pośrednictwem makra są:

    - Bezpieczeństwo typów. Funkcje śródwierszowe jest zależna od tego samego typu, sprawdzanie jako normalnych funkcji. Makra nie są bezpieczne dla typów.

    - Obsługa poprawne argumenty, które mają skutki uboczne. Funkcje śródwierszowe oceny wyrażenia dostarczone jako argumenty przed rozpoczęciem treści funkcji. Dlatego jest bez możliwości wyrażenie z efektami ubocznymi będzie niebezpieczne.

Aby uzyskać więcej informacji na temat wbudowanych funkcjach, zobacz [w tekście, __inline, \__forceinline](../cpp/inline-functions-cpp.md).

W celu zapewnienia zgodności z poprzednimi wersjami wszystkich preprocesora obiektach, które istniały w ANSI C i C++ specyfikacjach wcześniejszych zostaną zachowane dla Microsoft C++.

## <a name="see-also"></a>Zobacz też

[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)<br/>
[Makra (C/C++)](../preprocessor/macros-c-cpp.md)