---
title: Kompilator ostrzeżenie (poziom 1) C4953 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e53808d4ad97bad4eccdf81b0a863277f8f7796
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194635"
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilator ostrzeżenie (poziom 1) C4953

> Wbudowany "*funkcja*" został wyedytowany od profilu dane zostały zebrane, dane profilu nieużywane

Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł wejściowy nie kompilowanej po `/LTCG:PGINSTRUMENT` i ma funkcję (*funkcja*), był edytowany i którym wskazany działa istniejącego testu pełnią kandydatem do wbudowanie. Jednak w wyniku o konieczności ponownego kompilowania modułu, funkcja nie będzie już kandydatem do wbudowanie.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić `/LTCG:PGINSTRUMENT`, powtórz wszystkie testu działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zamienione błąd Jeśli `/LTCG:PGOPTIMIZE` została użyta.