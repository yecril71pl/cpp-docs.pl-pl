---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: e4ebaa9d47a569bc9cf7d843d3ddb54ca5d713a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176866"
---
# <a name="mmword"></a>MMWORD

Używane dla operandów multimedialnych 64-bitowe instrukcje MMX i SSE (XMM).

## <a name="syntax"></a>Składnia

> MMWORD

## <a name="remarks"></a>Uwagi

`MMWORD` jest typem.  Przed mmword — dodawany do MASM równoważne funkcje mógł być osiągnięty przy użyciu:

```asm
    mov mm0, qword ptr [ebx]
```

Gdy zarówno instrukcje działać na operandach 64-bitowych `QWORD` jest typem liczb całkowitych bez znaku 64-bitowych i `MMWORD` jest typem multimediów wartość 64-bitowych.

`MMWORD` reprezentuje tego samego typu co [__m64](../../cpp/m64.md).

## <a name="example"></a>Przykład

```asm
    movq     mm0, mmword ptr [ebx]
```