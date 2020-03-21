---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076279"
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

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[.\ danych](dot-data.md)
[MASM BNF, gramatyka](masm-bnf-grammar.md)
