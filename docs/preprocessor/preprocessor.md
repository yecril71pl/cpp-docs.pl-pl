---
title: Preprocesor
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 883504810f1b659e28764a75ebc7cfda325920a5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222236"
---
# <a name="preprocessor"></a>Preprocesor

Preprocesor jest procesorem tekstowym, który manipuluje tekstem pliku źródłowego w pierwszej fazie tłumaczenia. Preprocesor nie przeanalizuje tekstu źródłowego, ale podzieli go na tokeny umożliwiające lokalizowanie wywołań makr. Chociaż kompilator zwykle wywołuje preprocesor podczas pierwszego przebiegu, preprocesor może być również wywoływany oddzielnie, aby przetwarzać tekst bez kompilowania.

Materiał referencyjny w preprocesorach zawiera następujące sekcje:

- [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)

- [Operatory preprocesora](../preprocessor/preprocessor-operators.md)

- [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)

- [Pragmy](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft Specific**

Możesz uzyskać listę kodu źródłowego po wstępnej przejściu przy użyciu opcji kompilatora [/e](../build/reference/e-preprocess-to-stdout.md) lub [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) . Obie opcje wywołują preprocesor i wysyłają wynikowy tekst do standardowego urządzenia wyjściowego, które w większości przypadków jest konsolą programu. Różnica między tymi dwiema opcjami `/E` obejmuje dyrektywy, a `/EP` także `#line` paski te dyrektywy.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

##  <a name="_predir_special_terminology"></a>Specjalna terminologia

W dokumentacji preprocesora termin "argument" odwołuje się do jednostki, która jest przenoszona do funkcji. W niektórych przypadkach jest on modyfikowany przez "rzeczywiste" lub "formalne", który opisuje wyrażenie argumentu określone w wywołaniu funkcji i deklarację argumentu określoną odpowiednio w definicji funkcji.

Termin "zmienna" odnosi się do prostego obiektu danych typu C. Termin "Object" odnosi się zarówno C++ do obiektów, jak i zmiennych. jest to termin włącznie.

## <a name="see-also"></a>Zobacz także

[Dokumentacja językaC++ C/preprocesora](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fazy tłumaczenia](../preprocessor/phases-of-translation.md)
