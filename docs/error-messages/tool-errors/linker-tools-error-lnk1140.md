---
title: Błąd narzędzi konsolidatora LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195269"
---
# <a name="linker-tools-error-lnk1140"></a>Błąd narzędzi konsolidatora LNK1140

za dużo modułów dla bazy danych programu; Połącz z/PDB: brak

Projekt zawiera więcej niż 4096 modułów.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Połącz ponownie przy użyciu [/PDB: none](../../build/reference/pdb-use-program-database.md).

1. Kompiluj niektóre moduły bez informacji o debugowaniu.

1. Zmniejsz liczbę modułów.
