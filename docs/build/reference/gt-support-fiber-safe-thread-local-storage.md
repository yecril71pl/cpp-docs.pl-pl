---
title: "GT — (Obsługa włókien magazynu wątków lokalnych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs: C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86c027a1796f42d7b2932f68aff00136ee0d217f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Obsługa bezpieczeństwa włókien magazynu wątków lokalnych)
Obsługuje bezpieczeństwa włókien danych przydzielony przy użyciu statycznego magazynu wątków lokalnych, czyli danych przydzielone z `__declspec(thread)`.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GT  
```  
  
## <a name="remarks"></a>Uwagi  
 Dane zadeklarowana z `__declspec(thread)` odwołuje się do tablicy lokalny magazyn wątków (TLS). Tablica TLS jest tablicę adresów, która jest obsługiwana przez system dla każdego wątku. Każdy adres w tej macierzy daje lokalizację magazynu wątków lokalnych danych.  
  
 Fiber jest lekki obiekt, który składa się z stosu i kontekst rejestru i mogą być planowane w różnych wątkach. Włókna mogą działać na którymkolwiek wątku. Ponieważ włókna mogą uzyskać wymieniane i ponownie uruchomione później w innym wątku, adres tablicy TLS nie musi być buforowane lub optymalizowane jako wspólne wyrażenia podrzędnego w wywołaniu funkcji (zobacz [/Og (optymalizacje globalne)](../../build/reference/og-global-optimizations.md) opcja dla szczegółowe informacje). **/GT** uniemożliwia takie optymalizacji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **optymalizacji** strony właściwości.  
  
4.  Modyfikowanie **Włącz optymalizacje bezpieczne dla włókna** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)