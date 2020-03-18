---
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 6e63f5c8075b3c94370ad8863d224c097cf0ecdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440751"
---
# <a name="if"></a>IF

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

Następujące dyrektywy mogą zostać zastąpione przez [ElseIf](elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**i **ELSEIFNDEF**. Opcjonalnie należy połączyć *inne instrukcje* , jeśli poprzednie wyrażenie ma wartość false. Należy zauważyć, że wyrażenia są oceniane w czasie montażu.

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
