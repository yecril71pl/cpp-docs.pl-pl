---
title: . DOSSEG — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693235"
---
# <a name="dosseg"></a>.DOSSEG

Porządkuje segmentów zgodnie z Konwencją segmentu systemu MS-DOS: kodu po pierwsze, następnie segmenty nie znajduje się w DGROUP, a następnie segmenty w DGROUP.

## <a name="syntax"></a>Składnia

> .DOSSEG

## <a name="remarks"></a>Uwagi

Segmenty w DGROUP postępuj zgodnie z następującej kolejności: segmenty nie w BSS lub STOS, a następnie BSS segmenty, a na końcu segmenty STOSÓW. Używane głównie dla zapewnienia wsparcia CodeView w programach autonomicznej MASM. Taki sam jak [dosseg —](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>