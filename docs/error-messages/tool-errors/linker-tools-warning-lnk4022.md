---
title: Ostrzeżenie LNK4022 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 1c9ccfe6ca201ae4deed69c7d01429c67cce4bda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298469"
---
# <a name="linker-tools-warning-lnk4022"></a>Ostrzeżenie LNK4022 narzędzi konsolidatora

Nie można znaleźć unikatowego dopasowania dla symbolu "symbol"

ŁĄCZE lub LIB znaleziono wiele odpowiada danym niedekorowanego symbolu i nie można rozpoznać niejednoznaczności. Nie pliku wyjściowego (.exe, .dll, .exp lub .lib) jest generowany. To ostrzeżenie jest poprzedzony jedną ostrzeżenie [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) dla każdego duplikować symboli, a na koniec następuje błąd krytyczny [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Aby uniknąć tego ostrzeżenia, należy określić symbol w formie urządzonej. Uruchom [DUMPBIN](../../build/reference/dumpbin-options.md) w obiekcie, aby wyświetlić nazwy dekorowane.