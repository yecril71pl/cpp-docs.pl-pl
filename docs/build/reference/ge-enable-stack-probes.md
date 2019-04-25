---
title: /Ge (Włącz sondy stosu)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: a785ec041370e0bcbb2ce8b698bfba89235a0a0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292188"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Włącz sondy stosu)

Uaktywnia sondy stosu za każde wywołanie funkcji, wymagająca magazynu dla zmiennych lokalnych.

## <a name="syntax"></a>Składnia

```
/Ge
```

## <a name="remarks"></a>Uwagi

Ten mechanizm jest przydatne, jeśli przepiszesz funkcje sondy stosu. Zaleca się, że używasz [/Gh (Włącz _penter funkcja podłączania)](gh-enable-penter-hook-function.md) zamiast ponownego zapisywania adresów sondy stosu.

[/GS (wywołania sprawdzania stosu kontroli)](gs-control-stack-checking-calls.md) ma taki sam skutek.

**/GE** jest przestarzała; począwszy od programu Visual Studio 2005, kompilator automatycznie generuje sprawdzeniem stosu. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
