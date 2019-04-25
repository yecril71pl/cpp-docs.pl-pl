---
title: Przykładowy plik pliku reguł programu Make
ms.date: 11/04/2016
ms.assetid: 8343ce71-5556-4ae0-8d1e-7efd82673070
ms.openlocfilehash: 79ca4e466d37880787260be5b8b4ec76a5bb092f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318826"
---
# <a name="sample-makefile"></a>Przykładowy plik pliku reguł programu Make

Ten temat zawiera przykładowy plik reguł programu make.

## <a name="sample"></a>Przykład

### <a name="code"></a>Kod

```
# Sample makefile

!include <win32.mak>

all: simple.exe challeng.exe

.c.obj:
  $(cc) $(cdebug) $(cflags) $(cvars) $*.c

simple.exe: simple.obj
  $(link) $(ldebug) $(conflags) -out:simple.exe simple.obj $(conlibs) lsapi32.lib

challeng.exe: challeng.obj md4c.obj
  $(link) $(ldebug) $(conflags) -out:challeng.exe $** $(conlibs) lsapi32.lib
```

## <a name="see-also"></a>Zobacz także

[Zawartość pliku reguł programu Make](contents-of-a-makefile.md)
