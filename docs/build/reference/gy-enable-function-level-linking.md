---
title: /Gy (Włączenie łączenia na poziomie funkcji)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328280"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Włączenie łączenia na poziomie funkcji)

Umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDATs).

## <a name="syntax"></a>Składnia

```
/Gy[-]
```

## <a name="remarks"></a>Uwagi

Konsolidator wymaga, aby funkcje były pakowane oddzielnie jako COMDATs do wykluczania lub zamawiania poszczególnych funkcji w pliku DLL lub exe.

Za pomocą opcji konsolidatora [/OPT (Optymalizacje)](opt-optimizations.md) można wykluczyć z pliku .exe nieodwołane funkcje pakietowe.

Za pomocą opcji konsolidatora [/ORDER (Umieść funkcje w kolejności)](order-put-functions-in-order.md) można uwzględnić spakowane funkcje w określonej kolejności w pliku exe.

Wbudowane funkcje są zawsze pakowane, jeśli są tworzone jako wywołania (co występuje, na przykład, jeśli inlining jest wyłączony lub wziąć adres funkcji). Ponadto funkcje elementów członkowskich języka C++ zdefiniowane w deklaracji klasy są automatycznie pakowane; inne funkcje nie są i wybranie tej opcji jest wymagane do skompilowania ich jako spakowane funkcje.

> [!NOTE]
> Opcja [/ZI,](z7-zi-zi-debug-information-format.md) używana do edycji i kontynuowania, automatycznie ustawia opcję **/Gy.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Generowanie kodu.**

1. Zmodyfikuj **właściwość Włącz łączenie na poziomie funkcji.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
