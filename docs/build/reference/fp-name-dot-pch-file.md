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
ms.openlocfilehash: 80f59477695b83b33dd3cfa2b37837c5b52c8002
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fp-name-pch-file"></a>/Fp (Nazwa pliku .Pch)
Zawiera nazwę ścieżki dla prekompilowanego nagłówka, zamiast domyślna nazwa ścieżki.  
  
## <a name="syntax"></a>Składnia  
  
> **/ FP**_nazwy ścieżki_  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji z [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) lub [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) o podanie nazwy ścieżki dla prekompilowanego nagłówka, zamiast domyślna nazwa ścieżki. Można również użyć **/FP** z **/Yc** Aby określić korzystanie z pliku prekompilowanego nagłówka, która różni się od **/Yc *** filename* argumentu i z podstawowej nazwy pliku źródłowego.  
  
 Jeśli nie określisz rozszerzenia jako część nazwy ścieżki, przyjmowana jest rozszerzeniem .pch. Jeśli określisz katalogu bez nazwy pliku, domyślna nazwa pliku jest VC*x*0.pch, gdzie *x* jest wersję główną programu Visual C++ w użyciu.  
  
 Można również użyć **/FP** opcję z **/Yu**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **prekompilowanych nagłówków** strony właściwości.  
  
4.  Modyfikowanie **Prekompilowanego pliku nagłówka** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz utworzyć prekompilowanego pliku nagłówkowego dla debugowania wersji programu i kompilacja zarówno kod źródłowy, jak i pliki nagłówkowe, możesz określić polecenia takie jak:  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## <a name="example"></a>Przykład  
 Polecenie Określa użycie prekompilowanego nagłówka pliku o nazwie MYPCH.pch. Kompilator przyjęto założenie, że kod źródłowy w PROG.cpp została prekompilowanego poprzez MYAPP.h i że prekompilowany kod znajduje się w MYPCH.pch. Wykorzystuje zawartość MYPCH.pch, a następnie kompiluje reszty PROG.cpp, aby utworzyć plik .obj. Dane wyjściowe w tym przykładzie jest to plik o nazwie PROG.exe.  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)