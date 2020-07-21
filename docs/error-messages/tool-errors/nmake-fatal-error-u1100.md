---
title: Błąd krytyczny NMAKE U1100
description: Opis przyczyn wystąpienia błędu krytycznego programu Microsoft NMAKE U1100.
ms.date: 07/17/2020
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: f908514469a6c9fdb53df3b2bded1b30bddc5a41
ms.sourcegitcommit: 00af3df3331854b23693ee844e5e7c10c8b05a90
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86491391"
---
# <a name="nmake-fatal-error-u1100"></a>Błąd krytyczny NMAKE U1100

> makro "*Macro-Name*" jest niedozwolone w kontekście reguły wsadowej "*Rule-Name*"

NMAKE generuje ten błąd, gdy blok poleceń reguły trybu wsadowego bezpośrednio lub pośrednio odwołuje się do specjalnego makra pliku, który nie jest `$<` .

`$<`jest jedynym dozwolonym makrem dla reguł trybu wsadowego.

Aby uzyskać więcej informacji na temat makr NMAKE w regułach usługi Batch, zobacz [specjalne makra NMAKE](../../build/reference/special-nmake-macros.md).
