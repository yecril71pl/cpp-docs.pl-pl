---
title: Błąd narzędzi konsolidatora LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 0c531f70f98a017e8b75cceddc684f99d33bc554
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194602"
---
# <a name="linker-tools-error-lnk2027"></a>Błąd narzędzi konsolidatora LNK2027

nierozpoznane odwołanie do modułu "module"

Plik przesłany do konsolidatora ma zależność od modułu, który nie został określony przy użyciu **/ASSEMBLYMODULE** ani nie został przekazano bezpośrednio do konsolidatora.

Aby rozwiązać LNK2027, wykonaj jedną z następujących czynności:

- Nie przekazuj do konsolidatora plik, który ma zależność modułu.

- Określ moduł z **/ASSEMBLYMODULE**.

- Jeśli moduł jest bezpiecznym modułem sieci, Przekaż moduł bezpośrednio do konsolidatora.

Aby uzyskać więcej informacji, zobacz [/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) i [pliki. module jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).
