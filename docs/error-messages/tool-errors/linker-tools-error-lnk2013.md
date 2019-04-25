---
title: Błąd narzędzi konsolidatora LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299071"
---
# <a name="linker-tools-error-lnk2013"></a>Błąd narzędzi konsolidatora LNK2013

przepełnienie naprawy typ naprawy. Element docelowy "symbol name" jest poza zakresem

Konsolidator nie pasują niezbędne adres lub przesunięcie do podanej instrukcji, ponieważ symbol docelowy jest zbyt daleko od lokalizacji instrukcji.

Ten problem można rozwiązać przez utworzenie wielu obrazów lub za pomocą [/ORDER](../../build/reference/order-put-functions-in-order.md) opcja tak instrukcji i docelowy są ze sobą bliżej.

Gdy nazwa symbolu jest symbol zdefiniowany przez użytkownika (i nie symbol generowanych przez kompilator), możesz wypróbować następujące czynności, aby naprawić błąd:

- Zmienić statyczne funkcji niestatycznych.

- Zmień nazwę sekcji kodu, zawierającej funkcję statyczną, aby była taka sama jak obiekt wywołujący.

Użyj `DUMPBIN /SYMBOLS`, aby sprawdzić, czy funkcja jest statyczne.