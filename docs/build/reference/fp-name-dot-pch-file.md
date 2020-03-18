---
title: /FP (Nazwij plik PCH &period;)
description: Użyj opcji kompilatora/FP, aby określić nazwę prekompilowanego pliku nagłówkowego.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439786"
---
# <a name="fp-name-periodpch-file"></a>/FP (Nazwij plik PCH &period;)

Zawiera nazwę ścieżki prekompilowanego nagłówka zamiast używania domyślnej nazwy ścieżki.

## <a name="syntax"></a>Składnia

> **/Fp**<em>Nazwa ścieżki</em> /FP

## <a name="remarks"></a>Uwagi

Użyj opcji **/FP** z [/YC (Utwórz prekompilowany plik nagłówkowy)](yc-create-precompiled-header-file.md) lub [/Yu (Użyj prekompilowanego pliku nagłówkowego)](yu-use-precompiled-header-file.md) , aby określić ścieżkę i nazwę pliku dla prekompilowanego pliku nagłówkowego (pch). Domyślnie opcja **/YC** tworzy nazwę pliku PCH przy użyciu podstawowej nazwy pliku źródłowego i rozszerzenia *PCH* .

Jeśli nie określisz rozszerzenia jako części *nazwy ścieżki*, przyjmuje się rozszerzenie *PCH* . W przypadku określenia nazwy katalogu przy użyciu ukośnika ( **/** ) na końcu nazwy *ścieżki*domyślna nazwa pliku to VC w*wersji*0. PCH, gdzie *wersja* jest wersją główną zestawu narzędzi programu Visual Studio. Ten katalog musi istnieć lub został wygenerowany błąd C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę **Właściwości** > **C/C++**  > **prekompilowanych nagłówków** .

1. Zmodyfikuj właściwość **pliku wyjściowego prekompilowanego nagłówka** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Przykłady

Aby utworzyć oddzielną, nazwaną wersję prekompilowanego pliku nagłówkowego dla kompilacji debugowania programu, można określić polecenie, takie jak:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

Następujące polecenie Określa użycie prekompilowanego pliku nagłówkowego o nazwie MYPCH. PCH. Kompilator kompiluje kod źródłowy w programie MÓJ_PROG. cpp na końcu MOJAAPL. h i umieszcza wstępnie skompilowany kod w MYPCH. PCH. Następnie używa zawartości MYPCH. pch i kompiluje resztę programu MÓJ_PROG. cpp, aby utworzyć plik. obj. Danymi wyjściowymi tego przykładu jest plik o nazwie programu MÓJ_PROG. exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
