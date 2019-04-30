---
title: Błąd CXX0033 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397058"
---
# <a name="expression-evaluator-error-cxx0033"></a>Błąd CXX0033 programu Expression Evaluator

Błąd w informacje o typie OMF

Plik wykonywalny nie miał format modułu prawidłowy obiekt (OMF) do debugowania.

Ten błąd jest taka sama jak CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Plik wykonywalny nie został utworzony za pomocą konsolidatora ogólnie dostępnych w tej wersji programu Visual C++. Połącz ponownie kod obiektu przy użyciu bieżącej wersji programu LINK.exe.

1. Plik .exe mogła ulec uszkodzeniu. Należy ponownie skompilować i ponownie połączyć program.