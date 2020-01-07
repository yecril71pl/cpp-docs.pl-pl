---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 92f14a352e5c177d767232eed36a7e705fd155ce
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317633"
---
# <a name="model-32-bit-masm"></a>. MODEL (32-bitowy MASM)

Inicjuje model pamięci programu. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **. Model** *pamięci* modelu ⟦ __,__ *Language-Type*⟧ ⟦ __,__ *Stack-Option*⟧

### <a name="parameters"></a>Parametry

\ *modelu pamięci*
Wymagany parametr określający rozmiar kodu i wskaźników danych.

\ *typu języka*
Opcjonalny parametr, który ustawia konwencje wywoływania i nazewnictwa dla procedur i symboli publicznych.

\ *opcji stosu*
Parametr opcjonalny.

*stos-opcja* nie jest używana, jeśli *model pamięci* jest **płaski**.

Określanie grup **NEARSTACK** segment stosu w pojedynczym segmencie fizycznym (**DGROUP**) wraz z danymi. Przyjęto założenie, że rejestr segmentów stosu ma ten sam adres co rejestr segmentu danych (**ds** **).** **FARSTACK** nie grupuje stosu z **DGROUP**; w tym przypadku **SS** nie jest równe **ds**.

## <a name="remarks"></a>Uwagi

**. MODEL** nie jest używany w programie [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

Poniższa tabela zawiera listę możliwych wartości dla każdego parametru, które są przeznaczone dla platform 16-bitowych i 32-bitowych:

|Parametr|32-wartości bitowe|wartości 16-bitowe (obsługa wcześniejszych wersji 16-bitowych)|
|---------------|--------------------|----------------------------------------------------------------|
|*model pamięci*|**ZRYCZAŁTOWANY**|**małe**, **małe**, **kompaktowe**, **średnie**, **duże**, **ogromne**, **płaskie**|
|*typ języka*|**C**, **stdcall**|**C**, **Basic**, **Pascal**, **Pascal**, **syscall**, **stdcall**|
|*Stack — opcja*|Nieużywane|**NEARSTACK**, **FARSTACK**|

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

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
