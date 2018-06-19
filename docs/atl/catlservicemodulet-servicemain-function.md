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
ms.openlocfilehash: 9936090793890b1e33f0d5e29787d65f378afa84
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355577"
---
# <a name="catlservicemoduletservicemain-function"></a>Funkcja CAtlServiceModuleT::ServiceMain
Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji usługi w Panelu sterowania, wybierz usługę i kliknij przycisk **Start**.  
  
 Po SCM wywołuje `ServiceMain`, usługa musi nadać SCM funkcji obsługi. Ta funkcja umożliwia SCM uzyskać stanu usługi i podaj szczegółowe instrukcje (na przykład wstrzymanie lub zatrzymanie). Menedżer sterowania usługami pobiera tej funkcji, gdy usługa przekazuje **_Handler** funkcji Win32 API [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (**_Handler** jest funkcją statyczny element członkowski, który wywołuje funkcję niestatycznego elementu członkowskiego [obsługi](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Podczas uruchamiania usługi informowało SCM jego bieżący stan. Robi to przez przekazanie **SERVICE_START_PENDING** funkcji Win32 API [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` następnie wywołuje `CAtlExeModuleT::InitializeCom`, który wywołuje funkcję Win32 API [funkcja CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Domyślnie `InitializeCom` przekazuje **COINIT_MULTITHREADED** flagi funkcji. Ta flaga wskazuje, że program ma być serwerem bezwątkowy.  
  
 Teraz `CAtlServiceModuleT::Run` jest wywoływana w celu wykonywania głównych pracy usługi. **Uruchom** kontynuuje wykonywanie aż do zatrzymania usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

