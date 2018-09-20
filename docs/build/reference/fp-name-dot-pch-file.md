---
title: -Fp (nazwa. Plik pch) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a851f93ae845d56b9c986e822e94970ad5cccd5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427137"
---
# <a name="fp-name-pch-file"></a>/Fp (Nazwa pliku .Pch)

Zawiera nazwę ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki.

## <a name="syntax"></a>Składnia

> **/ FP**<em>nazwy ścieżki</em>

## <a name="remarks"></a>Uwagi

Użyj tej opcji z [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) lub [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) o podanie nazwy ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki. Można również użyć **/FP** z **/Yc** Aby określić plik prekompilowanego pliku nagłówkowego, która różni się od **/Yc**<em>filename</em> argumentów i z podstawowej nazwy pliku źródłowego.

Jeśli nie określisz rozszerzenie jako część nazwy ścieżki, przyjmowana jest rozszerzeniem .pch. Jeśli określisz katalogu bez nazwy pliku, domyślna nazwa pliku jest VC*x*0.pch, gdzie *x* jest główną wersją Visual C++ w użyciu.

Można również użyć **/FP** z opcją **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

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

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)