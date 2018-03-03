---
title: -c (Kompiluj bez konsolidacji) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 112e063af9c56ead8ae7e8f59fe88853ff55f7b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-compile-without-linking"></a>/c (Kompiluj bez konsolidacji)
Uniemożliwia automatyczne wywołaniu łącza.  
  
## <a name="syntax"></a>Składnia  
  
```  
/c  
```  
  
## <a name="remarks"></a>Uwagi  
 Kompilowanie przy użyciu **/c** tworzy tylko pliki .obj. ŁĄCZE musi jawnie wywołana z opcjami do wykonywania połączeń fazy kompilacji i właściwe pliki.  
  
 Używa żadnego projektu wewnętrznej utworzone w środowisku programistycznym **/c** opcji domyślnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
-   Ta opcja nie jest dostępne w środowisku programistycznym.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Aby ustawić tę opcję kompilatora programowo, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu tworzy pliki obiektów FIRST.obj i SECOND.obj. THIRD.obj jest ignorowana.  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 Aby utworzyć plik wykonywalny, należy wywołać łącza:  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)