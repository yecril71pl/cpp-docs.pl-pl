---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 17edea122afc03a8c3a2fdc86ee6c06c2ccf3c85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398486"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG — (32-bitowy MASM)

Porządkuje segmenty zgodnie z Konwencją segmentu MS-DOS: najpierw kod, następnie segmenty, a nie w DGROUP, a następnie segmenty w DGROUP. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **.DOSSEG**

## <a name="remarks"></a>Uwagi

Segmenty w DGROUP są zgodne z następującą kolejnością: segmenty nie są w BSS lub STOSie, a następnie segmenty BSS i wreszcie segmenty stosu. Używane przede wszystkim do zapewnienia obsługi CodeView w programach autonomicznych MASM. Analogicznie jak [dosseg —](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
