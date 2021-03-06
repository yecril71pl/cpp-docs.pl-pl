---
title: Błąd niekrytyczny ML A2008
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 79448f9358ffd422b8b25a69ac2b83693e58560e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318049"
---
# <a name="ml-nonfatal-error-a2008"></a>Błąd niekrytyczny ML A2008

**Błąd składniowy:**

Token w bieżącej lokalizacji spowodował błąd składniowy.

Może wystąpić jedna z następujących czynności:

- Prefiks kropki został dodany do lub pominięty z dyrektywy.

- Jako identyfikator użyto słowa zastrzeżonego (takiego jak **C** lub **size**).

- Użyto instrukcji, która była niedostępna z bieżącym procesorem lub wybranym współprocesorem.

- Porównanie operatora czasu wykonywania (takiego jak `==`) zostało użyte w instrukcji zestawu warunkowego zamiast operatora relacyjnego (na przykład [EQ](operator-eq.md)).

- Instrukcja lub dyrektywa otrzymała zbyt mało argumentów operacji.

- Użyto przestarzałej dyrektywy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
