---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 2b91698640e028bf91d822c12b85ded651a04d8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203067"
---
# <a name="if-masm"></a>IF (MASM)

Przyznaje zestawu *ifstatements* Jeśli *wyrażenie1* ma wartość true (niezerową) lub *elseifstatements* Jeśli *wyrażenie1* ma wartość false (0) i *wyrażenie2* ma wartość true.

## <a name="syntax"></a>Składnia

> IF *expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[ELSE<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>Uwagi

Może być zastąpiona następujące dyrektywy [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, i **ELSEIFNDEF**. Opcjonalnie składa *elsestatements* Jeśli poprzednie wyrażenie ma wartość false. Należy pamiętać, że wyrażenia są obliczane w czasie zestawu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>