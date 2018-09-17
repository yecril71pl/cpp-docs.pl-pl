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
ms.openlocfilehash: 5a34d3d0a601b2e160f988e0fed34a630612d839
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719254"
---
# <a name="predefined-rules"></a>Wstępnie zdefiniowane zasady

Zasady wnioskowania wstępnie zdefiniowanych Użyj dostarczonej w NMAKE makra poleceń i opcji.

|Reguła|Polecenie|Domyślny<br /><br /> Akcja|Usługi Batch<br /><br /> Reguła|Platforma nmake działa na|
|----------|-------------|------------------------|--------------------|----------------------------|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|uczenie maszynowe $<|Brak|x86|
|. asm.obj|$(AFLAGS) $(AS) /c $<|uczenie maszynowe/c $<|Tak|x86|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Brak|X64|
|. asm.obj|$(AFLAGS) $(AS) /c $<|ml64 /c $<|Tak|X64|
|. c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Brak|wszystkie|
|. c.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|
|. cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Brak|wszystkie|
|. cc.obj|$(CFLAGS) $(CC) /c $<|Cl /c $<|Tak|wszystkie|
|. cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|Brak|wszystkie|
|. cpp.obj|$(CPPFLAGS) $(CPP) /c $<|Cl /c $<|Tak|wszystkie|
|. cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|Brak|wszystkie|
|. cxx.obj|$(CXXFLAGS) $(CXX) /c $<|Cl /c $<|Tak|wszystkie|
|. rc.res|$(RC) $(RFLAGS)/r $<|RC /r $<|Brak|wszystkie|

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)