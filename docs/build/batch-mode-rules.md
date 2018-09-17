---
title: Zasady dotyczące trybu partii | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ddc5983f6a18146d12c75484e0db70f12797b35
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706241"
---
# <a name="batch-mode-rules"></a>Zasady dotyczące trybu partii

```
{frompath}.fromext{topath}.toext::
   commands
```

Zasady wnioskowania w trybie usługi Batch zapewniają tylko jedno wywołanie reguły wnioskowania, gdy polecenia N za pomocą tej reguły wnioskowania. Bez zasady wnioskowania w trybie wsadowym będzie to wymagać N poleceń do wywołania. N to liczba zależności, które mogą powodować reguły wnioskowania.

Pliki reguł programu make, która zawiera zasady wnioskowania w trybie wsadowym należy użyć NMAKE wersji 1.62 lub nowszej. Aby sprawdzić wersję NMAKE, należy uruchomić makro _NMAKE_VER dostępne z NMAKE wersji 1.62 lub nowszej. To makro zwraca ciąg reprezentujący wersję produktu Visual C++.

Tylko syntaktyczny różnica reguły wnioskowania standardowa polega na tym, że reguła wnioskowania w trybie wsadowym jest kończony przy użyciu podwójny dwukropek (:).

> [!NOTE]
>  Narzędzie wywoływanej musi mieć możliwość obsługi wielu plików. Reguła wnioskowania w trybie wsadowym należy użyć `$<` jako makra, aby uzyskać dostęp do plików zależnych.

Zasady wnioskowania w trybie usługi batch można przyspieszyć proces kompilacji. To szybsze do dostarczania plików do kompilatora w partii, ponieważ sterownik kompilator jest wywoływany tylko raz. Kompilator C i C++ działa na przykład, lepiej podczas obsługi zestawu plików, ponieważ może pozostać, pamięć, miejsce zamieszkania w procesie.

Poniższy przykład pokazuje, jak używać reguły wnioskowania w trybie wsadowym:

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE generuje następujące dane wyjściowe bez zasady wnioskowania w trybie wsadowym:

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE generuje następujące wyniki za pomocą reguły wnioskowania w trybie wsadowym:

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)