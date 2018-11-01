---
title: Błąd krytyczny NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635932"
---
# <a name="nmake-fatal-error-u1056"></a>Błąd krytyczny NMAKE U1056

Nie można znaleźć procesora poleceń

Procesor poleceń nie znajdowała się w ścieżce określonej w **COMSPEC** lub **ścieżki** zmiennych środowiskowych.

NMAKE używa COMMAND.COM lub CMD. EXE jako podmiot przetwarzający polecenia podczas wykonywania polecenia. Szuka procesora poleceń najpierw w ścieżce w **COMSPEC**. Jeśli **COMSPEC** nie istnieje, NMAKE wyszukiwania katalogów określonych w **ścieżki**.