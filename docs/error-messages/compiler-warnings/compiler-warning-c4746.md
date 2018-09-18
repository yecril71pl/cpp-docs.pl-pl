---
title: Ostrzeżenie kompilatora C4746 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6abce7ebbcdc41effed05ccf54337e3976c34e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054873"
---
# <a name="compiler-warning-c4746"></a>Ostrzeżenie kompilatora C4746

nietrwały dostęp "\<wyrażenia >" podlega/volatile: [iso&#124;ms]; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store funkcje wewnętrzne.

C4746 jest emitowane zawsze wtedy, gdy zmienna volatile odbywa się bezpośrednio. Mają ułatwić deweloperom zidentyfikowanie, lokalizacji kodu, które dotyczą określonych model nietrwały aktualnie określone (mogą być kontrolowane za pomocą [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora). W szczególności może być pomocne w odnalezieniu generowanych przez kompilator sprzętowych barier pamięci, gdy /volatile:ms jest używany.

Funkcje wewnętrzne funkcji wewnętrznych __iso_volatile_load/store może służyć jawnie uzyskiwać dostęp do pamięci volatile bez wpływowi model nietrwały. Za pomocą funkcji wewnętrznych nie spowodują uruchomienia C4746.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.