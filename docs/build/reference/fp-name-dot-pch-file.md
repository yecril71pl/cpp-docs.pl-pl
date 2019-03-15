---
title: /Fp (Nazwa pliku .Pch)
ms.date: 11/04/2016
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
ms.openlocfilehash: 95506e17dff47e51cb7a3d83b629880f63422d26
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820393"
---
# <a name="fp-name-pch-file"></a>/Fp (Nazwa pliku .Pch)

Zawiera nazwę ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki.

## <a name="syntax"></a>Składnia

> **/ FP**<em>nazwy ścieżki</em>

## <a name="remarks"></a>Uwagi

Użyj tej opcji z [/Yc (Utwórz prekompilowany plik nagłówkowy)](yc-create-precompiled-header-file.md) lub [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](yu-use-precompiled-header-file.md) o podanie nazwy ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki. Można również użyć **/FP** z **/Yc** Aby określić plik prekompilowanego pliku nagłówkowego, która różni się od **/Yc**<em>filename</em> argumentów i z podstawowej nazwy pliku źródłowego.

Jeśli nie określisz rozszerzenie jako część nazwy ścieżki, przyjmowana jest rozszerzeniem .pch. Jeśli określisz katalogu bez nazwy pliku, domyślna nazwa pliku jest VC*x*0.pch, gdzie *x* jest główną wersją Visual C++ w użyciu.

Można również użyć **/FP** z opcją **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **prekompilowanych nagłówków** stronę właściwości.

1. Modyfikowanie **Prekompilowanego pliku nagłówkowego** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.

## <a name="example"></a>Przykład

Jeśli chcesz utworzyć prekompilowany plik nagłówka dla wersji debugowania programu i kompilacja kodu źródłowego i pliki nagłówkowe, należy określić polecenia takie jak:

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>Przykład

Poniższe polecenie Określa użycie pliku wstępnie skompilowanego nagłówka o nazwie MYPCH.pch. Kompilator zakłada wstępnie kodu źródłowego w PROG.cpp za pośrednictwem MYAPP.h i że wstępnie skompilowany kod znajduje się w MYPCH.pch. Używa zawartości MYPCH.pch i kompiluje pozostałą część PROG.cpp, aby utworzyć plik .obj. W tym przykładzie danych wyjściowych jest plik o nazwie PROG.exe.

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
