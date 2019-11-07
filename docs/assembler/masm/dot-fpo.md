---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703793"
---
# <a name="fpo-32-bit-masm"></a>. FPO (32-bitowy MASM)

Polu. Dyrektywa FPO steruje emisją rekordów debugowania do segmentu lub sekcji. Debug $ F. (tylko 32-bitowy MASM).

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
