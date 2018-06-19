---
title: Wstępnie zdefiniowane reguły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a21847bb9363099fa64825b45a90003de053da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369763"
---
# <a name="predefined-rules"></a>Wstępnie zdefiniowane zasady
Zasady wnioskowania wstępnie zdefiniowanych Użyj dostarczony NMAKE makra poleceń i opcji.  
  
|Reguła|Polecenie|Domyślny<br /><br /> Akcja|Wsadowe<br /><br /> Reguła|Nmake platformy działa na|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Brak|x86|  
|. asm.obj|$(AFLAGS) $(AS) /c $<|ml /c $<|Tak|x86|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Brak|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. asm.obj|$(AFLAGS) $(AS) /c $<|ml64 /c $<|Tak|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Brak|wszystkie|  
|. c.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|  
|. cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Brak|wszystkie|  
|. cc.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|  
|. cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|Brak|wszystkie|  
|. cpp.obj|$(CPPFLAGS) $(CPP) /c $<|Cl /c $<|Tak|wszystkie|  
|. cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|Brak|wszystkie|  
|. cxx.obj|$(CXXFLAGS) $(CXX) /c $<|Cl /c $<|Tak|wszystkie|  
|. rc.res|$(RC) $(RFLAGS) /r $<|RC /r $<|Brak|wszystkie|  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady wnioskowania](../build/inference-rules.md)