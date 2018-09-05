---
title: IF (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0cce834924f7fc147b1ef301d5bd345dfd2973
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685310"
---
# <a name="if-masm"></a>IF (MASM)

Przyznaje zestawu *ifstatements* Jeśli *wyrażenie1* ma wartość true (niezerową) lub *elseifstatements* Jeśli *wyrażenie1* ma wartość false (0) i *wyrażenie2* ma wartość true.

## <a name="syntax"></a>Składnia

> Jeśli *wyrażenie1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *wyrażenie2*<br/>
> *elseifstatements*]]<br/>
> [[ELSE<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>Uwagi

Może być zastąpiona następujące dyrektywy [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI** , **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, i **ELSEIFNDEF** . Opcjonalnie składa *elsestatements* Jeśli poprzednie wyrażenie ma wartość false. Należy pamiętać, że wyrażenia są obliczane w czasie zestawu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>