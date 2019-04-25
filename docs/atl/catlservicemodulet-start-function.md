---
title: Funkcja CAtlServiceModuleT::Start
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 204d02a1122ee78b38850bedae5f98b1f338ab1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250748"
---
# <a name="catlservicemoduletstart-function"></a>Funkcja CAtlServiceModuleT::Start

Po uruchomieniu usługi `_tWinMain` wywołania `CAtlServiceModuleT::WinMain`, który z kolei wywołuje `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start` Ustawia tablicę `SERVICE_TABLE_ENTRY` struktur, które mapują poszczególnych usług dla jej funkcji uruchamiania. Ta tablica jest następnie przekazywany do funkcji Win32 API [StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera). Teoretycznie jeden plik EXE może obsługiwać wiele usług i tablicy może mieć wiele `SERVICE_TABLE_ENTRY` struktury. Obecnie jednak wygenerowane ATL usługa obsługuje tylko jedną usługę na pliku EXE. W związku z tym, tablica nie zawiera pojedynczy wpis, który zawiera nazwę usługi i `_ServiceMain` jako funkcję uruchamiania. `_ServiceMain` jest to funkcja statycznej składowej `CAtlServiceModuleT` wywołującą funkcję niestatycznego elementu członkowskiego `ServiceMain`.

> [!NOTE]
>  Niepowodzenie `StartServiceCtrlDispatcher` połączyć się z kontroli usług Menedżera (SCM) prawdopodobnie oznacza, że program nie jest uruchomiony jako usługa. W takim przypadku program wywołuje `CAtlServiceModuleT::Run` bezpośrednio, aby uruchomić program jako serwera lokalnego. Aby uzyskać więcej informacji na temat uruchamiania programu jako serwera lokalnego, zobacz [debugowania porady](../atl/debugging-tips.md).

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
