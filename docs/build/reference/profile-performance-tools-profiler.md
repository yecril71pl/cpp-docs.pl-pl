---
title: "-PROFILE (Profiler narzędzi wydajności) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54aff4c81b0bff9fcd6727333ee7d17c76564c71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profiler narzędzi do oceny wydajności)
Tworzy plik wyjściowy, który może być używany z profilerem narzędzi wydajności.  
  
## <a name="syntax"></a>Składnia  
  
```  
/PROFILE  
```  
  
## <a name="remarks"></a>Uwagi  
 PROFIL wymaga następujących opcji konsolidatora:  
  
-   [/ OPT: REF](../../build/reference/opt-optimizations.md)  
  
-   / OPT: NOICF  
  
-   [/ INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [/ FIXED: NO](../../build/reference/fixed-fixed-base-address.md)  
  
 Profil powoduje, że konsolidator, aby wygenerować sekcji relokacji w obrazie programu.  Sekcja relokacji umożliwia profiler do przekształcania obraz programu do pobierania danych profilu.  
  
 **/ PROFILE** tylko jest dostępna tylko w wersjach Enterprise (Programowanie zespołowe).  Aby uzyskać więcej informacji o PREfast, zobacz [analizy kodu dla C/C++ — omówienie](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **profilu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)