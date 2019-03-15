---
title: /Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)
ms.date: 1/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: f7ee51c858c9f90440cf0c2b21799ef7473cf6da
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813867"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)

**TP** opcja określa, że jej argument: Nazwa pliku jest plik źródłowy C, nawet jeśli nie ma rozszerzenia .c. **/Tp** opcja określa, że jej argument filename pliku źródłowego języka C++, nawet jeśli nie ma rozszerzenia .cpp lub .cxx. Odstęp między opcją i nazwa pliku jest opcjonalna. Każda opcja określa jeden plik; Aby określić dodatkowe pliki, powtórz opcji.

**/TC** i **/TP** są globalne warianty **TP** i **/Tp**. Określić kompilatorowi na traktowanie wszystkich plików o nazwie w wierszu polecenia, ponieważ pliki źródłowe C (**TP**) lub pliki źródłowe C++ (**/TP**), bez względu na lokalizację, w wierszu polecenia w odniesieniu do opcji. Te opcje globalne może zostać zastąpiona przez pojedynczy plik poprzez **TP** lub **/Tp**.

## <a name="syntax"></a>Składnia

> **/TC** _filename_
>  **/Tp** _filename_
> **TP** 
>  **/TP**

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Plik źródłowy C lub C++.

## <a name="remarks"></a>Uwagi

Domyślnie **CL** założono, że pliki z rozszerzeniem .c znajdują się pliki źródłowe C i pliki .cpp lub .cxx rozszerzenia są pliki źródłowe C++.

Podczas albo **TC** lub **Tc** opcja jest określona, wszystkie specyfikacji [/Zc: wchar_t (wchar_t jest typem natywnym)](zc-wchar-t-wchar-t-is-native-type.md) opcja jest ignorowana.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **kompilacji jako** właściwości. Wybierz **OK** lub **Zastosuj** Aby zastosować zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Przykłady

Ten wiersz polecenia CL Określa, że MAIN.c TEST.prg i COLLATE.prg są wszystkie pliki źródłowe C. CL nie rozpoznaje PRINT.prg.

> GŁÓWNE CL. C /TcTEST.PRG /TcCOLLATE.PRG drukowania. PRG

Ten wiersz polecenia CL Określa, że TEST1.c, TEST2.cxx, TEST3.huh i TEST4.o są kompilowane jako pliki języka C++ i TEST5.z jest kompilowany jako plik C.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
