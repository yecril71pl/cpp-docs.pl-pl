---
title: . FPO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be5e20716ff414eea3eddc8490e2a3f82adeb777
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687748"
---
# <a name="fpo"></a>.FPO

. Dyrektywa FPO steruje emisji rekordów debugowania do sekcji lub .debug$ F segmentu.

## <a name="syntax"></a>Składnia

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*,  *cbFrame*)

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