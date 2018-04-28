---
title: . MODEL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .MODEL
dev_langs:
- C++
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2814b1b6cc4483807f77989ff4fbb70929400d6e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="model"></a>.MODEL
Inicjuje modelu pamięci programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>Parametry  
 `memorymodel`  
 Wymagany parametr, który określa rozmiar wskaźniki kodu i danych.  
  
 `langtype`  
 Opcjonalny parametr, który ustawia Konwencje wywoływania i nazewnictwa dla procedury i symbole publiczne.  
  
 `stackoption`  
 Parametr opcjonalny.  
  
 `stackoption` nie jest używany, jeśli `memorymodel` jest `FLAT`.  
  
 Określanie `NEARSTACK` grupuje segmentu stosu w jednym segmencie fizycznym (`DGROUP`) wraz z danymi. Rejestr segmentu stosu (`SS`) przyjęto, że do przechowywania ten sam adres rejestru segmentu danych (`DS`). `FARSTACK` nie powoduje grupowania stosu z `DGROUP`; w związku z tym `SS` nie jest równa `DS`.  
  
## <a name="remarks"></a>Uwagi  
 .`MODEL` nie jest używany w [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 W poniższej tabeli wymieniono możliwe wartości dla każdego parametru, gdy wybieranie 16-bitowe i 32-bitowych platform:  
  
|Parametr|wartości 32-bitowe|wartości 16-bitowych (Obsługa starszych programowanie 16-bitowe)|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|Nieużywane|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>Kod  
 Dla MASM związane z przykładów pobierania próbek kompilatora z [Visual C++ — przykłady i dokumentacja pokrewna dla programu Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).  
  
 W poniższym przykładzie pokazano użycie `.MODEL` dyrektywy.  
  
## <a name="example"></a>Przykład  
  
```  
; file simple.asm  
; For x86 (32-bit), assemble with debug information:   
;   ml -c -Zi simple.asm  
; For x64 (64-bit), assemble with debug information:   
;   ml64 -c -DX64 -Zi simple.asm  
;  
; In this sample, the 'X64' define excludes source not used   
;  when targeting the x64 architecture  
  
ifndef X64  
.686p  
.XMM  
.model flat, C  
endif  
  
.data  
; user data  
  
.code  
; user code  
  
fxn PROC public  
  xor eax, eax ; zero function return value  
  ret  
fxn ENDP  
  
end  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)   
 [Visual C++ — przykłady i dokumentacja pokrewna dla programu Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)