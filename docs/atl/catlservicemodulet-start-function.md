---
title: 'Funkcja CAtlServiceModuleT:: Start — funkcja'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491665"
---
# <a name="catlservicemoduletstart-function"></a>Funkcja CAtlServiceModuleT:: Start — funkcja

Gdy usługa jest uruchomiona, `_tWinMain` wywołuje `CAtlServiceModuleT::WinMain` `CAtlServiceModuleT::Start`, co z kolei wywołuje.

`CAtlServiceModuleT::Start`konfiguruje tablicę `SERVICE_TABLE_ENTRY` struktur, które mapują poszczególne usługi do funkcji uruchamiania. Ta tablica jest następnie przenoszona do funkcji Win32 API, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). Teoretycznie jeden plik exe może obsłużyć wiele usług, a tablica może `SERVICE_TABLE_ENTRY` mieć wiele struktur. Obecnie jednak usługa wygenerowała ATL obsługuje tylko jedną usługę dla każdego pliku EXE. W związku z tym tablica zawiera pojedynczy wpis zawierający nazwę usługi i `_ServiceMain` funkcję uruchamiania. `_ServiceMain`jest statyczną funkcją `CAtlServiceModuleT` składową, która wywołuje niestatyczną `ServiceMain`funkcję członkowską.

> [!NOTE]
>  `StartServiceCtrlDispatcher` Niepowodzenie połączenia z menedżerem sterowania usługami (SCM) prawdopodobnie oznacza, że program nie jest uruchomiony jako usługa. W takim przypadku program wywołuje `CAtlServiceModuleT::Run` się bezpośrednio, aby program mógł zostać uruchomiony jako serwer lokalny. Aby uzyskać więcej informacji na temat uruchamiania programu jako serwera lokalnego, zobacz [porady dotyczące debugowania](../atl/debugging-tips.md).

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[Funkcja CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)
