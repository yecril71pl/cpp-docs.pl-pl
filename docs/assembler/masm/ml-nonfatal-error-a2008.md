---
title: Błąd niekrytyczny ML A2008
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 192d82186a58d4e6b534ab5ec65b696d4d7ce3ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856756"
---
# <a name="ml-nonfatal-error-a2008"></a>Błąd niekrytyczny ML A2008

**Błąd składniowy:**

Token w bieżącej lokalizacji spowodował błąd składniowy.

Może wystąpić jedna z następujących czynności:

- Prefiks kropki został dodany do lub pominięty z dyrektywy.

- Jako identyfikator użyto słowa zastrzeżonego (takiego jak **C** lub **size**).

- Użyto instrukcji, która była niedostępna z bieżącym procesorem lub wybranym współprocesorem.

- Porównanie operatora czasu wykonywania (takiego jak `==`) zostało użyte w instrukcji zestawu warunkowego zamiast operatora relacyjnego (na przykład [EQ](../../assembler/masm/operator-eq.md)).

- Instrukcja lub dyrektywa otrzymała zbyt mało argumentów operacji.

- Użyto przestarzałej dyrektywy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>