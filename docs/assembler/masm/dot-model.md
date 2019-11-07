---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: b341cfaec35c08f5ac16447890c85570e9c9c0df
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703579"
---
# <a name="model-32-bit-masm"></a>. MODEL (32-bitowy MASM)

Inicjuje model pamięci programu. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> . MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Parametry

*memorymodel*<br/>
Wymagany parametr określający rozmiar kodu i wskaźników danych.

*langtype*<br/>
Opcjonalny parametr, który ustawia konwencje wywoływania i nazewnictwa dla procedur i symboli publicznych.

*stackoption*<br/>
Opcjonalny parametr.

*stackoption* nie jest używana, jeśli *memorymodel* jest `FLAT`.

Określanie `NEARSTACK` grupuje segment stosu w pojedynczym segmencie fizycznym (`DGROUP`) wraz z danymi. Założono, że rejestr segmentu stosu (`SS`) przechowuje ten sam adres co rejestr segmentu danych (`DS`). `FARSTACK` nie grupuje stosu z `DGROUP`; Tak więc `SS` nie są równe `DS`.

## <a name="remarks"></a>Uwagi

.`MODEL` nie jest używany w programie [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

Poniższa tabela zawiera listę możliwych wartości dla każdego parametru, które są przeznaczone dla platform 16-bitowych i 32-bitowych:

|Parametr|32-wartości bitowe|wartości 16-bitowe (obsługa wcześniejszych wersji 16-bitowych)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL``STDCALL`|
|*stackoption*|Nieużywane|`NEARSTACK`, `FARSTACK`|

## <a name="code"></a>Kod

W przypadku przykładów związanych z MASM Pobierz przykłady kompilatora z [przykładów wizualizacji C++ i powiązanej dokumentacji dla programu Visual Studio 2010](https://go.microsoft.com/fwlink/p/?linkid=178749).

Poniższy przykład demonstruje użycie dyrektywy `.MODEL`.

## <a name="example"></a>Przykład

```asm
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

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
