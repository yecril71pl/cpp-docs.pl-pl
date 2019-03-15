---
title: /Od (Wyłącz (Debuguj))
ms.date: 11/04/2016
f1_keywords:
- /od
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
ms.openlocfilehash: 83ece0865eb74a4e9e292b78733df9d24602fe1d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57806769"
---
# <a name="od-disable-debug"></a>/Od (Wyłącz (Debuguj))

Wyłącza wszystkie optymalizacje w programie i przyspiesza kompilację.

## <a name="syntax"></a>Składnia

```
/Od
```

## <a name="remarks"></a>Uwagi

Ta opcja jest domyślnie. Ponieważ **/Od** pomija przepływu kodu, upraszcza proces debugowania. Aby uzyskać więcej informacji o opcjach kompilatora do debugowania, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Z7, /Zi, /ZI (Format informacji o debugowaniu)](z7-zi-zi-debug-information-format.md)
