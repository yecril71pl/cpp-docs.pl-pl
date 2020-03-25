---
title: Ostrzeżenie BSCMAKE BK4502
ms.date: 11/04/2016
f1_keywords:
- BK4502
helpviewer_keywords:
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
ms.openlocfilehash: 1c5204239909e579fa93006e245e3841b7fb64eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197460"
---
# <a name="bscmake-warning-bk4502"></a>Ostrzeżenie BSCMAKE BK4502

Cięcie. Plik SBR "filename" nie znajduje się w pliku

Plik o zerowej długości. sbr, który nie był pierwotnie częścią pliku BSC, został określony podczas aktualizacji.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Określono nieprawidłową nazwę pliku.

1. Plik został usunięty. (Błąd [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) wyników).

1. Plik jest uszkodzony, wymagając BSCMAKE do wykonania pełnej kompilacji.
