---
title: /Zc:auto (Dedukuj typ zmiennej)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 9609bc484310fbc9999182add384eb4e438378bf
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446244"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Dedukuj typ zmiennej)

**/Zc: Auto [-]** — opcja kompilatora informuje kompilator, jak używać [auto — słowo kluczowe](../../cpp/auto-keyword.md) do zadeklarowania zmiennych. W przypadku określenia opcji domyślnej **/Zc: Auto**, kompilator określi typ zmiennej zadeklarowanej z jej wyrażenia inicjowania. Jeśli określisz **/Zc:auto-**, kompilator przydziela zmienną automatyczna Klasa magazynu.

## <a name="syntax"></a>Składnia

> **/Zc:auto**[**-**]

## <a name="remarks"></a>Uwagi

C++ standard definiuje oryginału i poprawione znaczenie dla `auto` — słowo kluczowe. Przed Visual Studio 2010 słowo kluczowe deklaruje zmienną w klasie automatycznego przechowywania; oznacza to, że zmienna, który ma lokalne okresy istnienia. Począwszy od programu Visual Studio 2010, słowo kluczowe określi typ zmiennej z deklaracji wyrażenia inicjowania. Użyj **/Zc: Auto [-]** opcję kompilatora, aby poinformować kompilator, aby użyć oryginalnej lub poprawionego rozumieniu `auto` — słowo kluczowe. **/Zc: Auto** opcja jest domyślnie włączone. [/ Permissive-](permissive-standards-conformance.md) opcja nie powoduje zmiany domyślne ustawienie **/Zc: Auto**.

Kompilator generuje komunikat diagnostyczny odpowiednie, jeśli korzystanie z `auto` — słowo kluczowe jest sprzeczna bieżącego **/Zc: Auto** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [auto — słowo kluczowe](../../cpp/auto-keyword.md). Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **/Zc: Auto** lub **/Zc:auto-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
