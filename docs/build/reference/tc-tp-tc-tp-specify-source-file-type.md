---
title: "-Tc, - Tp,-TC, - TP (Określ typ pliku źródłowego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
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
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3b7508bf3ff65e27cab3260577d2831de00eb2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego)
**/TC** opcja określa, że `filename` jest plikiem źródłowym C, nawet jeśli nie ma rozszerzenia .c. **/Tp** opcja określa, że `filename` jest plik źródłowy języka C++, nawet jeśli nie ma rozszerzenia .cpp lub .cxx. Odstęp między opcji i `filename` jest opcjonalna. Każda opcja określa jeden plik; Aby określić dodatkowe pliki, powtórz opcji.  
  
 **/ TC** i **/TP** są globalne wariantów **/TC** i **/Tp**. Określa kompilatorowi na traktowanie wszystkich plików o nazwie w wierszu polecenia jako pliki źródłowe C (**/TC**) lub pliki źródłowe C++ (**/TP**), bez względu na lokalizację, w wierszu polecenia w odniesieniu do opcji. Te opcje globalne może zostać zastąpiona przez pojedynczy plik za pomocą klasy **/TC** lub **/Tp**.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik źródłowy języka C lub C++.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie CL założono, że pliki z rozszerzeniem .c są pliki źródłowe C i pliki z .cpp lub .cxx rozszerzenia są pliki źródłowe C++.  
  
 Podczas albo **TC** lub **Tc** określono opcję żadnych specyfikacji [/Zc: wchar_t (wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) opcja została zignorowana.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **skompilować jako** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie w wierszu CL Określa, że MAIN.c, TEST.prg i COLLATE.prg są wszystkie pliki źródłowe C. CL nie rozpoznaje PRINT.prg.  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 Następujące polecenie w wierszu CL Określa, czy TEST1.c, TEST2.cxx TEST3.huh i TEST4.o są kompilowane jako plików C++ i TEST5.z jest skompilowana jako plik C.  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)