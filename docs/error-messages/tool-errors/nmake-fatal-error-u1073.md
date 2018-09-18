---
title: Błąd krytyczny NMAKE U1073 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c309ed94cd1c984406e0d21f0139e35c6e41d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053946"
---
# <a name="nmake-fatal-error-u1073"></a>Błąd krytyczny NMAKE U1073

Nie wiem, jak "targetname"

Określony obiekt docelowy nie istnieje i nie ma polecenia do wykonania lub aby zastosować regułę wnioskowania.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Sprawdź pisownię nazwy docelowego.

1. Jeśli *targetname* pseudotarget, jest ono określone jako element docelowy inny opis bloku.

1. Jeśli *targetname* jest wywołanie makra, pamiętaj, że nie jest powiększony na pusty ciąg.