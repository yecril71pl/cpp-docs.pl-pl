---
title: Zasady dotyczące trybu partii
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328411"
---
# <a name="batch-mode-rules"></a>Zasady dotyczące trybu partii

```
{frompath}.fromext{topath}.toext::
   commands
```

Reguły wnioskowania w trybie wsadowym zapewniają tylko jedno wywołanie reguły wnioskowania, gdy polecenia N przechodzą przez tę regułę wnioskowania. Bez reguł wnioskowania w trybie wsadowym wymagałoby n polecenia do wywołania. N to liczba osób zależnych, które wyzwalają regułę wnioskowania.

Pliki makefiles, które zawierają reguły wnioskowania w trybie wsadowym, muszą używać NMAKE w wersji 1.62 lub nowszej. Aby sprawdzić wersję NMAKE, uruchom makro _NMAKE_VER dostępne z NMAKE w wersji 1.62 lub nowszej. To makro zwraca ciąg reprezentujący wersję produktu Visual C++.

Jedyną różnicą syntaktyczną od reguły wnioskowania standardowego jest to, że reguła wnioskowania w trybie wsadowym jest kończyona podwójnym dwukropkiem (::).

> [!NOTE]
> Wywoływane narzędzie musi być w stanie obsłużyć wiele plików. Reguła wnioskowania w trybie wsadowym musi być używana `$<` jako makro, aby uzyskać dostęp do plików zależnych.

Reguły wnioskowania w trybie wsadowym mogą przyspieszyć proces kompilacji. Jest szybsze dostarczanie plików do kompilatora w partii, ponieważ sterownik kompilatora jest wywoływany tylko raz. Na przykład kompilator C i C++ działa lepiej podczas obsługi zestawu plików, ponieważ może pozostać rezydentem pamięci podczas procesu.

W poniższym przykładzie pokazano, jak używać reguł wnioskowania w trybie wsadowym:

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

NMAKE generuje następujące dane wyjściowe bez reguł wnioskowania w trybie wsadowym:

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

NMAKE daje następujący wynik z regułami wnioskowania w trybie wsadowym:

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

[Zasady wnioskowania](inference-rules.md)
