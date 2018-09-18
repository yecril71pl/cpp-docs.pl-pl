---
title: Błąd narzędzi konsolidatora LNK2027 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 022e363af575e29e3085dcaec21257fa7e4ab5f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116850"
---
# <a name="linker-tools-error-lnk2027"></a>Błąd narzędzi konsolidatora LNK2027

Moduł nierozpoznanego odwołania "module"

Plik przekazywane do konsolidatora zależny od modułu, który nie został określony za pomocą **assemblymodule** ani przekazywane bezpośrednio do konsolidatora.

Aby rozwiązać LNK2027, wykonaj jedną z następujących czynności:

- Nie przekazuj do konsolidatora pliku który zawiera zależność modułu.

- Określ moduł za pomocą **assemblymodule**.

- Jeśli moduł .netmodule bezpieczne, należy przekazać modułu bezpośrednio do konsolidatora.

Aby uzyskać więcej informacji, zobacz [assemblymodule (Dodaj moduł MSIL do zestawu)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) i [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).