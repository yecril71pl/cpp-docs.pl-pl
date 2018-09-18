---
title: Błąd kompilatora C2097 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021866"
---
# <a name="compiler-error-c2097"></a>Błąd kompilatora C2097

Niedozwolona Inicjalizacja

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Inicjowanie zmiennej przy użyciu wartości stałymi.

1. Inicjalizacja Krótki adres długi adres.

1. Inicjowanie lokalnych struktura, Unia lub tablicy z wyrażeniem stałymi podczas kompilowania za pomocą **/Za**.

1. Inicjalizacja za pomocą wyrażenia zawierającego operatora przecinka.

1. Inicjalizacja z wyrażeniem, które nie jest ani stałe, ani symboliczne.