---
title: Błąd krytyczny ML A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317126"
---
# <a name="ml-fatal-error-a1007"></a>Błąd krytyczny ML A1007

**zbyt głęboki poziom zagnieżdżenia**

Asembler osiągnął limit zagnieżdżenia. Limit wynosi 20 poziomów, chyba że zaznaczono inaczej.

Jeden z następujących elementów został zagnieżdżony zbyt głęboko:

- Dyrektywa wysokiego poziomu, taka jak [. Jeśli](dot-if.md), [. Powtórz](dot-repeat.md)lub [. WHILE](dot-while.md).

- Definicja struktury.

- Dyrektywa zestawu warunkowego.

- Definicja procedury.

- Dyrektywa [PUSHCONTEXT](pushcontext.md) (limit wynosi 10).

- Definicja segmentu.

- Plik dołączany.

- Makro.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
