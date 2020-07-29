---
title: /volatile (interpretacja słowa kluczowego volatile)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 7c2c1cd477b424f56e66bd9246e7bde76ad06120
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223788"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretacja słowa kluczowego volatile)

Określa sposób interpretowania [nietrwałego](../../cpp/volatile-cpp.md) słowa kluczowego.

## <a name="syntax"></a>Składnia

> **/volatile:**{**ISO** | **MS**}

## <a name="arguments"></a>Argumenty

**/volatile: ISO**<br/>
Wybiera ścisłą **`volatile`** semantykę zgodnie z definicją w standardowym języku ISO języka C++. Semantyka pozyskiwania/wydawania nie jest gwarantowana w przypadku dostępu nietrwałych. Jeśli kompilator jest ukierunkowany na ARM, jest to domyślna interpretacja **`volatile`** .

**/volatile: MS**<br/>
Wybiera semantykę rozszerzoną firmy Microsoft **`volatile`** , która dodaje gwarancje porządkowania pamięci poza językiem C++ standard ISO. Semantyka pozyskiwania/wydawania jest gwarantowana na dostępach nietrwałych. Jednak ta opcja wymusza również, aby kompilator generował bariery pamięci sprzętowej, co może zwiększyć duże obciążenie ARM i inne słabe architektury zamawiania pamięci. Jeśli kompilator jest przeznaczony dla dowolnej platformy z wyjątkiem ARM, jest to domyślna interpretacja **`volatile`** .

## <a name="remarks"></a>Uwagi

Zdecydowanie zalecamy, aby używać **/volatile: ISO** wraz z jawnymi typami pierwotnych synchronizacji i środowiskami wewnętrznymi kompilatora podczas pracy z pamięcią udostępnioną przez wątki. Aby uzyskać więcej informacji, zobacz [nietrwały](../../cpp/volatile-cpp.md).

Jeśli planujesz istniejący kod lub zmienisz tę opcję w środku projektu, pomocne może być włączenie ostrzeżenia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) w celu zidentyfikowania lokalizacji kodu, na które mają wpływ różnice w semantyce.

Nie ma żadnego `#pragma` równoważnej kontroli tej opcji.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/volatile w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. W polu **dodatkowe opcje** Dodaj **/volatile: ISO** lub **/volatile: MS** , a następnie wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[volatile](../../cpp/volatile-cpp.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
