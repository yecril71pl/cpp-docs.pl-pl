---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314149"
---
# <a name="code"></a>.CODE

(tylko 32-bitowy MASM). W przypadku użycia z [. MODEL](dot-model.md)wskazuje początek segmentu kodu.

## <a name="syntax"></a>Składnia

> **. KOD** ⟦*Nazwa*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **;;** ⟧\

### <a name="parameters"></a>Parametry

\ *nazwy*
Opcjonalny parametr, który określa nazwę segmentu kodu. Domyślna nazwa jest **_TEXT** dla [modeli](dot-model.md)bardzo mały, mały, kompaktowy i płaski. Nazwa domyślna to *modulename*_TEXT dla innych modeli.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[.\ danych](dot-data.md)
[MASM BNF, gramatyka](masm-bnf-grammar.md)

