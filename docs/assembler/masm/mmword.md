---
title: MMWORD — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7314c6d0861195e312c7f72481d2e195e041965d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679237"
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