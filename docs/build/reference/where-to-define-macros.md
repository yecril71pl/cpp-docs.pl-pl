---
title: Miejsce definiowania makr
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: dc03644adea4619b3eabe33c481d71f704a9f410
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823862"
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr

Wiersz polecenia "," pliku poleceń "," pliku reguł programu make "lub" plik Tools.ini do definiowania makra.

W pliku reguł programu make lub pliku Tools.ini Każda definicja makra musi znajdować się w osobnym wierszu, a nie może rozpoczynać się od spacji lub tabulatorów. Spacje lub tabulatory wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](defining-an-nmake-macro.md) są literału, łącznie z otaczającego znaki cudzysłowu i spacji osadzonych.

W wierszu polecenia lub w pliku poleceń spacji od znaków tabulacji argumenty one, a nie całe znaku równości. Jeśli `string` zawierający osadzone spacje lub tabulatory, należy ująć sam ciąg lub całe makro w podwójnym cudzysłowie ("").

## <a name="see-also"></a>Zobacz także

[Definiowanie makro NMAKE](defining-an-nmake-macro.md)
