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
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927628"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)

Opcja **/TC** określa, że jej argument filename jest plikiem źródłowym C, nawet jeśli nie ma rozszerzenia. C. **/TP** opcja określa, że jej argument filename jest plikiem C++ źródłowym, nawet jeśli nie ma rozszerzenia. cpp lub. cxx. Spacja między opcją a nazwą pliku jest opcjonalna. Każda opcja określa jeden plik; Aby określić dodatkowe pliki, należy powtórzyć tę opcję.

**/TC** i **/TP** są globalnymi wariantami **/TC** i **/TP**. Określają one kompilator, aby traktować wszystkie pliki nazwane w wierszu polecenia jako C pliki źródłowe ( **/TC**) lub C++ pliki źródłowe ( **/TP**), bez względu na lokalizację w wierszu polecenia w odniesieniu do opcji. Te opcje globalne można zastąpić pojedynczym plikiem za pomocą **/TC** lub **/TP**.

## <a name="syntax"></a>Składnia

> **/TC** _Nazwa pliku_ **/TP filename**/TC/TP
>  
> 
> 

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Plik C lub C++ .

## <a name="remarks"></a>Uwagi

Domyślnie **CL** zakłada, że pliki z rozszerzeniem c są plikami źródłowymi c i plików z rozszerzeniem. cpp lub rozszerzenia. cxx są C++ plikami źródłowymi.

Gdy jest określona opcja **TC** lub **TC** , jakakolwiek Specyfikacja [/Zc: Wchar_t (wchar_t jest typem natywnym)](zc-wchar-t-wchar-t-is-native-type.md) jest ignorowana.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **C/C++**  > **Advanced** .

1. Zmodyfikuj właściwość **Kompiluj jako** . Wybierz **przycisk OK** lub **Zastosuj** , aby zastosować zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Przykłady

Ten ciąg CL wskazuje, że MAIN. c, TEST. PRG, i COLLATE. PRG to wszystkie pliki źródłowe języka C. CL nie będą rozpoznawane przez program PRINT. PRG.

> CL GŁÓWNE. Drukuj/TcTEST.PRG/TcCOLLATE.PRG. PRG

Ten CL wskazuje, że TEST1. c, TEST2. cxx, TEST3. tak i TEST4. o są kompilowane jako C++ pliki, a test5. z jest kompilowany jako plik c.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
