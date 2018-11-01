---
title: Użyciem (Włącz makra __cplusplus zaktualizowane)
ms.date: 05/30/2018
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 8e73d93ae0618a04bdcc8476fadb6cc2aab595b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623993"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>Użyciem (Włącz makra __cplusplus zaktualizowane)

**Użyciem** włącza opcję kompilatora  **\_ \_cplusplus** makro preprocesora Aby zgłosić zaktualizowaną wartość dla ostatnich Obsługa standardów języka C++. Domyślnie program Visual Studio zawsze zwraca wartość "199711L"  **\_ \_cplusplus** makro preprocesora.

## <a name="syntax"></a>Składnia

> **Użyciem**[**-**]

## <a name="remarks"></a>Uwagi

**\_ \_Cplusplus** makro preprocesora jest najczęściej używany do obsługi raport dla konkretnej wersji C++ standard. Ponieważ wiele istniejący kod wydaje się zależą od wartości tego makra dopasowania "199711L", kompilator nie zmienia wartość makra, chyba że jawnie zgody przez klienta na przy użyciu **użyciem** — opcja kompilatora. **Użyciem** opcja jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.7 i jest domyślnie wyłączona. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc:__cplusplus-** jest określony, program Visual Studio zwraca wartość "199711 L" dla  **\_ \_cplusplus** Makro preprocesora. [/ Permissive-](permissive-standards-conformance.md) opcji nie włącza **użyciem**.

Gdy **użyciem** opcja jest włączona, wartość zgłoszone przez  **\_ \_cplusplus** — makro jest zależna od [/STD](std-specify-language-standard-version.md) przełącznika wersji ustawienie. W poniższej tabeli przedstawiono możliwe wartości dla makra:

|Użyciem przełącznika|Przełącznik /STD:c++|__cplusplus wartość|
|-|-|-|
Zc:__cplusplus|/ STD: c ++ 14 (domyślnie)|201402L
Zc:__cplusplus|/ STD: c ++ 17|201703L
Zc:__cplusplus|/ STD: c ++ najnowsze|201704L
Zc:__cplusplus-(wyłączony)|Dowolna wartość|199711L
Nie określono|Dowolna wartość|199711L

Kompilator nie obsługuje przełączników standardów C ++ 98, C ++ 03 lub C ++ 11.

Bardziej szczegółowej wykrycia zmiany zestawu narzędzi kompilatora, można użyć [_MSC_VER](../../preprocessor/predefined-macros.md) wstępnie zdefiniowane makro. Wartość tego makra wbudowane są zwiększane dla każdej aktualizacji zestawu narzędzi w programie Visual Studio 2017 i nowszych wersjach. [_MSVC_LANG](../../preprocessor/predefined-macros.md) czy raporty wstępnie zdefiniowane makro standardowej wersji **użyciem** opcja jest włączona lub wyłączona. Gdy **użyciem** jest włączona, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **użyciem** lub **/Zc:__cplusplus-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

- [/Zc (Zgodność)](zc-conformance.md)
- [/ STD (Określ wersję standardu języka)](std-specify-language-standard-version.md)
- [Wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md)
