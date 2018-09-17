---
title: Makra zerowe i niezdefiniowane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eee6e713715e4709af990878224261a41f5470e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702640"
---
# <a name="null-and-undefined-macros"></a>Makra niezdefiniowane oraz makra o wartości zerowej

Zarówno zerowe i niezdefiniowane makra rozbudowywać ciągów o wartości null, ale makro zdefiniowany jako pusty ciąg jest uważany za zdefiniowany w przetwarzaniu wstępnym wyrażeń. Aby zdefiniować makro jako ciąg pusty, należy określić żadnych znaków, z wyjątkiem znaków tabulacji lub spacji po znaku równości (=), w wierszu polecenia lub pliku poleceń i ująć w znaki cudzysłowu pusty ciąg lub definicji (""). Aby Usuń definicję makra, należy użyć **! UNDEF.** Aby uzyskać więcej informacji, zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Zobacz też

[Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)