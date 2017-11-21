---
title: "Zasady dotyczące trybu partii | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: be8c00009e285ec84f42ae6f53c578a3084432de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="batch-mode-rules"></a>Zasady dotyczące trybu partii
```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 Zasady wnioskowania w trybie wsadowym udzielać tylko jedno wywołanie reguły wnioskowania polecenia N go za pomocą tej reguły wnioskowania. Bez zasady wnioskowania w trybie wsadowym będzie to wymagać N poleceń do wywołania. N to liczba zależności, które wyzwolenie reguły wnioskowania.  
  
 Pliki reguł programu make, która zawiera zasady wnioskowania w trybie wsadowym należy użyć NMAKE wersji 1.62 lub nowszej. Aby sprawdzić wersję NMAKE, uruchom makro _NMAKE_VER dostępne z NMAKE wersji 1.62 lub nowszej. To makro zwraca ciąg reprezentujący wersji produktu Visual C++.  
  
 Tylko syntaktycznych różnica z reguły wnioskowania standardowe jest, czy reguła wnioskowania w trybie wsadowym kończy się znakiem podwójnego dwukropka (:).  
  
> [!NOTE]
>  Wywoływanie narzędzia musi mieć możliwość obsługi wielu plików. Reguła wnioskowania w trybie wsadowym należy użyć `$<` jako makro dostęp do plików zależnych.  
  
 Zasady wnioskowania w trybie wsadowym można przyspieszyć proces kompilacji. Jest szybsze do dostarczania plików do kompilatora w partii, ponieważ sterownik kompilatora jest wywoływany tylko raz. Kompilator C i C++ wykonuje na przykład lepiej podczas obsługi zestawu plików, ponieważ może pozostawać pamięci rezydentna podczas procesu.  
  
 Poniższy przykład przedstawia użycie zasady wnioskowania w trybie wsadowym:  
  
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
  
 NMAKE tworzy następujące dane wyjściowe bez zasady wnioskowania w trybie wsadowym:  
  
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
  
 NMAKE tworzy następujące wyniki z zasady wnioskowania w trybie wsadowym:  
  
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