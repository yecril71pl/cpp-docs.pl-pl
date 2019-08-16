---
title: 'Funkcja CAtlServiceModuleT:: ServiceMain — funkcja'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491723"
---
# <a name="catlservicemoduletservicemain-function"></a>Funkcja CAtlServiceModuleT:: ServiceMain — funkcja

Wywołania `ServiceMain` Menedżera sterowania usługami (SCM) po otwarciu aplikacji panelu sterowania wybierz usługę, a następnie kliknij przycisk **Uruchom**.

Po wywołaniach `ServiceMain`SCM usługa musi udzielić funkcji programu obsługi SCM. Ta funkcja umożliwia menedżerowi SCM uzyskanie stanu usługi i przekazywanie określonych instrukcji (takich jak Wstrzymywanie lub zatrzymywanie). Menedżer SCM otrzymuje tę funkcję, gdy usługa przejdzie `_Handler` do funkcji Win32 API, [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw). (`_Handler` to statyczna funkcja członkowska, która wywołuje [procedurę obsługi](../atl/reference/catlservicemodulet-class.md#handler)niestatycznej funkcji członkowskiej).

Podczas uruchamiania usługa powinna również poinformować menedżer SCM o jego bieżącym stanie. Robi to poprzez przekazywanie SERVICE_START_PENDING do funkcji Win32 API, [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain`następnie wywołuje `CAtlExeModuleT::InitializeCom`metodę, która wywołuje funkcję Win32 API [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex). Domyślnie `InitializeCom` przekazuje flagę COINIT_MULTITHREADED do funkcji. Ta flaga wskazuje, że program ma być serwerem wolnych wątków.

`CAtlServiceModuleT::Run` Teraz jest wywoływana w celu wykonania głównej pracy usługi. `Run`kontynuuje wykonywanie, dopóki usługa nie zostanie zatrzymana.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[Funkcja CAtlServiceModuleT:: ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
