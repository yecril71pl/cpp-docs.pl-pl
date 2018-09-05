---
title: Błąd niekrytyczny ML A2066 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2066
dev_langs:
- C++
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf5cbe7d5c77da7f129cbc40ffa97f4051afca6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690255"
---
# <a name="ml-nonfatal-error-a2066"></a>Błąd niekrytyczny ML A2066

**niezgodne rozmiar tryb i segmentów procesora CPU**

Próbowano otworzyć segment o **USE16**, **USE32**, lub **PROSTEGO** atrybut, który nie jest zgodny z określonym procesora CPU lub zmienić na 16-bitowego Procesora w 32-bitowa Segment.

**USE32** i **PROSTEGO** atrybuty muszą być poprzedzone.386 lub większa procesora dyrektywy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>