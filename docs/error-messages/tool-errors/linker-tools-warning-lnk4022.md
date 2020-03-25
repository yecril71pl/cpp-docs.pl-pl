---
title: Ostrzeżenie LNK4022 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194190"
---
# <a name="linker-tools-warning-lnk4022"></a>Ostrzeżenie LNK4022 narzędzi konsolidatora

nie można znaleźć unikatowego dopasowania dla symbolu "symbol"

LINK lub biblioteka LIB znalazła wiele dopasowań dla danego niedekoracyjnego symbolu i nie może rozpoznać niejednoznaczności. Nie jest tworzony plik wyjściowy (exe, DLL,. EXP lub. lib). Po tym ostrzeżeniu następuje jedno ostrzeżenie [LNK4002 narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) dla każdego zduplikowanego symbolu i ostatecznie następuje błąd krytyczny [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Aby uniknąć tego ostrzeżenia, należy określić symbol w postaci dekoracyjnej. Uruchom [polecenia DUMPBIN](../../build/reference/dumpbin-options.md) na obiekcie, aby zobaczyć dekoracyjne nazwy.
