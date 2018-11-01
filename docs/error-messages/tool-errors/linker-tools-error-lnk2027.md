---
title: Błąd narzędzi konsolidatora LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545902"
---
# <a name="linker-tools-error-lnk2027"></a>Błąd narzędzi konsolidatora LNK2027

Moduł nierozpoznanego odwołania "module"

Plik przekazywane do konsolidatora zależny od modułu, który nie został określony za pomocą **assemblymodule** ani przekazywane bezpośrednio do konsolidatora.

Aby rozwiązać LNK2027, wykonaj jedną z następujących czynności:

- Nie przekazuj do konsolidatora pliku który zawiera zależność modułu.

- Określ moduł za pomocą **assemblymodule**.

- Jeśli moduł .netmodule bezpieczne, należy przekazać modułu bezpośrednio do konsolidatora.

Aby uzyskać więcej informacji, zobacz [assemblymodule (Dodaj moduł MSIL do zestawu)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) i [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).