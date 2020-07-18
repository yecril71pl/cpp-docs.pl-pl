---
title: OPTION (MASM)
ms.date: 07/15/2020
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a614697a9d633628b02b59a7b810fa261887f859
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446440"
---
# <a name="option"></a>OPTION

Włącza i wyłącza funkcje asemblera.

## <a name="syntax"></a>Składnia

> **`OPTION`***Lista opcji*

## <a name="remarks"></a>Uwagi

Dostępne opcje to:

:::row:::
   :::column span="":::
      **`CASEMAP`**<br/>**`DOTNAME`**<br/>**`NODOTNAME`**<br/>**`EMULATOR`**<br/>**`NOEMULATOR`**<br/>**`EPILOGUE`**<br/>**`EXPR16`**
   :::column-end:::
   :::column span="":::
      **`EXPR32`**<br/>**`LANGUAGE`**<br/>**`LJMP`**<br/>**`NOLJMP`**<br/>**`M510`**<br/>**`NOM510`**<br/>**`NOKEYWORD`**
   :::column-end:::
   :::column span="":::
      **`NOSIGNEXTEND`**<br/>**`OFFSET`**<br/>**`OLDMACROS`**<br/>**`NOOLDMACROS`**<br/>**`OLDSTRUCTS`**<br/>**`NOOLDSTRUCTS`**<br/>**`PROC`**
   :::column-end:::
   :::column span="":::
      **`PROLOGUE`**<br/>**`READONLY`**<br/>**`NOREADONLY`**<br/>**`SCOPED`**<br/>**`NOSCOPED`**<br/>**`SEGMENT`**<br/>**`SETIF2`**
   :::column-end:::
:::row-end:::

Składnia języka to **`OPTION LANGUAGE:`** _`x`_ , gdzie *`x`* jest jedną z,, **`C`** **`SYSCALL`** ,, **`STDCALL`** **`PASCAL`** **`FORTRAN`** , lub **`BASIC`** . **`SYSCALL`**, **`PASCAL`** , **`FORTRAN`** i **`BASIC`** nie są obsługiwane w programie [`.MODEL`](dot-model.md) **`FLAT`** .

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
