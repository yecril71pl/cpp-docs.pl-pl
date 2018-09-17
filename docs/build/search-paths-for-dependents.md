---
title: Ścieżki wyszukiwania dla zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1fd407f99abb98fb949b6d5bcc45b10c6ff9121
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706312"
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