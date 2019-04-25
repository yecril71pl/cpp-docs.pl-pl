---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 65d336d2829c97fdf21e6f4b0fcb3063cc7776ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204377"
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