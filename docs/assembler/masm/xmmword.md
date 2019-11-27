---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: c7783049a143b19295a67cd3e9e40afeab3c814f
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74392792"
---
# <a name="xmmword"></a>XMMWORD

Używany do 128-bitowego operandów multimediów z instrukcjami MMX i SSE (XMM).

## <a name="syntax"></a>Składnia

> **XMMWORD**

## <a name="remarks"></a>Uwagi

**XMMWORD** jest przeznaczony do reprezentowania tego samego typu co [__m128](../../cpp/m128.md).

## <a name="example"></a>Przykład

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```
