---
title: Windows 32-bitowe formaty daty / godziny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55eca447de7818f749628505a4c4f2fa6eb0dcd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061119"
---
# <a name="32-bit-windows-timedate-formats"></a>32-bitowe formaty daty/godziny systemu Windows

Czas pliku i Data są przechowywane osobno, przy użyciu pól bitowych liczb całkowitych bez znaku. Data i godzina w pliku są pakowane w następujący sposób:

### <a name="time"></a>Godzina

|Pozycja bitu:|0   1   2   3   4|5 6 7 8 9 A|B C D E F|
|-------------------|-----------------------|---------------------------|-----------------------|
|Czas trwania:|5|6|5|
|Zawartość:|godziny|minuty|2-sekundowych przyrostów|
|Zakres wartości:|0-23|0-59|0 – 29 w 2-drugie odstępach czasu|

### <a name="date"></a>Data

|Pozycja bitu:|0   1   2   3   4   5   6|7 8 9 A|B C D E F|
|-------------------|-------------------------------|-------------------|-----------------------|
|Czas trwania:|7|4|5|
|Zawartość:|Rok|Miesiąc|dzień|
|Zakres wartości:|0-119|1-12|1-31|
||(względem 1980)|||

## <a name="see-also"></a>Zobacz też

[Stałe globalne](../c-runtime-library/global-constants.md)