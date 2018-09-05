---
title: . KOD | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682490"
---
# <a name="code"></a>.CODE

Gdy jest używane z [. MODEL](../../assembler/masm/dot-model.md), wskazuje początek segment kodu.

## <a name="syntax"></a>Składnia

> . Kod [[name]]

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`name`|Opcjonalny parametr określający nazwę segmentu kodu. Nazwa domyślna to _text — kompaktowy małe, małe, i stosowana jest stała [modeli](../../assembler/masm/dot-model.md). Nazwa domyślna to *modulename*_text — w przypadku innych modeli.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>