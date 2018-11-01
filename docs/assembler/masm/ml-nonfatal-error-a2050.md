---
title: Błąd niekrytyczny ML A2050
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439718"
---
# <a name="ml-nonfatal-error-a2050"></a>Błąd niekrytyczny ML A2050

**rzeczywiste lub nie jest dozwoloną liczbę BCD**

Liczba zmiennoprzecinkowa (rzeczywiste) lub stałej dziesiętnej kodowany plik binarny (BCD) użyto innej niż jako inicjator danych.

Wystąpił jeden z następujących czynności:

- Liczba rzeczywista lub BCD był używany w wyrażeniu.

- Liczba rzeczywista został użyty do zainicjowania dyrektywy innych niż [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), lub [tbyte —](../../assembler/masm/tbyte.md).

- BCD został użyty do zainicjowania dyrektywy innych niż `TBYTE`.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>