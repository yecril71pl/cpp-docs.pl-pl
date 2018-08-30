---
title: Funkcja CAtlServiceModuleT::ServiceMain | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs:
- C++
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 746a7c9d95d629329fb0f47705f61c5f0753a662
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203685"
---
# <a name="catlservicemoduletservicemain-function"></a>Funkcja CAtlServiceModuleT::ServiceMain
Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji w Panelu sterowania, wybierz usługę i kliknij przycisk **Start**.  
  
 Po Menedżer sterowania usługami wywołuje `ServiceMain`, usługa musi udzielić Menedżer sterowania usługami, funkcja obsługi. Ta funkcja pozwala na uzyskanie stanu usługi i przekazać szczegółowych instrukcji (na przykład wstrzymanie lub zatrzymanie) Menedżer sterowania usługami. Menedżer sterowania usługami pobiera tę funkcję, gdy usługa przekazuje `_Handler` funkcji Win32 API [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` jest funkcją statycznego elementu członkowskiego, która wywołuje funkcję niestatycznego elementu członkowskiego [obsługi](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Podczas uruchamiania usługi powinien również poinformować SCM swojego bieżącego stanu. Jest to realizowane przez przekazanie SERVICE_START_PENDING funkcji Win32 API [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).  
  
 `ServiceMain` następnie wywołuje `CAtlExeModuleT::InitializeCom`, który wywołuje funkcję Win32 API [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). Domyślnie `InitializeCom` przekazuje flagę COINIT_MULTITHREADED do funkcji. Ta flaga wskazuje, że program ma być bezwątkowy serwer.  
  
 Teraz `CAtlServiceModuleT::Run` jest wywoływana w celu wykonania pracy głównego usługi. `Run` kontynuuje wykonywanie dopóki nie zostanie zatrzymana.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

