---
title: Błąd narzędzi konsolidatora LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194749"
---
# <a name="linker-tools-error-lnk2013"></a>Błąd narzędzi konsolidatora LNK2013

przepełnienie naprawy typu naprawy. Obiekt docelowy "Nazwa symbolu" jest poza zakresem

Konsolidator nie może dopasować wymaganego adresu lub przesunięcia do podanych instrukcji, ponieważ symbol docelowy jest zbyt daleko od lokalizacji instrukcji.

Ten problem można rozwiązać przez utworzenie wielu obrazów lub użycie opcji [/Order](../../build/reference/order-put-functions-in-order.md) , aby instrukcje i cel zostały bliżej siebie.

Gdy nazwa symbolu jest symbolem zdefiniowanym przez użytkownika (a nie symbolem wygenerowanym przez kompilator), możesz również spróbować wykonać następujące czynności, aby rozwiązać ten problem:

- Zmień statyczną funkcję na niestatyczną.

- Zmień nazwę sekcji kodu zawierającej funkcję statyczną tak, aby była taka sama jak obiekt wywołujący.

Użyj `DUMPBIN /SYMBOLS`, aby sprawdzić, czy funkcja jest statyczna.
