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
ms.openlocfilehash: 9dff3fa3f3ed20406955570f2ad72531f4e44f11
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848124"
---
# <a name="catlservicemoduletservicemain-function"></a>Funkcja CAtlServiceModuleT::ServiceMain
Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji w Panelu sterowania, wybierz usługę i kliknij przycisk **Start**.  
  
 Po Menedżer sterowania usługami wywołuje `ServiceMain`, usługa musi udzielić Menedżer sterowania usługami, funkcja obsługi. Ta funkcja pozwala na uzyskanie stanu usługi i przekazać szczegółowych instrukcji (na przykład wstrzymanie lub zatrzymanie) Menedżer sterowania usługami. Menedżer sterowania usługami pobiera tę funkcję, gdy usługa przekazuje `_Handler` funkcji Win32 API [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (`_Handler` jest funkcją statycznego elementu członkowskiego, która wywołuje funkcję niestatycznego elementu członkowskiego [obsługi](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Podczas uruchamiania usługi powinien również poinformować SCM swojego bieżącego stanu. Jest to realizowane przez przekazanie SERVICE_START_PENDING funkcji Win32 API [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` następnie wywołuje `CAtlExeModuleT::InitializeCom`, który wywołuje funkcję Win32 API [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Domyślnie `InitializeCom` przekazuje flagę COINIT_MULTITHREADED do funkcji. Ta flaga wskazuje, że program ma być bezwątkowy serwer.  
  
 Teraz `CAtlServiceModuleT::Run` jest wywoływana w celu wykonania pracy głównego usługi. `Run` kontynuuje wykonywanie dopóki nie zostanie zatrzymana.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

