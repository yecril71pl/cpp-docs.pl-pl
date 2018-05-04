---
title: -Wp64 (wykrywaj problemy związane z przenośnością 64-bitowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
dev_langs:
- C++
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 295f2f690cb3c9db17a410cea1f23d04e54b0054
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Wykrywaj problemy związane z przenośnością w programowaniu 64-bitowym)

Ta opcja kompilatora jest przestarzałe. W wersjach programu Visual Studio przed Visual Studio 2013, to wykrywa problemów związanych z przenośnością 64-bitowych na typy, które są również oznaczane [__w64](../../cpp/w64.md) — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Wp64  
```  
  
## <a name="remarks"></a>Uwagi  

Domyślnie w wersjach programu Visual Studio przed Visual Studio 2013 **/Wp64** — opcja kompilatora jest wyłączone w kompilatorze języka Visual C++, korzystająca x86 32-bitowego kodu, a na kompilatora Visual C++ który kompiluje 64-bitowy, x64 kodu.  
  
> [!IMPORTANT]
>  [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) — opcja kompilatora i [__w64](../../cpp/w64.md) — słowo kluczowe nie są używane w programie Visual Studio 2010 i Visual Studio 2012, a nie obsługiwane w programie Visual Studio 2013. Jeśli Konwertuj na projekt, który używa tego przełącznika, przełącznika nie będą migrowane podczas konwersji. Aby użyć tej opcji w programie Visual Studio 2010 lub Visual Studio 2012, należy wpisać przełącznika kompilatora pod **dodatkowe opcje** w **wiersza polecenia** sekcji właściwości projektu. Jeśli używasz **/Wp64** — opcja kompilatora w wierszu polecenia, kompilator generuje D9002 ostrzeżenie wiersza polecenia. Zamiast za pomocą tej opcji i słowo kluczowe wykrywać problemy związane z przenośnością 64-bitowych, należy użyć kompilatora Visual C++, przeznaczonego dla platformy 64-bitowej i określić [/W4](../../build/reference/compiler-option-warning-level.md) opcji. Aby uzyskać więcej informacji, zobacz [skonfigurować Visual C++ dla 64-bitowy, x64 cele](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
Tak, jakby były one używane w 64-bitowym systemie operacyjnym, w 32-bitowym systemie operacyjnym sprawdzane są zmienne następujących typów:  
  
-   int  
  
-   long  
  
-   pointer  
  
 Jeśli regularnie kompilowania aplikacji za pomocą kompilatora, która tworzy 64-bitowy, x64 kodu, możesz po prostu wyłączyć **/Wp64** w kompilacjach kodu z 32-bitowych ponieważ kompilator 64-bitowy wykrywa wszystkie problemy. Aby uzyskać więcej informacji na temat docelowego Windows 64-bitowego systemu operacyjnego, zobacz [skonfigurować Visual C++ dla 64-bitowy, x64 cele](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe.  
  
     Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** pole, aby uwzględnić **/Wp64**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.  
  
## <a name="see-also"></a>Zobacz też  

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../../build/configuring-programs-for-64-bit-visual-cpp.md)