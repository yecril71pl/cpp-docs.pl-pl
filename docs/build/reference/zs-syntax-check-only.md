---
title: /Zs (Sprawdzaj tylko składnię)
ms.date: 11/04/2016
f1_keywords:
- /zs
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
ms.openlocfilehash: e3713312b71c4cd539d40e09a3eaa821a2e5caed
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822083"
---
# <a name="zs-syntax-check-only"></a>/Zs (Sprawdzaj tylko składnię)

Informuje kompilator, aby sprawdzić składnię plików źródłowych w wierszu polecenia.

## <a name="syntax"></a>Składnia

```
/Zs
```

## <a name="remarks"></a>Uwagi

Podczas korzystania z tej opcji nie ma plików wyjściowych są tworzone i komunikaty o błędach są zapisywane do wyjścia standardowego.

**/Zs** opcja zapewnia szybki sposób, aby znaleźć i poprawić błędy składniowe, zanim kompilujesz i łączysz pliku źródłowego.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
