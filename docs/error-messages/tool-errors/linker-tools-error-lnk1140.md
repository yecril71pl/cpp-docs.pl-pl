---
title: Błąd narzędzi konsolidatora LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482473"
---
# <a name="linker-tools-error-lnk1140"></a>Błąd narzędzi konsolidatora LNK1140

za dużo modułów dla bazy danych programu; Link z opcją/PDB: NONE

Projekt zawiera więcej niż 4096 modułów.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Połącz ponownie przy użyciu [/PDB: NONE](../../build/reference/pdb-use-program-database.md).

1. Skompilować niektórych modułów bez informacji debugowania.

1. Zmniejsz liczbę modułów.