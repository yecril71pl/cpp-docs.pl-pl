---
title: Tworzenie skryptów dla Rejestrator ALT
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: e1a0b66e673fcefd0b75683ef75247a388217361
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295516"
---
# <a name="creating-registrar-scripts"></a>Tworzenie skryptów rejestratora

Skryptu rejestratora zapewnia oparte na danych, a nie na podstawie interfejsu API, dostęp do rejestru systemowego. Dostępu opartej na danych jest zazwyczaj bardziej efektywne, ponieważ zajmuje tylko jeden lub dwa wiersze w skrypcie, aby dodać klucz rejestru.

[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skryptu rejestratora dla modelu COM serwera. Ten skrypt można znaleźć w pliku .rgs skojarzone z obiektem.

Aparat skryptów Rejestrator ALT przetwarza skryptu rejestratora w czasie wykonywania. ATL automatycznie wywołuje aparat skryptu podczas instalacji serwera.

W tym artykule omówiono następujące tematy związane z skrypty rejestratora:

- [Opis składni formularza Backus Nauer (BNF)](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [Opis drzew analizy](../atl/understanding-parse-trees.md)

- [Przykłady skryptów rejestru](../atl/registry-scripting-examples.md)

- [Używanie wymiennych parametrów (preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Wywoływanie skryptów](../atl/invoking-scripts.md)

## <a name="see-also"></a>Zobacz także

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)
