---
title: /FP (nazwa &period;plik pch)
description: /Fp — opcja kompilatora umożliwia określenie nazwy pliku wstępnie skompilowanego nagłówka.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460874"
---
# <a name="fp-name-periodpch-file"></a>/FP (nazwa &period;plik pch)

Zawiera nazwę ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki.

## <a name="syntax"></a>Składnia

> **/ FP**<em>nazwy ścieżki</em>

## <a name="remarks"></a>Uwagi

Użyj **/FP** z opcją [/Yc (Utwórz prekompilowany plik nagłówkowy)](yc-create-precompiled-header-file.md) lub [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](yu-use-precompiled-header-file.md) Aby określić ścieżkę i nazwę dla prekompilowanego nagłówka (PCH) plik. Domyślnie **/Yc** opcja tworzy nazwę pliku PCH, korzystając z podstawowej nazwy pliku źródłowego i *pch* rozszerzenia.

Jeśli nie określisz rozszerzenie jako część *pathname*, rozszerzenie *pch* zakłada, że. Po określeniu nazwy katalogu przy użyciu ukośnika ( **/** ) na końcu *pathname*, domyślna nazwa pliku jest vc*wersji*0.pch, gdzie  *Wersja* jest główną wersją zestawu narzędzi Visual Studio. Ten katalog musi istnieć lub zostanie wygenerowany błąd C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C /C++**  > **prekompilowanych nagłówków** stronę właściwości.

1. Modyfikowanie **prekompilowany wyjściowy plik nagłówkowy** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Przykłady

Aby utworzyć oddzielny o nazwie wersję pliku wstępnie skompilowanego nagłówka w celu kompilacji debugowania programu, można określić polecenia takie jak:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

Poniższe polecenie Określa użycie pliku wstępnie skompilowanego nagłówka o nazwie MYPCH.pch. Kompilator wstępnie kompiluje kod źródłowy w PROG.cpp do końca MYAPP.h i umieszcza ten kod w MYPCH.pch. Następnie używa zawartości MYPCH.pch i kompiluje pozostałą część PROG.cpp, aby utworzyć plik .obj. W tym przykładzie danych wyjściowych jest plik o nazwie PROG.exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
