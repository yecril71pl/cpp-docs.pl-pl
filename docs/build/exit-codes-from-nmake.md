---
title: Kody zakończenia z NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 08aceadf107112b446844b09fad24a11fbe7a731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499596"
---
# <a name="exit-codes-from-nmake"></a>Kody zakończenia z NMAKE

NMAKE zwraca poniższe kody zakończenia:

|Kod|Znaczenie|
|----------|-------------|
|0|Brak błędu (prawdopodobnie ostrzeżenie)|
|1|Niekompletne kompilacji (wydać tylko wtedy, gdy jest używany /K)|
|2|Błąd programu, prawdopodobnie z powodu jednej z następujących czynności:|
||-Błąd składni w pliku reguł programu make|
||— Kod błędu lub zakończenia z polecenia|
||-Przerwania przez użytkownika|
|4|Błąd systemu — za mało pamięci|
|255|Element docelowy nie jest aktualna (wydać tylko wtedy, gdy jest używany/q)|

## <a name="see-also"></a>Zobacz też

[Uruchomienie NMAKE](../build/running-nmake.md)