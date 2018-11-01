---
title: Przeszukuj ścieżki pod kątem zależności
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 8856d845d51072d205c84278978c7fbb447aed9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448805"
---
# <a name="search-paths-for-dependents"></a>Przeszukuj ścieżki pod kątem zależności

Każdy zależnych od ustawień lokalnych ma ścieżkę wyszukiwania opcjonalne, określone w następujący sposób:

## <a name="syntax"></a>Składnia

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>Uwagi

NMAKE szuka zależnych od ustawień lokalnych pierwszy w bieżącym katalogu, a następnie w katalogach w określonej kolejności. Makra można określić część lub całość ścieżki wyszukiwania. Katalog nazw należy ujmować w nawiasy klamrowe ({}); Oddziel wiele katalogów przy użyciu średnika (;). Nie spacje lub tabulatory są dozwolone.

## <a name="see-also"></a>Zobacz też

[Zależności](../build/dependents.md)