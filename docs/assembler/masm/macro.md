---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076147"
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

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[Goto (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
