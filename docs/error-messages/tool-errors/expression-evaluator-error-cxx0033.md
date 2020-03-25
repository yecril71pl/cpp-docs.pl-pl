---
title: Błąd CXX0033 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195516"
---
# <a name="expression-evaluator-error-cxx0033"></a>Błąd CXX0033 programu Expression Evaluator

błąd w informacjach o typie OMF

Plik wykonywalny nie ma prawidłowego formatu modułu obiektów (OMF) na potrzeby debugowania.

Ten błąd jest identyczny z CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Plik wykonywalny nie został utworzony za pomocą konsolidatora wydanego za pomocą C++tej wersji wizualizacji. Ponownie połącz kod obiektu przy użyciu bieżącej wersji programu LINK. exe.

1. Plik. exe mógł zostać uszkodzony. Ponownie skompiluj i ponownie połącz program.
