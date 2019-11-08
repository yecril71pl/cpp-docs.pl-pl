---
title: Odwołania preprocesora języka C/C++
ms.date: 10/31/2019
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: ef93f2cb98a033eed539ffc25559937b274d8a21
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754084"
---
# <a name="cc-preprocessor-reference"></a>Odwołania preprocesora języka C/C++

*Dokumentacja C/C++ preprocesora* objaśnia preprocesor, ponieważ jest zaimplementowany w Microsoft C/.C++ Preprocesor wykonuje wstępne operacje na C i C++ plikach przed przekazaniem ich do kompilatora. Preprocesora można użyć do warunkowego kompilowania kodu, wstawiania plików, określania komunikatów o błędach w czasie kompilacji i stosowania reguł specyficznych dla maszyn do sekcji kodu.

W programie Visual Studio 2019 opcja kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) włącza nową implementację preprocesora. Nowa implementacja jest nadal w toku i dlatego jest uważana za eksperymentalną. Ma ona ostatecznie być zgodna z C99, C11 i C++ 20. Aby uzyskać więcej informacji, zobacz [MSVC eksperymentalny preprocesora — Omówienie](preprocessor-experimental-overview.md).

## <a name="in-this-section"></a>W tej sekcji

[Preprocesor](preprocessor.md)\
Zawiera przegląd tradycyjnych i nowych eksperymentalnych preprocesora.

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)\
Opisuje dyrektywy, zwykle używane do łatwego zmieniania i łatwego kompilowania programów źródłowych w różnych środowiskach wykonawczych.

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)\
Omawia cztery operatory specyficzne dla preprocesora używane w kontekście dyrektywy `#define`.

[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)\
Omawia wstępnie zdefiniowane makra określone przez ANSI i firmę C++Microsoft.

[Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
W tym artykule omówiono dyrektywy pragma, które udostępniają sposób, w jaki każdy kompilator oferuje funkcje specyficzne dla komputera i systemu operacyjnego przy zachowaniu ogólnej zgodności C++ z językami C i.

## <a name="related-sections"></a>Sekcje pokrewne

informacje dotyczące języka\ [ C++ ](../cpp/cpp-language-reference.md)
Zapewnia materiał referencyjny dla implementacji C++ języka firmy Microsoft.

[Dokumentacja języka C](../c-language/c-language-reference.md)\
Zapewnia materiał referencyjny dla implementacji języka C firmy Microsoft.

[Dokumentacja językaC++ C/build](../build/reference/c-cpp-building-reference.md)\
Zawiera łącza do tematów omawiających opcje kompilatora i konsolidatora.

[Projekty programu Visual Studio C++ —](../build/creating-and-managing-visual-cpp-projects.md)\
Opisuje interfejs użytkownika w programie Visual Studio, który umożliwia określenie katalogów, które system projektu będzie przeszukiwać w celu zlokalizowania plików dla C++ projektu.
