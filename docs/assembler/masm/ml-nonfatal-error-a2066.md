---
title: Błąd niekrytyczny ML A2066
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 4c7c32264fe5daa6cd4e14f47cff111899e8f8d6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316892"
---
# <a name="ml-nonfatal-error-a2066"></a>Błąd niekrytyczny ML A2066

**niezgodny tryb procesora CPU i rozmiar segmentu**

Podjęto próbę otwarcia segmentu z atrybutem **USE16**, **USE32**lub **flatem** , który nie jest zgodny z określonym procesorem CPU, lub aby zmienić na 16-bitowy procesor w ramach segmentu 32-bitowego.

Atrybuty **USE32** i **Flat** muszą być poprzedzone dyrektywą procesora. 386 lub większą.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
