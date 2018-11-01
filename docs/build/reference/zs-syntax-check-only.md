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
ms.openlocfilehash: 5cdd52ba6c221cbfa1526c19f3d6cfaf26a96e51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429799"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)