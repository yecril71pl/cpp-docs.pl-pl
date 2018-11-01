---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 5c7d5a1cfe16ef3cb1d79617133cd1ceccdfb78c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633518"
---
# <a name="model"></a>.MODEL

Inicjuje model pamięci programu.

## <a name="syntax"></a>Składnia

> . MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Parametry

*memorymodel*<br/>
Wymagany parametr, który określa rozmiar wskaźniki kodu i danych.

*langtype*<br/>
Opcjonalny parametr, który ustawia Konwencje wywoływania i nazewnictwa, aby uzyskać procedury i symboli publicznych.

*stackoption*<br/>
Parametr opcjonalny.

*stackoption* nie jest używane, jeśli *memorymodel* jest `FLAT`.

Określanie `NEARSTACK` grupuje segment stosu w jednym segmencie fizycznym (`DGROUP`) wraz z danymi. Zarejestruj segment stosu (`SS`) zakłada, że jest przechowywania jako ten sam adres rejestru segmentu danych (`DS`). `FARSTACK` nie powoduje grupowania stosu za pomocą `DGROUP`; w związku z tym `SS` nie jest równa `DS`.

## <a name="remarks"></a>Uwagi

.`MODEL` nie jest używany w [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

W poniższej tabeli wymieniono możliwe wartości dla każdego parametru podczas określania wartości 16-bitowe i 32-bitowych platform:

|Parametr|wartości 32-bitowe|wartości 16-bitowych (obsługa opracowywania wcześniej 16-bitowe)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|Nieużywane|`NEARSTACK`, `FARSTACK`|

## <a name="code"></a>Kod

Aby uzyskać przykłady związane z MASM, Pobierz przykłady kompilatora z [przykłady Visual C++ i powiązanej dokumentacji dla programu Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).

W poniższym przykładzie pokazano użycie `.MODEL` dyrektywy.

## <a name="example"></a>Przykład

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>

