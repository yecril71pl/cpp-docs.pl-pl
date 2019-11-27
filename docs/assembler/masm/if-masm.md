---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: ed7b9e63bb19dcc16539dbdaaf1f6a7f16566b3c
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397463"
---
# <a name="if-masm"></a>IF (MASM)

Przyznaje zestaw elementu *ifstatements* , jeśli *wyrażenie1* ma wartość true (niezerowa) lub *elseifstatements* , jeśli *wyrażenie1* ma wartość false (0), a *wyrażenie2* ma wartość true.

## <a name="syntax"></a>Składnia

> **Jeśli** *wyrażenie1*\
> *if-statements*\
> ⟦**ElseIf** *wyrażenie2*\
> *ElseIf-Statements*⟧ \
> ⟦**ELSE**\
> *else-instrukcje*⟧ \
> **ENDIF**

## <a name="remarks"></a>Uwagi

Następujące dyrektywy mogą zostać zastąpione przez [ElseIf](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**i **ELSEIFNDEF**. Opcjonalnie należy połączyć *inne instrukcje* , jeśli poprzednie wyrażenie ma wartość false. Należy zauważyć, że wyrażenia są oceniane w czasie montażu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
