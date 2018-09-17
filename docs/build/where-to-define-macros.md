---
title: Miejsce definiowania makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29a2899d7dba0b34c0ac3319c253c8056912d883
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713820"
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr

Wiersz polecenia "," pliku poleceń "," pliku reguł programu make "lub" plik Tools.ini do definiowania makra.

W pliku reguł programu make lub pliku Tools.ini Każda definicja makra musi znajdować się w osobnym wierszu, a nie może rozpoczynać się od spacji lub tabulatorów. Spacje lub tabulatory wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](../build/defining-an-nmake-macro.md) są literału, łącznie z otaczającego znaki cudzysłowu i spacji osadzonych.

W wierszu polecenia lub w pliku poleceń spacji od znaków tabulacji argumenty one, a nie całe znaku równości. Jeśli `string` zawierający osadzone spacje lub tabulatory, należy ująć sam ciąg lub całe makro w podwójnym cudzysłowie ("").

## <a name="see-also"></a>Zobacz też

[Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)