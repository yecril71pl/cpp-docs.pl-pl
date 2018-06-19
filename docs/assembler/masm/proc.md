---
title: PROC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48eb872d394c3b131d32d4b41c5923883ff36cee
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057776"
---
# <a name="proc"></a>PROC
Oznacza początek i koniec bloku procedury o nazwie *etykiety*. Instrukcje w bloku może być wywołany z **WYWOŁAĆ** instrukcji lub [INVOKE](../../assembler/masm/invoke.md) dyrektywy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## <a name="remarks"></a>Uwagi  
 [Ramki [:*ehandler adres*]] jest prawidłowa tylko z ml64.exe i powoduje, że MASM można wygenerować wpisu tabeli funkcji w .pdata i unwind informacji w .xdata dla funkcji przez strukturę zachowanie unwind obsługi wyjątków.  
  
 Gdy **ramki** atrybut jest używany, musi następować przez [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy.  
  
 Zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) Aby uzyskać więcej informacji na temat używania ml64.exe.  
  
## <a name="example"></a>Przykład  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
 Powyższy kod będzie emisji w poniższej tabeli funkcji i unwind informacji:  
  
```  
FileHeader->Machine 34404  
Dumping Unwind Information for file ex2.exe  
  
.pdata entry 1 0x00001000 0x00001023  
  
  Unwind data: 0x00002000  
  
    Unwind version: 1  
    Unwind Flags: None  
    Size of prologue: 0x08  
    Count of codes: 3  
    Frame register: rbp  
    Frame offset: 0x0  
    Unwind codes:  
  
      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00  
      Code offset: 0x05, ALLOC_SMALL, size=0x10  
      Code offset: 0x01, PUSH_NONVOL, register=rbp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)