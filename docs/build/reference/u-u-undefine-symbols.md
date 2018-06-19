---
title: -U, -u (Usuń definicje symboli) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 897ca229ec7312812b6f2bd2991bf519e98c836c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378330"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Usuń definicje symboli)
**/U** — opcja kompilatora definicji określony symbol preprocesora do usunięcia. **/U** — opcja kompilatora anulowanie definicji symboli specyficzne dla firmy Microsoft, które definiuje kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/U[ ]symbol  
/u  
```  
  
## <a name="arguments"></a>Argumenty  
 `symbol`  
 Symbol preprocesora nie zdefiniowany.  
  
## <a name="remarks"></a>Uwagi  
 Ani **/U** lub **/u** opcja może nie zdefiniowany symbol, który został utworzony przy użyciu **#define** dyrektywy.  
  
 **/U** opcja może nie zdefiniowany symbol, który został uprzednio zdefiniowany za pomocą **/D** opcji.  
  
 Domyślnie kompilator definiuje następujące symbole specyficzne dla firmy Microsoft.  
  
|Symbol|Funkcja|  
|------------|--------------|  
|_CHAR_UNSIGNED —|Domyślny typ char nie jest podpisany. Kiedy zdefiniowano [/J](../../build/reference/j-default-char-type-is-unsigned.md) określono opcję.|  
|_CPPRTTI —|Zdefiniowany dla kodu skompilowanego z [GR](../../build/reference/gr-enable-run-time-type-information.md) opcji.|  
|_CPPUNWIND —|Zdefiniowany dla kodu skompilowanego z [/ehsc](../../build/reference/eh-exception-handling-model.md) opcji.|  
|_DLL|Kiedy zdefiniowano [/ / MD](../../build/reference/md-mt-ld-use-run-time-library.md) określono opcję.|  
|_M_IX86 —|Domyślnie, zdefiniowanych na 600 dla x86 elementów docelowych.|  
|ELEMENCIE _MSC_VER|Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).|  
|_WIN32 —|Definicja aplikacji WIN32. Zawsze jest definiowany.|  
|_MT|Kiedy zdefiniowano [/ / MD lub/MT](../../build/reference/md-mt-ld-use-run-time-library.md) określono opcję.|  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **Usuń definicje preprocesora** lub **Usuń wszystkie definicje preprocesora** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/J (domyślny typ unsigned char)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [/GR (Włącz informacje typu Run-Time)](../../build/reference/gr-enable-run-time-type-information.md)   
 [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)   
 [/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md)