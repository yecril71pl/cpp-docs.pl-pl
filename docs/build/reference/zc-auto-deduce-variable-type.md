---
title: '-Zc: auto (Dedukuj typ zmiennej) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 662095cdc1555891a543920a64cb7b31074914aa
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Dedukuj typ zmiennej)

**/Zc: Auto [-]** — opcja kompilatora informuje kompilator, jak używać [auto — słowo kluczowe](../../cpp/auto-keyword.md) do deklarowania zmiennych. Po określeniu opcji domyślnej **/Zc: Auto**, kompilator deduces typ zadeklarowanej zmiennej w jej wyrażeniu inicjowania. Jeśli określisz **/Zc:auto-**, kompilator przydziela zmienną automatyczna Klasa magazynu.

## <a name="syntax"></a>Składnia

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>Uwagi

C++ standard definiuje oryginał i poprawione znaczenie dla `auto` — słowo kluczowe. Przed [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], słowo kluczowe deklaruje zmienną w automatyczna Klasa magazynu; oznacza to, że zmienna mający lokalnego okres istnienia. Począwszy od [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], słowo kluczowe deduces typu zmienną z wyrażenia inicjowania deklaracji. Użyj **/Zc: Auto [-]** — opcja kompilatora do Poinformuj kompilator, aby używał znaczenie pierwotny lub skorygowany `auto` — słowo kluczowe. **/Zc: Auto** opcja jest domyślnie włączona. [/ Ograniczająca-](permissive-standards-conformance.md) opcji nie zmienia domyślne ustawienie **/Zc: Auto**.

Kompilator generuje odpowiedni komunikat diagnostycznych, jeśli korzystanie z `auto` — słowo kluczowe jest sprzeczna z bieżącej **/Zc: Auto** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [auto — słowo kluczowe](../../cpp/auto-keyword.md). Aby uzyskać więcej informacji na temat problemów zgodności z programem Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Dodaj **/Zc: Auto** lub **/Zc:auto-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
