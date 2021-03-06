---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269768"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Określa, czy podpis cyfrowy obrazu binarnego musi być zaznaczone w czasie ładowania.

> **/INTEGRITYCHECK**[**:NO**]

## <a name="remarks"></a>Uwagi

W nagłówku pliku DLL lub pliku wykonywalnego ta opcja ustawia flagę, która wymaga sprawdzenia podpisu cyfrowego przez Menedżera pamięci w celu załadowania obrazu w Windows. Wersje Windows przed Windows Vista, ignorują tę flagę. Tę opcję należy ustawić dla 64-bitowych bibliotek DLL, które implementują kod trybu jądra i jest zalecana dla wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące podpisywania kodu trybu jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)
