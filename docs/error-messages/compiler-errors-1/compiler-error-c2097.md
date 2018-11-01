---
title: Błąd kompilatora C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676593"
---
# <a name="compiler-error-c2097"></a>Błąd kompilatora C2097

Niedozwolona Inicjalizacja

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Inicjowanie zmiennej przy użyciu wartości stałymi.

1. Inicjalizacja Krótki adres długi adres.

1. Inicjowanie lokalnych struktura, Unia lub tablicy z wyrażeniem stałymi podczas kompilowania za pomocą **/Za**.

1. Inicjalizacja za pomocą wyrażenia zawierającego operatora przecinka.

1. Inicjalizacja z wyrażeniem, które nie jest ani stałe, ani symboliczne.