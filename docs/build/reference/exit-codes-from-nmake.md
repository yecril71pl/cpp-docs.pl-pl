---
title: Kody zakończenia z NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 25ea4060e7b7a968b6a9da78f344e645c5d43a44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271472"
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

## <a name="see-also"></a>Zobacz także

[Uruchomienie NMAKE](running-nmake.md)
