---
title: Tworzenie skryptów dla Rejestrator ALT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abffe3c8d0a107c48c3a14a9bf584122229ad3b7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767263"
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

## <a name="see-also"></a>Zobacz też

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)

