---
title: Błąd niekrytyczny ML A2066 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 92cc0daf183f617767ff5ff119c5e95b8f34cd51
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054266"
---
# <a name="ml-nonfatal-error-a2066"></a>Błąd niekrytyczny ML A2066
**niezgodne rozmiar trybu i segmentów Procesora**  
  
 Podjęto próbę otwarcia segment o **USE16**, **USE32**, lub **PŁASKIEJ** atrybut, który nie jest zgodny z określonym procesora CPU lub zmienić do 16-bitowego procesora CPU w 32-bitowy Segment.  
  
 **USE32** i **PŁASKIEJ** atrybutów musi być poprzedzona.386 lub większa procesora dyrektywy.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)