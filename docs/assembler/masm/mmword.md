---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: d4378c1435df09f249fe7f55dabd4bd0f43f6100
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397172"
---
# <a name="mmword"></a>MMWORD

Używany do 64-bitowego operandów multimediów z instrukcjami MMX i SSE (XMM).

## <a name="syntax"></a>Składnia

> **MMWORD**

## <a name="remarks"></a>Uwagi

**MMWORD** jest typem.  Przed dodaniem **MMWORD** do MASM można osiągnąć równoważne funkcje przy użyciu:

```asm
    mov mm0, qword ptr [ebx]
```

Chociaż obie instrukcje działają na 64-bitowych operandach, **Qword** jest typem dla 64-bitowych liczb całkowitych bez znaku, a **MMWORD** jest typem dla 64-bitowej wartości multimedialnej.

**MMWORD** jest przeznaczony do reprezentowania tego samego typu co [__m64](../../cpp/m64.md).

## <a name="example"></a>Przykład

```asm
    movq     mm0, mmword ptr [ebx]
```
