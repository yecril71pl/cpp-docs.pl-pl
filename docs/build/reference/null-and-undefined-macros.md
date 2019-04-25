---
title: Makra niezdefiniowane oraz makra o wartości zerowej
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: 0f4905473dd6914547ad6ac129d34e438992c2af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320503"
---
# <a name="null-and-undefined-macros"></a>Makra niezdefiniowane oraz makra o wartości zerowej

Zarówno zerowe i niezdefiniowane makra rozbudowywać ciągów o wartości null, ale makro zdefiniowany jako pusty ciąg jest uważany za zdefiniowany w przetwarzaniu wstępnym wyrażeń. Aby zdefiniować makro jako ciąg pusty, należy określić żadnych znaków, z wyjątkiem znaków tabulacji lub spacji po znaku równości (=), w wierszu polecenia lub pliku poleceń i ująć w znaki cudzysłowu pusty ciąg lub definicji (""). Aby Usuń definicję makra, należy użyć **! UNDEF.** Aby uzyskać więcej informacji, zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](makefile-preprocessing-directives.md).

## <a name="see-also"></a>Zobacz także

[Definiowanie makro NMAKE](defining-an-nmake-macro.md)
