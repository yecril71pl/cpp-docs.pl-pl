---
title: Błąd niekrytyczny ML A2050 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680674"
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