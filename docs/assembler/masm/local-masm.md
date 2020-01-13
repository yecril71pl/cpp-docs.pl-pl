---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317152"
---
# <a name="local"></a>LOCAL

W pierwszej dyrektywie w makrze **lokalna** definiuje etykiety, które są unikatowe dla każdego wystąpienia makra.

## <a name="syntax"></a>Składnia

> **Local** *LocalId* ⟦, *LocalId* ... ⟧
>
> **Local** *labelId* ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *kwalifikowanatype*⟧ ⟦ __,__ *labelId* ⟦ __\[__ *Count* __]__ ⟧ ⟦*kwalifikowanatype*⟧... ⟧

## <a name="remarks"></a>Uwagi

W drugiej dyrektywie, w ramach definicji procedury (**proc**), **lokalna** tworzy zmienne oparte na stosie, które istnieją na czas trwania tej procedury. *LabelId* może być prostą zmienną lub tablicą zawierającą elementy *Count* , gdzie *Count* jest wyrażeniem stałym.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
