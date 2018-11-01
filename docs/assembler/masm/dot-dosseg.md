---
title: .DOSSEG
ms.date: 08/30/2018
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 28b3e351030ee83693c0fec5568aacf9b4b77c27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639442"
---
# <a name="dosseg"></a>.DOSSEG

Porządkuje segmentów zgodnie z Konwencją segmentu systemu MS-DOS: kodu po pierwsze, następnie segmenty nie znajduje się w DGROUP, a następnie segmenty w DGROUP.

## <a name="syntax"></a>Składnia

> .DOSSEG

## <a name="remarks"></a>Uwagi

Segmenty w DGROUP postępuj zgodnie z następującej kolejności: segmenty nie w BSS lub STOS, a następnie BSS segmenty, a na końcu segmenty STOSÓW. Używane głównie dla zapewnienia wsparcia CodeView w programach autonomicznej MASM. Taki sam jak [dosseg —](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>