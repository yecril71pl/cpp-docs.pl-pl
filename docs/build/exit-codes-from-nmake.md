---
title: Kody zakończenia z NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5a593e38efb5230630ed01e65f4bfb1f2ba92a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722621"
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