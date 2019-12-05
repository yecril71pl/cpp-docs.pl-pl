---
title: Błąd niekrytyczny ML A2050
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 15c6449ff4207c92dee28120d4f61be641cf01c8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856580"
---
# <a name="ml-nonfatal-error-a2050"></a>Błąd niekrytyczny ML A2050

**Liczba rzeczywistych lub BCD nie jest dozwolona**

Stała liczba zmiennoprzecinkowa (rzeczywista) lub zakodowana cyfra dziesiętna (BCD) została użyta inna niż inicjator danych.

Wystąpił jeden z następujących:

- W wyrażeniu użyto liczby rzeczywistej lub BCD.

- Liczba rzeczywista została użyta do zainicjowania dyrektywy innej niż [DWORD](../../assembler/masm/dword.md), [Qword](../../assembler/masm/qword.md)lub [TBYTE](../../assembler/masm/tbyte.md).

- Wykryto BCD do zainicjowania dyrektywy innej niż `TBYTE`.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>