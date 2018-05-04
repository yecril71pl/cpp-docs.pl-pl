---
title: Funkcja CAtlServiceModuleT::Run | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a07ad6b09fa10a81b500625531226dc18fc6281a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemoduletrun-function"></a>Funkcja CAtlServiceModuleT::Run
**Uruchom** zawiera wywołania `PreMessageLoop`, `RunMessageLoop`, i `PostMessageLoop`. Po wywołaniu, `PreMessageLoop` najpierw przechowuje identyfikator wątku usługi. Usługa użyje tego Identyfikatora zamknąć samego, wysyłając **WM_QUIT** wiadomości przy użyciu funkcji Win32 API [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946).  
  
 `PreMessageLoop` następnie wywołuje `InitializeSecurity`. Domyślnie `InitializeSecurity` wywołania [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) przez deskryptor zabezpieczeń jest ustawiony na wartość NULL, co oznacza, że każdy użytkownik ma dostęp do obiektu.  
  
 Jeśli nie chcesz, aby usługi do określenia własnego bezpieczeństwa, Zastąp `PreMessageLoop` i nie wywołuj `InitializeSecurity`, oraz COM następnie określić ustawienia zabezpieczeń z rejestru. Jest to wygodny sposób konfigurowania ustawień rejestru z [DCOMCNFG](../atl/dcomcnfg.md) narzędzie później omówione w tej sekcji.  
  
 Po zabezpieczeń jest określony, obiekt jest zarejestrowana w modelu COM, dzięki czemu nowi klienci mogą łączyć się z programem. Ponadto program informuje Menedżera sterowania usługami (SCM) jest uruchomiona, a program wprowadza pętlę komunikatów. Program jest uruchomiona do momentu jego zapisuje komunikat o rezygnacji po zamknięciu usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [Klasa CSecurityDesc](../atl/reference/csecuritydesc-class.md)   
 [Klasa CSid](../atl/reference/csid-class.md)   
 [Klasa CDacl](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

