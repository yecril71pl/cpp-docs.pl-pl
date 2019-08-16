---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: b793b3efa72a676b800c10b98ea06001ddcf10d5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491434"
---
# <a name="fpo"></a>.FPO

Polu. Dyrektywa FPO steruje emisją rekordów debugowania do segmentu lub sekcji. Debug $ F.

## <a name="syntax"></a>Składnia

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*<br/>
Liczba zmiennych lokalnych, nieniepodpisana wartość bitowa 32.

*cdwParams*<br/>
Rozmiar parametrów w elementach DWORD, wartość 16-bitowa bez znaku.

*cbProlog*<br/>
Liczba bajtów w kodzie prologu funkcji, 8-bitowej wartości bez znaku.

*cbRegs*<br/>
Zapisano numery rejestrów.

*fUseBP*<br/>
Wskazuje, czy rejestr EBP został przydzielony. wartość 0 lub 1.

*cbFrame*<br/>
Wskazuje typ ramki.  Aby uzyskać więcej informacji, zobacz [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
