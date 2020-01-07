---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: ec08be4941f81abed55420884b34dc817caf3f13
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317737"
---
# <a name="fpo-32-bit-masm"></a>. FPO (32-bitowy MASM)

**. Dyrektywa FPO** steruje emisją rekordów debugowania do segmentu lub sekcji. Debug $ F. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **. FPO** (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*\
Liczba zmiennych lokalnych, nieniepodpisana wartość bitowa 32.

*cdwParams*\
Rozmiar parametrów w elementach DWORD, wartość 16-bitowa bez znaku.

*cbProlog*\
Liczba bajtów w kodzie prologu funkcji, 8-bitowej wartości bez znaku.

*cbRegs*\
Zapisano numery rejestrów.

*fUseBP*\
Wskazuje, czy rejestr EBP został przydzielony. wartość 0 lub 1.

*cbFrame*\
Wskazuje typ ramki.  Aby uzyskać więcej informacji, zobacz [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
