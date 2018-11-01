---
title: Preprocesor
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: bd139dcbbbe519cc4c9750a657f8b47c5a5bcd18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530969"
---
# <a name="preprocessor"></a>Preprocesor
Preprocesor jest procesora tekstu, która manipuluje tekst pliku źródłowego w ramach pierwszej fazy tłumaczenia. Preprocesor nie analizuje tekst źródłowy, ale jej Podziel je na tokeny na potrzeby znajdowania wywołania makra. Mimo że kompilator wywołuje zazwyczaj preprocesor w jego pierwszym przebiegu, preprocesor można również wywołać oddzielnie do przetwarzania tekstu bez kompilacji.

Materiał odniesienia na preprocesora zawiera następujące sekcje:

- [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)

- [Operatory preprocesora](../preprocessor/preprocessor-operators.md)

- [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)

- [Pragmy](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft Specific**

Możesz uzyskać go w kodzie źródłowym po przetwarzanie wstępne za pomocą [/E](../build/reference/e-preprocess-to-stdout.md) lub [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) — opcja kompilatora. Obie opcje preprocesora wywołania i wynikowy tekst na urządzeniu standardowe dane wyjściowe, które w większości przypadków to konsola danych wyjściowych polecenia. Różnica między dwie opcje jest, że zawiera /E `#line` dyrektywy i /EP usuwa te dyrektywy się.

**END specyficzny dla Microsoft**

##  <a name="_predir_special_terminology"></a> Terminologię

W dokumentacji preprocesora termin "argument" odnosi się do jednostki, który jest przekazywany do funkcji. W niektórych przypadkach jest on zmodyfikowany przez "rzeczywiste" lub "formalnych", której opisano wyrażenie argumentu, określone w wywołaniu funkcji i deklaracji argumentów odpowiednio określone w definicji funkcji.

Termin "Zmienna" odnosi się do obiektu proste danych typu C. Termin "object" odnosi się do obiektu języka C++ i zmiennych; to termin (włącznie).

## <a name="see-also"></a>Zobacz też

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Fazy tłumaczenia](../preprocessor/phases-of-translation.md)