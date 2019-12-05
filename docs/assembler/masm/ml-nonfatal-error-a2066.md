---
title: Błąd niekrytyczny ML A2066
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 8dc3000b2edc2b1ecda7cc3952b554296de19aa3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855882"
---
# <a name="ml-nonfatal-error-a2066"></a>Błąd niekrytyczny ML A2066

**niezgodny tryb procesora CPU i rozmiar segmentu**

Podjęto próbę otwarcia segmentu z atrybutem **USE16**, **USE32**lub **flatem** , który nie jest zgodny z określonym procesorem CPU, lub aby zmienić na 16-bitowy procesor w ramach segmentu 32-bitowego.

Atrybuty **USE32** i **Flat** muszą być poprzedzone dyrektywą procesora. 386 lub większą.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>