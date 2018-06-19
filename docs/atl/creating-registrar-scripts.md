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
ms.openlocfilehash: e140e66ee24d8333d25c0c2942924c7a9db4965b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354436"
---
# <a name="creating-registrar-scripts"></a>Tworzenie skryptów rejestratora
Skryptu rejestratora zapewnia oparte na danych, a nie obsługiwanego interfejsu API, dostępu do rejestru systemowego. Danymi dostępu jest zazwyczaj bardziej wydajne, ponieważ trwa tylko jeden lub dwa wiersze w skrypcie, aby dodać klucz w rejestrze.  
  
 [Kreator formantu ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skryptu rejestratora dla modelu COM serwera. Ten skrypt można znaleźć w pliku .rgs skojarzone z obiektem.  
  
 Aparat skryptu Rejestrator ALT przetwarza skryptu rejestratora, w czasie wykonywania. ATL automatycznie wywołuje aparatu skryptu podczas instalacji serwera.  
  
 W tym artykule omówiono następujące tematy związane z skrypty rejestratora:  
  
-   [Opis składni formularza Backus Nauer (BNF)](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [Opis drzew analizy](../atl/understanding-parse-trees.md)  
  
-   [Przykłady skryptów rejestru](../atl/registry-scripting-examples.md)  
  
-   [Używanie wymiennych parametrów (preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [Wywoływanie skryptów](../atl/invoking-scripts.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)

