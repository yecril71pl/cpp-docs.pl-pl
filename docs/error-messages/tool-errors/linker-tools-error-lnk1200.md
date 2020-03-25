---
title: Błąd narzędzi konsolidatora LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195139"
---
# <a name="linker-tools-error-lnk1200"></a>Błąd narzędzi konsolidatora LNK1200

błąd podczas odczytywania bazy danych programu "filename"

Nie można odczytać bazy danych programu (PDB).

Ten błąd może być spowodowany uszkodzeniem pliku.

Jeśli `filename` jest plikiem PDB dla pliku obiektu, Skompiluj ponownie plik obiektu za pomocą [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Jeśli `filename` jest plikiem PDB dla głównego pliku wyjściowego i ten błąd wystąpił podczas przyrostowego linku, usuń plik PDB i ponownie połącz.
