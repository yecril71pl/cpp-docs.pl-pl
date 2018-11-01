---
title: Wstępnie zdefiniowane zasady
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: b4b8ca7b0126ca42b2144aa094e7f766f6344b2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609694"
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