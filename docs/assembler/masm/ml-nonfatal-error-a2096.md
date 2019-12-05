---
title: Błąd niekrytyczny ML A2096
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855477"
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096

**Oczekiwano rejestru segmentów, grup lub segmentów**

Oczekiwano segmentu lub grupy, ale nie znaleziono tego elementu.

Wystąpił jeden z następujących:

- Lewy argument operacji określony za pomocą operatora przesłonięcia segmentu ( **:** ) nie jest rejestrem segmentu (CS, DS, SS, ES, FS lub GS), nazwą grupy, nazwą segmentu ani wyrażeniem segmentu.

- [Przyjęto](../../assembler/masm/assume.md) , że dyrektywa przyjmuje rejestr segmentu bez prawidłowego adresu segmentu, rejestru segmentów, grupy lub specjalnej grupy **prostej** .

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>