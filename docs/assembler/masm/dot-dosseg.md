---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 8f0388c3df9804c0cdb105162a962a44fe207345
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703318"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG — (32-bitowy MASM)

Porządkuje segmenty zgodnie z Konwencją segmentu MS-DOS: najpierw kod, następnie segmenty, a nie w DGROUP, a następnie segmenty w DGROUP. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> .DOSSEG

## <a name="remarks"></a>Uwagi

Segmenty w DGROUP są zgodne z następującą kolejnością: segmenty nie są w BSS lub STOSie, a następnie segmenty BSS i wreszcie segmenty stosu. Używane przede wszystkim do zapewnienia obsługi CodeView w programach autonomicznych MASM. Analogicznie jak [dosseg —](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>