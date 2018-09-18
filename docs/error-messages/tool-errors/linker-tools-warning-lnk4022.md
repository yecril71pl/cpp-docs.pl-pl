---
title: Ostrzeżenie LNK4022 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 644e7a9ba26dab15e2bfa2a269f62c04f0510180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041002"
---
# <a name="linker-tools-warning-lnk4022"></a>Ostrzeżenie LNK4022 narzędzi konsolidatora

Nie można znaleźć unikatowego dopasowania dla symbolu "symbol"

ŁĄCZE lub LIB znaleziono wiele odpowiada danym niedekorowanego symbolu i nie można rozpoznać niejednoznaczności. Nie pliku wyjściowego (.exe, .dll, .exp lub .lib) jest generowany. To ostrzeżenie jest poprzedzony jedną ostrzeżenie [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) dla każdego duplikować symboli, a na koniec następuje błąd krytyczny [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Aby uniknąć tego ostrzeżenia, należy określić symbol w formie urządzonej. Uruchom [DUMPBIN](../../build/reference/dumpbin-options.md) w obiekcie, aby wyświetlić nazwy dekorowane.