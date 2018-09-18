---
title: Funkcja CAtlServiceModuleT::Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b1edd5d01300324a8d24b41aa289f510cf078ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021777"
---
# <a name="catlservicemoduletstart-function"></a>Funkcja CAtlServiceModuleT::Start

Po uruchomieniu usługi `_tWinMain` wywołania `CAtlServiceModuleT::WinMain`, który z kolei wywołuje `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start` Ustawia tablicę `SERVICE_TABLE_ENTRY` struktur, które mapują poszczególnych usług dla jej funkcji uruchamiania. Ta tablica jest następnie przekazywany do funkcji Win32 API [StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera). Teoretycznie jeden plik EXE może obsługiwać wiele usług i tablicy może mieć wiele `SERVICE_TABLE_ENTRY` struktury. Obecnie jednak wygenerowane ATL usługa obsługuje tylko jedną usługę na pliku EXE. W związku z tym, tablica nie zawiera pojedynczy wpis, który zawiera nazwę usługi i `_ServiceMain` jako funkcję uruchamiania. `_ServiceMain` jest to funkcja statycznej składowej `CAtlServiceModuleT` wywołującą funkcję niestatycznego elementu członkowskiego `ServiceMain`.

> [!NOTE]
>  Niepowodzenie `StartServiceCtrlDispatcher` połączyć się z kontroli usług Menedżera (SCM) prawdopodobnie oznacza, że program nie jest uruchomiony jako usługa. W takim przypadku program wywołuje `CAtlServiceModuleT::Run` bezpośrednio, aby uruchomić program jako serwera lokalnego. Aby uzyskać więcej informacji na temat uruchamiania programu jako serwera lokalnego, zobacz [debugowania porady](../atl/debugging-tips.md).

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

