---
title: "Wstępnie zdefiniowane reguły | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3be1c8eea7b11f60e9ce9a7cbf5ebc0c2b99b698
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-rules"></a>Wstępnie zdefiniowane zasady
Zasady wnioskowania wstępnie zdefiniowanych Użyj dostarczony NMAKE makra poleceń i opcji.  
  
|Reguła|Polecenie|Domyślny<br /><br /> Akcja|Wsadowe<br /><br /> Reguła|Nmake platformy działa na|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|. asm.exe|$(AS) $(AFLAGS) $<|ml $<|Brak|x86|  
|. asm.obj|$(AFLAGS) $(AS) /c $<|ml /c $<|Tak|x86|  
|. asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|Brak|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. asm.obj|$(AFLAGS) $(AS) /c $<|ml64 /c $<|Tak|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. c.exe|$(CC) $(CFLAGS) $<|cl $<|Brak|wszystkie|  
|. c.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|  
|. cc.exe|$(CC) $(CFLAGS) $<|cl $<|Brak|wszystkie|  
|. cc.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|  
|. cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|Brak|wszystkie|  
|. cpp.obj|$(CPPFLAGS) $(CPP) /c $<|Cl /c $<|Tak|wszystkie|  
|. cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|Brak|wszystkie|  
|. cxx.obj|$(CXXFLAGS) $(CXX) /c $<|Cl /c $<|Tak|wszystkie|  
|. rc.res|$(RC) $(RFLAGS) /r $<|RC /r $<|Brak|wszystkie|  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady wnioskowania](../build/inference-rules.md)