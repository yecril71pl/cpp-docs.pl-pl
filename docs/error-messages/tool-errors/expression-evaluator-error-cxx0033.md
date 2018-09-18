---
title: Błąd ewaluatora wyrażeń CXX0033 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f37b53c30d36a43d339132bfd9baca3e5ec70c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057201"
---
# <a name="expression-evaluator-error-cxx0033"></a>Błąd CXX0033 programu Expression Evaluator

Błąd w informacje o typie OMF

Plik wykonywalny nie miał format modułu prawidłowy obiekt (OMF) do debugowania.

Ten błąd jest taka sama jak CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Plik wykonywalny nie został utworzony za pomocą konsolidatora ogólnie dostępnych w tej wersji programu Visual C++. Połącz ponownie kod obiektu przy użyciu bieżącej wersji programu LINK.exe.

1. Plik .exe mogła ulec uszkodzeniu. Należy ponownie skompilować i ponownie połączyć program.