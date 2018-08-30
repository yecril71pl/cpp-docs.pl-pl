---
title: Kompilator ostrzeżenie (poziom 1) C4951 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204238"
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilator ostrzeżenie (poziom 1) C4951

> "*funkcja*" został wyedytowany od profilu dane zostały zebrane, nieużywane dane profilu funkcji

Funkcja został zmodyfikowany w danych wejściowych modułu [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), dzięki czemu dane profilu są obecnie nieprawidłowe. Moduł wejściowy został ponownie kompilowana po **pginstrument** i ma funkcję (*funkcja*) przy użyciu różnych przepływu sterowania niż w module w momencie **pginstrument**  operacji.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić **pginstrument**, powtórz wszystkie testu działa, a następnie uruchom **/LTCG:PGOPTIMIZE**.

To ostrzeżenie zostanie zamienione błąd Jeśli **/LTCG:PGOPTIMIZE** została użyta.