---
title: -arch (x86) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4905634af75f30c5428f8091d736adbe1b8490d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="arch-x86"></a>/arch (x86)
Określa generowanie kodu na x86 architektury. Zobacz też [/arch (x64)](../../build/reference/arch-x64.md) i [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## <a name="arguments"></a>Argumenty  
 **/arch:IA32**  
 Określa nie ulepszonych instrukcji i określa również x87 do obliczeń zmiennoprzecinkowych.  
  
 **/arch:SSE**  
 Włącza używanie instrukcji SSE.  
  
 **SSE2**  
 Włącza używanie instrukcji SSE2. To domyślne instrukcji na x86 platformy, jeśli nie **/arch** określono opcję.  
  
 **/ arch: avx**  
 Włącza używanie instrukcji Intel Advanced Vector Extensions.  
  
 **/arch:AVX2**  
 Włącza używanie instrukcji Intel zaawansowany wektor rozszerzeń 2.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcje SSE i SSE2 istnieje na różnych procesorów Intel i AMD. Na procesory Intel Sandy mostek i procesorów AMD Bulldozer istnieje instrukcji AVX. Instrukcji AVX2 są obsługiwane przez Intel Haswell i Broadwell procesorów oraz procesorów AMD Koparka na podstawie.  
  
 `_M_IX86_FP`, `__AVX__` i `__AVX2__` makra określają, ile, **/arch** użyto — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** opcji i `__AVX2__` makro wprowadzono w programie Visual Studio 2013 Update 2, wersja 12.0.34567.1.  
  
 Optymalizator wybierze, kiedy i jak należy skorzystać z instrukcji SSE i SSE2 podczas **/arch** jest określona. Używa SSE i SSE2 instrukcje dotyczące niektórych skalarne obliczenia liczb zmiennoprzecinkowych, gdy ustali, że szybciej jest używać instrukcji SSE/SSE2 i rejestruje zamiast x87 liczb zmiennoprzecinkowych Zarejestruj stosu. W związku z tym kodzie faktycznie można użyć zarówno x87 i SSE/SSE2 dla obliczeń zmiennoprzecinkowych. Ponadto z **SSE2**, SSE2 instrukcje mogą służyć do niektórych operacji 64-bitową liczbę całkowitą.  
  
 Oprócz przy użyciu instrukcji SSE i SSE2, kompilator używa także inne instrukcje, które znajdują się na poprawki procesora, które obsługują SSE i SSE2. Przykładem jest instrukcji CMOV najpierw pojawił się o zmianie procesory Intel Pentium Pro.  
  
 Ponieważ x86 kompilator generuje kod tego używa instrukcji SSE2 domyślnie, należy określić **/arch:IA32** wyłączyć Generowanie instrukcji SSE i SSE2 x86 procesorów.  
  
 **/ arch** tylko wpływa na generowanie kodu dla funkcji macierzystego. Jeśli używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) skompilować, **/arch** nie ma wpływu na generowanie kodu dla zarządzanego funkcji.  
  
 **/ arch** i [/QIfist](../../build/reference/qifist-suppress-ftol.md) nie można użyć w tym samym compiland. W szczególności, jeśli nie używasz `_controlfp` do modyfikowania słowa formantu FP, a następnie uruchomienia środowiska wykonawczego zestawy x87 FPU kontroli word precyzyjną kontrolę pole kodu dla usługi bits 53. W związku z tym co float i podwójne operacji w wyrażeniu używają mantysy 53-bitowe i wykładnik 15-bitowych. Każda operacja pojedynczej precyzji SSE używa mantysy 24-bitowego i wykładnik 8-bitową i SSE2 podwójnej precyzji operacji użyj mantysy 53-bitowe i wykładnik 11-bitowych. Aby uzyskać więcej informacji, zobacz [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Te różnice są możliwe w jedno wyrażenie drzewa, ale nie w przypadkach, w których uczestniczy po każdym Podwyrażenie przypisanie użytkownika. Rozważ następujące opcje:  
  
```cpp  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 Porównaj:  
  
```cpp  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Aby ustawić tę opcję kompilatora, AVX AVX2, IA32, SSE i SSE2 w programie Visual Studio  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++** folderu.  
  
3.  Wybierz **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **Włącz rozszerzony rozkazów** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/ arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)