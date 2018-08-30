---
title: Kompilator ostrzeżenie (poziom 1) C4952 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62f4c18380d89eb516a5fa49ef63e92ab79a6f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207154"
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilator ostrzeżenie (poziom 1) C4952

> "*funkcja*": nie znaleziono danych profilowych w bazie danych programu "*pgd_file*"

Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł wejściowy nie kompilowanej po `/LTCG:PGINSTRUMENT` i ma nową funkcję (*funkcja*) istnieje.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić `/LTCG:PGINSTRUMENT`, powtórz wszystkie testu działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zamienione błąd Jeśli `/LTCG:PGOPTIMIZE` została użyta.