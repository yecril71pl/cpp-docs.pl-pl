---
title: /GX (Włącz obsługę wyjątków)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245086"
---
# <a name="gx-enable-exception-handling"></a>/GX (Włącz obsługę wyjątków)

Przestarzałe. Włącza synchroniczną obsługę wyjątków przy użyciu założeń, które funkcje zadeklarowane za pomocą `extern "C"` nigdy nie generują wyjątku.

## <a name="syntax"></a>Składnia

```
/GX
```

## <a name="remarks"></a>Uwagi

**/GX** jest przestarzała. Zamiast tego użyj równoważnej opcji [/EHsc](eh-exception-handling-model.md) . Aby zapoznać się z listą przestarzałych opcji kompilatora, zobacz sekcję **przestarzałe i usunięte opcje kompilatora** w [opcjach kompilatora wymienionych według kategorii](compiler-options-listed-by-category.md).

Domyślnie **/EHsc**, odpowiednik **/GX**, jest stosowany podczas kompilowania przy użyciu środowiska deweloperskiego programu Visual Studio. W przypadku korzystania z narzędzi wiersza polecenia nie określono obsługi wyjątków. Jest to odpowiednik **/GX-** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. W okienku nawigacji wybierz **Właściwości konfiguracji**, **CC++/** , **wiersz polecenia**.

1. Wpisz opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Model obsługi wyjątku)](eh-exception-handling-model.md)
