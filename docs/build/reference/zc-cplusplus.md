---
title: /Zc:__cplusplus (Włącz zaktualizowane __cplusplus — makro)
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705796"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (Włącz zaktualizowane __cplusplus — makro)

**/Zc:__cplusplus** włącza opcję kompilatora  **\_ \_cplusplus** makro preprocesora do zgłaszania zaktualizowanej wartości dla ostatnich obsługę standardów języka C++. Domyślnie program Visual Studio zawsze zwraca wartość "199711L"  **\_ \_cplusplus** makro preprocesora.

## <a name="syntax"></a>Składnia

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Uwagi

**\_ \_Cplusplus** makro preprocesora jest najczęściej używany do obsługi raportów dla konkretnej wersji C++ standard. Ponieważ wiele istniejący kod wydaje się zależą od wartości to makro dopasowania "199711L", kompilator nie powoduje zmiany wartości makra, chyba że użytkownik jawnie uczestnictwa w za pomocą **/Zc:__cplusplus** — opcja kompilatora. **/Zc:__cplusplus** opcja jest dostępna, począwszy od programu Visual Studio 2017 wersji 15.7 i jest domyślnie wyłączone. We wcześniejszych wersjach programu Visual Studio i domyślnie lub, jeśli **/Zc:__cplusplus-** jest określony, program Visual Studio zwraca wartość "199711 L" dla  **\_ \_cplusplus** Makro preprocesora. [/ Ograniczająca-](permissive-standards-conformance.md) nie obsługuje opcji **/Zc:__cplusplus**.

Gdy **/Zc:__cplusplus** opcja jest włączona, wartość zgłaszana przez  **\_ \_cplusplus** makro jest zależna od [/std](std-specify-language-standard-version.md) przełącznika wersji ustawienie. W tej tabeli przedstawiono możliwe wartości makra:

|Przełącznik /Zc:__cplusplus|Przełącznik /STD:c++|__cplusplus — wartość|
|-|-|-|
Zc:__cplusplus|/STD:c ++ 14 (ustawienie domyślne)|201402L
Zc:__cplusplus|/STD:c ++ 17|201703L
Zc:__cplusplus|/STD:c ++ najnowsze|201704L
Zc:__cplusplus-(wyłączone)|Dowolna wartość|199711L
Nie określono|Dowolna wartość|199711L

Kompilator nie obsługuje przełączników standardów języka C ++ 98, C ++ 03 lub C ++ 11.

Precyzyjny system wykrywania zmian do zestawu narzędzi kompilatora, użyj [elemencie _MSC_VER](../../preprocessor/predefined-macros.md) wstępnie zdefiniowanego makra. Wartość to wbudowane makro jest zwiększany dla każdej aktualizacji narzędzi programu Visual Studio 2017 i nowszych wersjach. [_MSVC_LANG](../../preprocessor/predefined-macros.md) wstępnie zdefiniowanego makra raporty standardowe wersji czy **/Zc:__cplusplus** opcja jest włączona lub wyłączona. Gdy **/Zc:__cplusplus** jest włączona, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Dodaj **/Zc:__cplusplus** lub **/Zc:__cplusplus-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

- [/Zc (Zgodność)](zc-conformance.md)
- [/STD (Określanie języka standardowej wersji)](std-specify-language-standard-version.md)
- [Wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md)
