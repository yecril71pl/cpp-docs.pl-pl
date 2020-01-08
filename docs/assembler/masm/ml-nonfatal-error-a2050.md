---
title: Błąd niekrytyczny ML A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316983"
---
# <a name="ml-nonfatal-error-a2050"></a>Błąd niekrytyczny ML A2050

**Liczba rzeczywistych lub BCD nie jest dozwolona**

Stała liczba zmiennoprzecinkowa (rzeczywista) lub zakodowana cyfra dziesiętna (BCD) została użyta inna niż inicjator danych.

Wystąpił jeden z następujących:

- W wyrażeniu użyto liczby rzeczywistej lub BCD.

- Liczba rzeczywista została użyta do zainicjowania dyrektywy innej niż [DWORD](dword.md), [Qword](qword.md)lub [TBYTE](tbyte.md).

- Wykryto BCD do zainicjowania dyrektywy innej niż `TBYTE`.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
