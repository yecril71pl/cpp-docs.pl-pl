---
title: /Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)
ms.date: 01/11/2018
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
ms.openlocfilehash: fa35249983284261252c8ada65e79ed1cb6ec79a
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825395"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)

Opcja **/TC** określa, że jej argument filename jest plikiem źródłowym C, nawet jeśli nie ma rozszerzenia. C. **/TP** opcja określa, że jej argument filename jest plikiem źródłowym języka C++, nawet jeśli nie ma rozszerzenia. cpp lub. cxx. Spacja między opcją a nazwą pliku jest opcjonalna. Każda opcja określa jeden plik; Aby określić dodatkowe pliki, należy powtórzyć tę opcję.

**/TC** i **/TP** są globalnymi wariantami **/TC** i **/TP**. Określają one kompilator, aby traktować wszystkie pliki nazwane w wierszu polecenia jako C pliki źródłowe (**/TC**) lub pliki źródłowe C++ (**/TP**) bez względu na lokalizację w wierszu polecenia w odniesieniu do opcji. Te opcje globalne można zastąpić pojedynczym plikiem za pomocą **/TC** lub **/TP**.

## <a name="syntax"></a>Składnia

> **/Tc** _Nazwa pliku_ /TC\
> **/TP** _filename_\
> **/TC**\
> **/TP**

### <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Plik źródłowy C lub C++.

## <a name="remarks"></a>Uwagi

Domyślnie **CL** założono, że pliki z rozszerzeniem c są plikami źródłowymi c i plikami z rozszerzeniem CPP lub. cxx są plikami źródłowymi języka C++.

Gdy jest określona opcja **TC** lub **TC** , każda Specyfikacja [/Zc: Wchar_t (wchar_t jest typem natywnym)](zc-wchar-t-wchar-t-is-native-type.md) jest ignorowana.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **zaawansowana** **C/C++** > .

1. Zmodyfikuj właściwość **Kompiluj jako** . Wybierz **przycisk OK** lub **Zastosuj** , aby zastosować zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Przykłady

Ten ciąg CL wskazuje, że MAIN. c, TEST. PRG, i COLLATE. PRG to wszystkie pliki źródłowe języka C. CL nie będą rozpoznawane przez program PRINT. PRG.

> CL GŁÓWNE. Drukuj/TcTEST.PRG/TcCOLLATE.PRG. PRG

Ten wiersz polecenia CL Określa, że TEST1. c, TEST2. cxx, TEST3. tak i TEST4. o są kompilowane jako pliki języka C++, a TEST5. z jest kompilowany jako plik C.

> CL TEST1. C TEST2. CXX TEST3. TAK TEST4. O/TC TEST5. Z/TP

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
