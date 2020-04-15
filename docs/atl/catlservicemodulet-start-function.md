---
title: CAtlServiceModuleT::Funkcja uruchamiania
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317278"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Funkcja uruchamiania

Po uruchomieniu usługi `_tWinMain` wywołania `CAtlServiceModuleT::WinMain`, co `CAtlServiceModuleT::Start`z kolei wywołuje .

`CAtlServiceModuleT::Start`konfiguruje tablicę `SERVICE_TABLE_ENTRY` struktur, które mapują każdą usługę do jej funkcji uruchamiania. Ta tablica jest następnie przekazywana do funkcji interfejsu API Win32, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). Teoretycznie jeden EXE może obsługiwać wiele usług, a tablica może mieć wiele `SERVICE_TABLE_ENTRY` struktur. Obecnie jednak usługa generowana przez ATL obsługuje tylko jedną usługę na exe. W związku z tym tablica ma pojedynczy `_ServiceMain` wpis, który zawiera nazwę usługi i jako funkcję uruchamiania. `_ServiceMain`jest statyczną funkcją `CAtlServiceModuleT` elementu członkowskiego, która wywołuje `ServiceMain`niestatyczną funkcję elementu członkowskiego, .

> [!NOTE]
> Niepowodzenie `StartServiceCtrlDispatcher` połączenia z menedżerem sterowania usługami (SCM) prawdopodobnie oznacza, że program nie jest uruchomiony jako usługa. W takim przypadku program `CAtlServiceModuleT::Run` wywołuje bezpośrednio, aby program mógł działać jako serwer lokalny. Aby uzyskać więcej informacji na temat uruchamiania programu jako serwera lokalnego, zobacz [Wskazówki dotyczące debugowania](../atl/debugging-tips.md).

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
