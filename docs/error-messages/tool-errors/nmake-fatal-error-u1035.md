---
title: Błąd krytyczny NMAKE U1035 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019864"
---
# <a name="nmake-fatal-error-u1035"></a>Błąd krytyczny NMAKE U1035

Błąd składniowy: oczekiwano ":" lub "=" separator

Albo dwukropka (**:**) lub znak równości (**=**) był oczekiwany.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Dwukropek nie korzystał z obiektu docelowego.

1. Dwukropek i brak miejsca (na przykład a:), a następnie element docelowy jedną literę. NMAKE interpretuje ją jako specyfikację dysku.

1. Dwukropek nie korzystał z reguły wnioskowania.

1. Znak równości nie nastąpiła definicji makra.

1. Znak, a następnie kreski ułamkowej odwróconej (**\\**) który został użyty do kontynuowania polecenia do nowego wiersza.

1. Pojawiły się ciąg, który nie korzystał z dowolnej reguły składni NMAKE.

1. Pliku reguł programu make został sformatowany przy użyciu edytora tekstu.