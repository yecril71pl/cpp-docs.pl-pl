---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313850"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG — (32-bitowy MASM)

Porządkuje segmenty zgodnie z Konwencją segmentu MS-DOS: najpierw kod, następnie segmenty, a nie w DGROUP, a następnie segmenty w DGROUP. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **.DOSSEG**

## <a name="remarks"></a>Uwagi

Segmenty w DGROUP są zgodne z następującą kolejnością: segmenty nie są w BSS lub STOSie, a następnie segmenty BSS i wreszcie segmenty stosu. Używane przede wszystkim do zapewnienia obsługi CodeView w programach autonomicznych MASM. Analogicznie jak [dosseg —](dosseg.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
