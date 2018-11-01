---
title: Błąd krytyczny NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582276"
---
# <a name="nmake-fatal-error-u1073"></a>Błąd krytyczny NMAKE U1073

Nie wiem, jak "targetname"

Określony obiekt docelowy nie istnieje i nie ma polecenia do wykonania lub aby zastosować regułę wnioskowania.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Sprawdź pisownię nazwy docelowego.

1. Jeśli *targetname* pseudotarget, jest ono określone jako element docelowy inny opis bloku.

1. Jeśli *targetname* jest wywołanie makra, pamiętaj, że nie jest powiększony na pusty ciąg.