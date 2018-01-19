---
title: "/ Tc, / TP, / TC, /TP (Określ typ pliku źródłowego) | Dokumentacja firmy Microsoft"
ms.date: 1/11/2018
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
dev_langs: C++
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3d51e4c6bbf6a77f86be5cabde9b65f8e4f8c9f
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)

**/TC** opcja określa, że jej argument filename pliku źródłowego C, nawet jeśli nie ma rozszerzenia .c. **/Tp** opcja określa, że jej argument filename plik źródłowy języka C++, nawet jeśli nie ma rozszerzenia .cpp lub .cxx. Odstęp między opcją i nazwa pliku jest opcjonalna. Każda opcja określa jeden plik; Aby określić dodatkowe pliki, powtórz opcji.

**/ TC** i **/TP** są globalne wariantów **/TC** i **/Tp**. Określa kompilatorowi na traktowanie wszystkich plików o nazwie w wierszu polecenia jako pliki źródłowe C (**/TC**) lub pliki źródłowe C++ (**/TP**), bez względu na lokalizację, w wierszu polecenia w odniesieniu do opcji. Te opcje globalne może zostać zastąpiona przez pojedynczy plik za pomocą klasy **/TC** lub **/Tp**.

## <a name="syntax"></a>Składnia

> **/ TC** _filename_  
> **/TP** _filename_  
> **/TC**  
> **/TP**  

## <a name="arguments"></a>Argumenty

*Nazwa pliku*  
Plik źródłowy języka C lub C++.

## <a name="remarks"></a>Uwagi

Domyślnie **CL** założono, że pliki z rozszerzeniem .c są pliki źródłowe C i pliki z .cpp lub .cxx rozszerzenia są pliki źródłowe C++.

Podczas albo **TC** lub **Tc** określono opcję żadnych specyfikacji [/Zc: wchar_t (wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) opcja została zignorowana.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** strony właściwości.

1. Modyfikowanie **skompilować jako** właściwości. Wybierz **OK** lub **Zastosuj** Aby zastosować zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Przykłady

Ten wiersz polecenia CL Określa, że MAIN.c, TEST.prg i COLLATE.prg są wszystkie pliki źródłowe C. CL nie rozpoznaje PRINT.prg.

> CL GŁÓWNE. C /TcTEST.PRG /TcCOLLATE.PRG drukowania. PRG

Ten wiersz polecenia CL Określa, czy TEST1.c, TEST2.cxx TEST3.huh i TEST4.o są kompilowane jako plików C++ i TEST5.z jest skompilowana jako plik C.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
