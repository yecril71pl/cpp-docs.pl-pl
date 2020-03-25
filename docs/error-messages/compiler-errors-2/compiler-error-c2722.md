---
title: Błąd kompilatora C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 7426df1970dee58cd4363ee345e2286165e375b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202180"
---
# <a name="compiler-error-c2722"></a>Błąd kompilatora C2722

":: operator": niedozwolone polecenie po operatorze; Użyj "operator operatora"

Instrukcja `operator` ponownie definiuje `::new` lub `::delete`. Operatory `new` i `delete` są globalne, więc operator rozpoznawania zakresu (`::`) nie ma znaczenia. Usuń operator `::`.
