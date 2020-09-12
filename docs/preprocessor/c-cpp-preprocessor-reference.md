---
title: Odwołania preprocesora języka C/C++
description: Dokumentacja preprocesora kompilatora języka Microsoft C/C++ w programie Visual Studio.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e53f7270a71e5e7c3f456be7d55d49eaf352aecb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040746"
---
# <a name="cc-preprocessor-reference"></a>Odwołania preprocesora języka C/C++

*Dokumentacja preprocesora języka C/C++* wyjaśnia preprocesor, który jest zaimplementowany w Microsoft C/c++. Preprocesor wykonuje wstępne operacje na plikach C i C++ przed przekazaniem ich do kompilatora. Preprocesora można użyć do warunkowego kompilowania kodu, wstawiania plików, określania komunikatów o błędach w czasie kompilacji i stosowania reguł specyficznych dla maszyn do sekcji kodu.

W programie Visual Studio 2019 opcja kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) włącza nową implementację preprocesora. Nowa implementacja jest nadal w toku i dlatego jest uważana za eksperymentalną. Ma ona ostatecznie być zgodna z C99, C11 i C++ 20. Aby uzyskać więcej informacji, zobacz temat [MSVC New preprocesora Overview](preprocessor-experimental-overview.md).

## <a name="in-this-section"></a>W tej sekcji

[Preprocesora](preprocessor.md)\
Zawiera omówienie tradycyjnych i nowych preprocesorów preprocesora.

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)\
Opisuje dyrektywy, zwykle używane do łatwego zmieniania i łatwego kompilowania programów źródłowych w różnych środowiskach wykonawczych.

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)\
Omawia cztery operatory specyficzne dla preprocesora używane w kontekście `#define` dyrektywy.

[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)\
Omawia wstępnie zdefiniowane makra określone przez standardy C i C++ oraz Microsoft C++.

[Pragm](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
W tym artykule omówiono dyrektywy pragma, które oferują sposób, aby każdy kompilator oferował funkcje specyficzne dla komputera i systemu operacyjnego przy zachowaniu ogólnej zgodności z językami C i C++.

## <a name="related-sections"></a>Sekcje pokrewne

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)\
Zapewnia materiał referencyjny dla implementacji języka C++ firmy Microsoft.

[Dokumentacja języka C](../c-language/c-language-reference.md)\
Zapewnia materiał referencyjny dla implementacji języka C firmy Microsoft.

[Dokumentacja kompilacji C/C++](../build/reference/c-cpp-building-reference.md)\
Zawiera łącza do tematów omawiających opcje kompilatora i konsolidatora.

[Projekty programu Visual Studio — C++](../build/creating-and-managing-visual-cpp-projects.md)\
Opisuje interfejs użytkownika w programie Visual Studio, który umożliwia określenie katalogów, które system projektu będzie przeszukiwać w celu zlokalizowania plików dla projektu języka C++.
