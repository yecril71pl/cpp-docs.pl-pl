---
title: Błąd narzędzi konsolidatora LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466836"
---
# <a name="linker-tools-error-lnk1200"></a>Błąd narzędzi konsolidatora LNK1200

Błąd odczytu bazy danych programu "filename"

Nie można odczytać bazy danych programu (PDB).

Ten błąd może być spowodowany przez uszkodzenie pliku.

Jeśli `filename` jest pliku PDB dla pliku obiektu, należy ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Jeśli `filename` jest plik PDB dla pliku wyjściowego głównym, a ten błąd wystąpił podczas konsolidowania przyrostowego, usuń plik PDB i połącz ponownie.