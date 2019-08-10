---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3bdb6af98aa71fef3d4af24091dc7463d917ce15
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915962"
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
Wskazuje typ ramki.  Aby uzyskać więcej informacji, zobacz [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
