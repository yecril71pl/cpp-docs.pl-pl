---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312953"
---
# <a name="macro"></a>MACRO

Oznacza blok makra o nazwie *name* i ustanawia symbole zastępcze *parametru* dla argumentów przewidzianych podczas wywoływania makra.

## <a name="syntax"></a>Składnia

> *Nazwij***makro** ⟦*parametr* ⟦ **: REQ** | : =*default* | *args* **: vararg**⟧... ⟧\
> *instrukcje*\
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦*wartość*⟧

## <a name="remarks"></a>Uwagi

Funkcja makro zwraca *wartość* do instrukcji wywołującej.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[Goto (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)

