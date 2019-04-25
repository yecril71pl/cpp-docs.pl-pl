---
title: Windows 32-bitowe formaty daty / godziny
ms.date: 11/04/2016
f1_keywords:
- vc.time
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
ms.openlocfilehash: 4827f82df08273dfa369d6242b9fe2be84875128
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290576"
---
# <a name="32-bit-windows-timedate-formats"></a>32-bitowe formaty daty/godziny systemu Windows

Czas pliku i Data są przechowywane osobno, przy użyciu pól bitowych liczb całkowitych bez znaku. Data i godzina w pliku są pakowane w następujący sposób:

### <a name="time"></a>Godzina

|Pozycja bitu:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|
|-------------------|-----------------------|---------------------------|-----------------------|
|Czas trwania:|5|6|5|
|Zawartość:|godziny|minuty|2-sekundowych przyrostów|
|Zakres wartości:|0-23|0-59|0 – 29 w 2-drugie odstępach czasu|

### <a name="date"></a>Data

|Pozycja bitu:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|
|-------------------|-------------------------------|-------------------|-----------------------|
|Czas trwania:|7|4|5|
|Zawartość:|rok|miesiąc|dzień|
|Zakres wartości:|0-119|1-12|1-31|
||(względem 1980)|||

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)
