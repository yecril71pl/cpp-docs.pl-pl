---
title: Tworzenie skryptów dla Rejestrator ALT
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707056"
---
# <a name="creating-registrar-scripts"></a>Tworzenie skryptów rejestratora

Skryptu rejestratora zapewnia oparte na danych, a nie na podstawie interfejsu API, dostęp do rejestru systemowego. Dostępu opartej na danych jest zazwyczaj bardziej efektywne, ponieważ zajmuje tylko jeden lub dwa wiersze w skrypcie, aby dodać klucz rejestru.

[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skryptu rejestratora dla modelu COM serwera. Ten skrypt można znaleźć w pliku .rgs skojarzone z obiektem.

Aparat skryptów Rejestrator ALT przetwarza skryptu rejestratora w czasie wykonywania. ATL automatycznie wywołuje aparat skryptu podczas instalacji serwera.

W tym artykule omówiono następujące tematy związane z skrypty rejestratora:

- [Opis składni formularza (BNF) notacji Backusa-Naura](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [Opis drzew analizy](../atl/understanding-parse-trees.md)

- [Przykłady skryptów rejestru](../atl/registry-scripting-examples.md)

- [Używanie wymiennych parametrów (preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Wywoływanie skryptów](../atl/invoking-scripts.md)

## <a name="see-also"></a>Zobacz także

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)
