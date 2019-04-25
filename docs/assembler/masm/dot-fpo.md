---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204061"
---
# <a name="fpo"></a>.FPO

. Dyrektywa FPO steruje emisji rekordów debugowania do sekcji lub .debug$ F segmentu.

## <a name="syntax"></a>Składnia

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*<br/>
Liczba zmiennych lokalnych, wartością bez znaku 32-bitowych.

*cdwParams*<br/>
Rozmiar parametrów w dane DWORD, wartością bez znaku 16-bitowych.

*cbProlog*<br/>
Liczba bajtów w kodzie prologu funkcji wartością bez znaku 8-bitową.

*cbRegs*<br/>
Liczba rejestrów zapisane.

*fUseBP*<br/>
Wskazuje, czy został przydzielony do rejestru EBP. 0 lub 1.

*cbFrame*<br/>
Wskazuje typ ramki.  Zobacz [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>