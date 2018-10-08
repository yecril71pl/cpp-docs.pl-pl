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
ms.openlocfilehash: 1c70c76292b62560b1d9895aca2851b4cf56802b
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861801"
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