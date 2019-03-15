---
title: Funkcja CAtlServiceModuleT::ServiceMain
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 81cd8fcbdf275063b243e215301eff504a2b5cc6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811904"
---
# <a name="catlservicemoduletservicemain-function"></a>Funkcja CAtlServiceModuleT::ServiceMain

Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji w Panelu sterowania, wybierz usługę i kliknij przycisk **Start**.

Po Menedżer sterowania usługami wywołuje `ServiceMain`, usługa musi udzielić Menedżer sterowania usługami, funkcja obsługi. Ta funkcja pozwala na uzyskanie stanu usługi i przekazać szczegółowych instrukcji (na przykład wstrzymanie lub zatrzymanie) Menedżer sterowania usługami. Menedżer sterowania usługami pobiera tę funkcję, gdy usługa przekazuje `_Handler` funkcji Win32 API [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` jest funkcją statycznego elementu członkowskiego, która wywołuje funkcję niestatycznego elementu członkowskiego [obsługi](../atl/reference/catlservicemodulet-class.md#handler).)

Podczas uruchamiania usługi powinien również poinformować SCM swojego bieżącego stanu. Jest to realizowane przez przekazanie SERVICE_START_PENDING funkcji Win32 API [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` następnie wywołuje `CAtlExeModuleT::InitializeCom`, który wywołuje funkcję Win32 API [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). Domyślnie `InitializeCom` przekazuje flagę COINIT_MULTITHREADED do funkcji. Ta flaga wskazuje, że program ma być bezwątkowy serwer.

Teraz `CAtlServiceModuleT::Run` jest wywoływana w celu wykonania pracy głównego usługi. `Run` kontynuuje wykonywanie dopóki nie zostanie zatrzymana.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
