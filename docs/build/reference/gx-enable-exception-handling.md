---
title: -GX (Włącz obsługę wyjątków) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095db3db73f2be4012efe39f3b8cd8e645ad46c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718338"
---
# <a name="gx-enable-exception-handling"></a>/GX (Włącz obsługę wyjątków)

Przestarzałe. Włącza synchroniczną obsługę wyjątków za pomocą przy założeniu, że funkcje zadeklarowane za pomocą `extern "C"` nigdy nie zgłasza wyjątku.

## <a name="syntax"></a>Składnia

```
/GX
```

## <a name="remarks"></a>Uwagi

**/GX** jest przestarzała. Użyj odpowiednik [/ehsc](../../build/reference/eh-exception-handling-model.md) zamiast opcji. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** sekcji [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

Domyślnie **/ehsc**, odpowiednik **/GX**, obowiązuje podczas kompilowania przy użyciu środowiska programistycznego Visual Studio. Podczas korzystania z narzędzi wiersza polecenia, brak obsługi wyjątku jest określony. Jest to równoważne z **/GX-**.

Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków języka C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **wiersza polecenia**.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)