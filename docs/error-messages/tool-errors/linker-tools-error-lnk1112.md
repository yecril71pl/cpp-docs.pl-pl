---
title: "Błąd narzędzi konsolidatora LNK1112 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1112
dev_langs: C++
helpviewer_keywords: LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a915768f0668a4ce276962f9eafd1f905980e2be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1112"></a>Błąd narzędzi konsolidatora LNK1112
Moduł maszyny typu "type1" jest w konflikcie z typem maszyny docelowej "type2".  
  
 Pliki obiektów określony jako dane wejściowe zostały skompilowane dla typów na innym komputerze.  
  
 Na przykład, jeśli użytkownik próbuje połączyć skompilowany plik obiektu z **/CLR** i pliku obiektu skompilowane przy użyciu **/CLR: pure** (komputera typu CEE), konsolidator wygeneruje błąd LNK1112.  
  
 Podobnie jeśli tworzysz jeden moduł z [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatora i inny moduł z x86 kompilatora, a następnie spróbuj połączyć je, konsolidator wygeneruje LNK1112.  
  
 Możliwa przyczyna tego błędu jest Jeśli opracowujesz 64-bitowej aplikacji, ale nie jest zainstalowany jeden z kompilatorów Visual C++ 64-bitowych. W takim przypadku 64-bitowych konfiguracjach nie będą dostępne. Aby rozwiązać ten problem, uruchom Instalatora programu Visual Studio i zainstaluj brakujące składniki C++.  
  
 Ten błąd może również wystąpić, jeśli zmienisz **aktywnej konfiguracji rozwiązania** w **programu Configuration Manager** , a następnie spróbuj skompilować projektu przed usunięciem plików pośrednich projektu. Aby rozwiązać ten problem, wybierz **Kompiluj ponownie rozwiązanie** z **kompilacji** menu. Możesz też wybrać **czystą rozwiązania** z **kompilacji** menu, a następnie kompilacji rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)