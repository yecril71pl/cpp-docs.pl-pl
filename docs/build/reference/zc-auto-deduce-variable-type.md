---
title: '-Zc: auto (Dedukuj typ zmiennej) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: b306a104b9f71d536684e62f6dda1cac45b1d9dd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612944"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Dedukuj typ zmiennej)

**/Zc: Auto [-]** — opcja kompilatora informuje kompilator, jak używać [auto — słowo kluczowe](../../cpp/auto-keyword.md) do zadeklarowania zmiennych. W przypadku określenia opcji domyślnej **/Zc: Auto**, kompilator określi typ zmiennej zadeklarowanej z jej wyrażenia inicjowania. Jeśli określisz **/Zc:auto-**, kompilator przydziela zmienną automatyczna Klasa magazynu.

## <a name="syntax"></a>Składnia

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>Uwagi

C++ standard definiuje oryginału i poprawione znaczenie dla `auto` — słowo kluczowe. Przed Visual C++ 2010 słowo kluczowe deklaruje zmienną w klasie automatycznego przechowywania; oznacza to, że zmienna, który ma lokalne okresy istnienia. Począwszy od programu Visual C++ 2010, słowo kluczowe określi typ zmiennej z deklaracji wyrażenia inicjowania. Użyj **/Zc: Auto [-]** opcję kompilatora, aby poinformować kompilator, aby użyć oryginalnej lub poprawionego rozumieniu `auto` — słowo kluczowe. **/Zc: Auto** opcja jest domyślnie włączone. [/ Permissive-](permissive-standards-conformance.md) opcja nie powoduje zmiany domyślne ustawienie **/Zc: Auto**.

Kompilator generuje komunikat diagnostyczny odpowiednie, jeśli korzystanie z `auto` — słowo kluczowe jest sprzeczna bieżącego **/Zc: Auto** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [auto — słowo kluczowe](../../cpp/auto-keyword.md). Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **/Zc: Auto** lub **/Zc:auto-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
