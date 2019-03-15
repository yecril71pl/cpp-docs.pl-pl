---
title: Wstępnie zdefiniowane zasady
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823802"
---
# <a name="predefined-rules"></a>Wstępnie zdefiniowane zasady

Zasady wnioskowania wstępnie zdefiniowanych Użyj dostarczonej w NMAKE makra poleceń i opcji.

|Reguła|Polecenie|Domyślny<br /><br /> Akcja|Batch<br /><br /> Reguła|Platforma nmake działa na|
|----------|-------------|------------------------|--------------------|----------------------------|
|. asm.exe|$(AS) $(AFLAGS) $<|ml $<|Brak|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|uczenie maszynowe/c $<|tak|x86|
|. asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|Brak|X64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|tak|X64|
|.c.exe|$(CC) $(CFLAGS) $<|cl $<|Brak|wszystkie|
|.c.obj|$(CC) $(CFLAGS) /c $<|Cl /c $<|tak|wszystkie|
|.cc.exe|$(CC) $(CFLAGS) $<|cl $<|Brak|wszystkie|
|. cc.obj|$(CC) $(CFLAGS) /c $<|Cl /c $<|tak|wszystkie|
|.cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|Brak|wszystkie|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|Cl /c $<|tak|wszystkie|
|.cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|Brak|wszystkie|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|Cl /c $<|tak|wszystkie|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|Brak|wszystkie|

## <a name="see-also"></a>Zobacz także

[Zasady wnioskowania](inference-rules.md)
