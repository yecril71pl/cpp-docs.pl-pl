---
title: Preprocesor
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337510"
---
# <a name="preprocessor"></a>Preprocesor

Preprocesor jest procesorem tekstu, który manipuluje tekstem pliku źródłowego w ramach pierwszej fazy tłumaczenia. Preprocesor nie analizuje tekstu źródłowego, ale rozbija go na tokeny, aby zlokalizować wywołania makr. Chociaż kompilator zwykle wywołuje preprocesora w pierwszym przebiegu, preprocesor można również wywołać oddzielnie do przetwarzania tekstu bez kompilacji.

Materiał odniesienia na preprocesorze zawiera następujące sekcje:

- [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)

- [Operatory preprocesora](../preprocessor/preprocessor-operators.md)

- [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)

- [Pragmy](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Specyficzne dla firmy Microsoft**

Po wstępnym przetworzeniu można uzyskać listę kodu źródłowego przy użyciu opcji kompilatora [/E](../build/reference/e-preprocess-to-stdout.md) lub [/EP.](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) Obie opcje wywołać preprocesora i wysłać wynikowy tekst do standardowego urządzenia wyjściowego, który w większości przypadków jest konsola. Różnica między tymi dwoma `/E` opcjami polega na tym, że obejmuje `#line` to dyrektywy i `/EP` usuwa te dyrektywy.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>Terminologia specjalna

W dokumentacji preprocesora termin "argument" odnosi się do jednostki, która jest przekazywana do funkcji. W niektórych przypadkach jest modyfikowany przez "rzeczywiste" lub "formalne", który opisuje wyrażenie argumentu określone w wywołaniu funkcji i deklarację argumentu określoną w definicji funkcji, odpowiednio.

Termin "zmienna" odnosi się do prostego obiektu danych typu C. Termin "obiekt" odnosi się zarówno do obiektów języka C++, jak i zmiennych; jest to termin integracyjny.

## <a name="see-also"></a>Zobacz też

[Odwołanie do preprocesora C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fazy tłumaczenia](../preprocessor/phases-of-translation.md)
