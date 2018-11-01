---
title: Miejsce definiowania makr
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: 130863f8c5640a0c4915734732d93fc00d3d6479
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656251"
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr

Wiersz polecenia "," pliku poleceń "," pliku reguł programu make "lub" plik Tools.ini do definiowania makra.

W pliku reguł programu make lub pliku Tools.ini Każda definicja makra musi znajdować się w osobnym wierszu, a nie może rozpoczynać się od spacji lub tabulatorów. Spacje lub tabulatory wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](../build/defining-an-nmake-macro.md) są literału, łącznie z otaczającego znaki cudzysłowu i spacji osadzonych.

W wierszu polecenia lub w pliku poleceń spacji od znaków tabulacji argumenty one, a nie całe znaku równości. Jeśli `string` zawierający osadzone spacje lub tabulatory, należy ująć sam ciąg lub całe makro w podwójnym cudzysłowie ("").

## <a name="see-also"></a>Zobacz też

[Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)