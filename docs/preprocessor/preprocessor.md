---
title: Preprocesor
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: b1443d88fdba470cb8ed5058c9a9012bfbdc5bc7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028577"
---
# <a name="preprocessor"></a>Preprocesor
Preprocesor jest procesora tekstu, która manipuluje tekst pliku źródłowego w ramach pierwszej fazy tłumaczenia. Preprocesor nie analizuje tekst źródłowy, ale jej Podziel je na tokeny na potrzeby znajdowania wywołania makra. Mimo że kompilator wywołuje zazwyczaj preprocesor w jego pierwszym przebiegu, preprocesor można również wywołać oddzielnie do przetwarzania tekstu bez kompilacji.

Materiał odniesienia na preprocesora zawiera następujące sekcje:

- [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)

- [Operatory preprocesora](../preprocessor/preprocessor-operators.md)

- [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)

- [Pragma — dyrektywy](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Specyficzne dla firmy Microsoft**

Możesz uzyskać go w kodzie źródłowym po przetwarzanie wstępne za pomocą [/E](../build/reference/e-preprocess-to-stdout.md) lub [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) — opcja kompilatora. Obie opcje preprocesora wywołania i wynikowy tekst na urządzeniu standardowe dane wyjściowe, które w większości przypadków to konsola danych wyjściowych polecenia. Różnica między dwie opcje jest, że zawiera /E `#line` dyrektywy i /EP usuwa te dyrektywy się.

**KONIEC Specyficzne dla firmy Microsoft**

##  <a name="_predir_special_terminology"></a> Terminologię

W dokumentacji preprocesora termin "argument" odnosi się do jednostki, który jest przekazywany do funkcji. W niektórych przypadkach jest on zmodyfikowany przez "rzeczywiste" lub "formalnych", której opisano wyrażenie argumentu, określone w wywołaniu funkcji i deklaracji argumentów odpowiednio określone w definicji funkcji.

Termin "Zmienna" odnosi się do obiektu proste danych typu C. Termin "object" odnosi się do obiektu języka C++ i zmiennych; to termin (włącznie).

## <a name="see-also"></a>Zobacz także

[Odwołania preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Fazy tłumaczenia](../preprocessor/phases-of-translation.md)