---
title: IF1 i IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317321"
---
# <a name="if1-and-if2"></a>IF1 i IF2

Blok **IF1** jest oceniany podczas pierwszego przebiegu zestawu.

Blok **IF2** jest obliczany na każdym przebiegu zestawu, jeśli **Opcja: SETIF2** ma **wartość true**.

## <a name="syntax"></a>Składnia

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>Uwagi

Aby uzyskać pełną składnię [, zobacz.](if-masm.md)

W przeciwieństwie do wersji 5,1, MASM 6,1 i nowszych większość pracy z pierwszego przebiegu, a następnie wykonuje tyle kolejnych przebiegów w razie potrzeby. Z kolei MASM 5,1 zawsze składa się z dwóch przebiegów źródłowych. W związku z tym może zajść potrzeba zmiany lub usunięcia niektórych konstrukcji zależnych od przebiegu w ramach MASM 6,1 i nowszych.

### <a name="two-pass-directives"></a>Dyrektywy dwuprzebiegowe

Aby zapewnić zgodność, MASM 6,1 i nowsze wsparcie 5,1 dyrektywy odnoszące się do dwóch przebiegów. Należą do nich **. ERR1**, **. ERR2**, **IF1**, **IF2**, **ELSEIF1**i **ELSEIF2**. Dla konstrukcji drugiego przebiegu należy określić [opcję SETIF2](option-masm.md). Bez **opcji SETIF2**, **IF2** i **. ERR2** dyrektywy powodują wystąpienie błędu:

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6,1 i nowsze dojście pierwszego przebiegu w inny sposób. Traktuje **. Dyrektywa ERR1** jako **. BŁĄD**i dyrektywa **IF1** jako **if**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
