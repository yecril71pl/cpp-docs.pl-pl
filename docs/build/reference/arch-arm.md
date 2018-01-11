---
title: -arch (ARM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 468401bcee2d627149175d022c420b8bb905c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="arch-arm"></a>/arch (ARM)
Określa generowanie kodu na ARM architektury. Zobacz też [/arch (x86)](../../build/reference/arch-x86.md) i [/arch (x64)](../../build/reference/arch-x64.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>Argumenty  
 **/arch:ARMv7VE**  
 Umożliwia użycie instrukcji ARMv7VE wirtualizacji rozszerzenia.  
  
 **/arch:VFPv4**  
 Umożliwia użycie instrukcji ARM VFPv4. Jeśli ta opcja nie jest określona, VFPv3 jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `_M_ARM_FP` Makro (tylko ARM) wskazuje, które, jeśli taki występuje, **/arch** użyto — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).  
  
 Jeśli używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) skompilować, **/arch** nie ma wpływu na generowanie kodu dla zarządzanego funkcji. **/ arch** tylko wpływa na generowanie kodu dla funkcji macierzystego.  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /arch:ARMv7VE lub /arch:VFPv4 w programie Visual Studio  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  W **dodatkowe opcje** Dodaj `/arch:ARMv7VE` lub `/arch:VFPv4`.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/ arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)