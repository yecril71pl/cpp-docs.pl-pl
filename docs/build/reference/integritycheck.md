---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b3f6622e3628db53c363b239c59accd94f708ab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617277"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Określa, czy podpis cyfrowy obrazu binarnego musi być zaznaczone w czasie ładowania.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

W nagłówku pliku DLL lub pliku wykonywalnego ta opcja ustawia flagę, która wymaga sprawdzenia podpisu cyfrowego przez Menedżera pamięci w celu załadowania obrazu w Windows. Wersje Windows przed Windows Vista, ignorują tę flagę. Tę opcję należy ustawić dla 64-bitowych bibliotek DLL, które implementują kod trybu jądra i jest zalecana dla wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące podpisywania kodu trybu jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](../../build/reference/editbin-options.md)
