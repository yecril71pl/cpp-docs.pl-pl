---
title: -arch (x64) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 848d229d6cf8df7d08494d0c300e082c6dc7d0a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="arch-x64"></a>/arch (x64)
Określa generowanie kodu na x64 architektury. Zobacz też [/arch (x86)](../../build/reference/arch-x86.md) i [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
/arch:[AVX|AVX2]  
```  
  
## <a name="arguments"></a>Argumenty  
 **/ arch: avx**  
 Włącza używanie instrukcji Intel Advanced Vector Extensions.  
  
 **/arch:AVX2**  
 Włącza używanie instrukcji Intel zaawansowany wektor rozszerzeń 2.  
  
## <a name="remarks"></a>Uwagi  
 **/ arch** tylko wpływa na generowanie kodu dla funkcji macierzystego. Jeśli używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) skompilować, **/arch** nie ma wpływu na generowanie kodu dla zarządzanego funkcji.  
  
 `__AVX__` Zdefiniowano symbol preprocesora po **/arch: avx** określono opcję kompilatora. `__AVX2__` Zdefiniowano symbol preprocesora po **/arch:AVX2** określono opcję kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** opcja została wprowadzona w programie Visual Studio 2013 Update 2, wersja 12.0.34567.1.  
  
### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/arch: avx lub /arch:AVX2 w programie Visual Studio  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++** folderu.  
  
3.  Wybierz **generowania kodu** strony właściwości.  
  
4.  W **Włącz rozszerzony rozkazów** listy rozwijanej wybierz pozycję **Advanced Vector Extensions (/ arch: AVX)** lub **zaawansowany wektor rozszerzeń 2 (/ arch: AVX2)**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/ arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)