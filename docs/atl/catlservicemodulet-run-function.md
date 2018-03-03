---
title: Funkcja CAtlServiceModuleT::Run | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff3efe9298b7a2c11e7f83ef58640b2947519b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemoduletrun-function"></a>Funkcja CAtlServiceModuleT::Run
**Uruchom** zawiera wywołania `PreMessageLoop`, `RunMessageLoop`, i `PostMessageLoop`. Po wywołaniu, `PreMessageLoop` najpierw przechowuje identyfikator wątku usługi. Usługa użyje tego Identyfikatora zamknąć samego, wysyłając **WM_QUIT** wiadomości przy użyciu funkcji Win32 API [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946).  
  
 `PreMessageLoop`następnie wywołuje `InitializeSecurity`. Domyślnie `InitializeSecurity` wywołania [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) przez deskryptor zabezpieczeń jest ustawiony na wartość NULL, co oznacza, że każdy użytkownik ma dostęp do obiektu.  
  
 Jeśli nie chcesz, aby usługi do określenia własnego bezpieczeństwa, Zastąp `PreMessageLoop` i nie wywołuj `InitializeSecurity`, oraz COM następnie określić ustawienia zabezpieczeń z rejestru. Jest to wygodny sposób konfigurowania ustawień rejestru z [DCOMCNFG](../atl/dcomcnfg.md) narzędzie później omówione w tej sekcji.  
  
 Po zabezpieczeń jest określony, obiekt jest zarejestrowana w modelu COM, dzięki czemu nowi klienci mogą łączyć się z programem. Ponadto program informuje Menedżera sterowania usługami (SCM) jest uruchomiona, a program wprowadza pętlę komunikatów. Program jest uruchomiona do momentu jego zapisuje komunikat o rezygnacji po zamknięciu usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [Klasa CSecurityDesc](../atl/reference/csecuritydesc-class.md)   
 [Klasa CSid](../atl/reference/csid-class.md)   
 [Klasa CDacl](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

