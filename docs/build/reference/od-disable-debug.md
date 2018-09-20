---
title: -Od (Wyłącz (Debuguj)) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f0fa55b7ddfc97d1073211ad23c04d724aabe50
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404283"
---
# <a name="od-disable-debug"></a>/Od (Wyłącz (Debuguj))

Wyłącza wszystkie optymalizacje w programie i przyspiesza kompilację.

## <a name="syntax"></a>Składnia

```
/Od
```

## <a name="remarks"></a>Uwagi

Ta opcja jest domyślnie. Ponieważ **/Od** pomija przepływu kodu, upraszcza proces debugowania. Aby uzyskać więcej informacji o opcjach kompilatora do debugowania, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Z7, /Zi, /ZI (Format informacji o debugowaniu)](../../build/reference/z7-zi-zi-debug-information-format.md)