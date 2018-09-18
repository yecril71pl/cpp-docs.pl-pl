---
title: Błąd narzędzi konsolidatora LNK2013 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041743"
---
# <a name="linker-tools-error-lnk2013"></a>Błąd narzędzi konsolidatora LNK2013

przepełnienie naprawy typ naprawy. Element docelowy "symbol name" jest poza zakresem

Konsolidator nie pasują niezbędne adres lub przesunięcie do podanej instrukcji, ponieważ symbol docelowy jest zbyt daleko od lokalizacji instrukcji.

Ten problem można rozwiązać przez utworzenie wielu obrazów lub za pomocą [/ORDER](../../build/reference/order-put-functions-in-order.md) opcja tak instrukcji i docelowy są ze sobą bliżej.

Gdy nazwa symbolu jest symbol zdefiniowany przez użytkownika (i nie symbol generowanych przez kompilator), możesz wypróbować następujące czynności, aby naprawić błąd:

- Zmienić statyczne funkcji niestatycznych.

- Zmień nazwę sekcji kodu, zawierającej funkcję statyczną, aby była taka sama jak obiekt wywołujący.

Użyj `DUMPBIN /SYMBOLS`, aby sprawdzić, czy funkcja jest statyczne.