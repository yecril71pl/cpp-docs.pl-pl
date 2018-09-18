---
title: Wydajność bibliotek wielowątkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f66aebc7b6d77e3697fabf783332a83bdd6f3fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052110"
---
# <a name="multithreaded-libraries-performance"></a>Wydajność bibliotek wielowątkowych

Jednowątkowe CRT nie jest już dostępna. W tym temacie omówiono sposób uzyskać maksymalną wydajność bibliotek wielowątkowych.

## <a name="maximizing-performance"></a>Maksymalizacja wydajności

Wydajność bibliotek wielowątkowych została ulepszona i zbliża się wydajność bibliotek wyeliminowane teraz apartamentem. W tych sytuacjach podczas jeszcze większej wydajności jest wymagany, istnieje kilka nowych funkcji.

- Blokowanie niezależnych strumienia pozwala na blokowanie strumienia, a następnie użyj [_nolock — funkcje](../c-runtime-library/nolock-functions.md) , uzyskać dostęp do strumienia bezpośrednio. Dzięki temu użycia blokady, aby być podciągnięta poza krytyczne pętli.

- Ustawienia regionalne dla wątku zmniejsza koszty dostępu ustawień regionalnych dla scenariusze wielowątkowe (zobacz [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Funkcje zależne od ustawień regionalnych (przy użyciu nazwy kończące się na _l) przyjmują ustawień regionalnych jako parametru, usuwając znaczne ograniczenie kosztów (na przykład [printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Optymalizacja pod kątem typowych strony kodowe zmniejszyć koszt wiele operacji krótki.

- Definiowanie [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) wymusza wszystkie operacje We/Wy przyjęto założenie modelu jednowątkowe operacji We/Wy i używać formy _nolock — funkcje. Dzięki temu wysoce I/O-based aplikacje jednowątkowe w celu uzyskania lepszej wydajności.

- Narażenia uchwyt sterty CRT umożliwia włączenie Windows niskiego fragmentację sterty (LFH) na stercie CRT, która może znacznie poprawić wydajność w scenariuszach wysoce skalowaną.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)