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
ms.openlocfilehash: d9f1be2c862775c76bbaad36f84c871eff5a38d5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759625"
---
# <a name="catlservicemoduletrun-function"></a>Funkcja CAtlServiceModuleT::Run

`Run` zawiera wywołania `PreMessageLoop`, `RunMessageLoop`, i `PostMessageLoop`. Po wywołaniu, `PreMessageLoop` najpierw przechowuje identyfikator usługi wątku. Usługa będzie Użyj tego Identyfikatora, aby zamknąć samego, wysyłając wiadomość WM_QUIT przy użyciu funkcji Win32 API [PostThreadMessage](https://msdn.microsoft.com/library/windows/desktop/ms644946).

`PreMessageLoop` następnie wywołuje `InitializeSecurity`. Domyślnie `InitializeSecurity` wywołania [funkcję CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity) deskryptora zabezpieczeń, wartość NULL, co oznacza, że każdy użytkownik ma dostęp do obiektu.

Jeśli użytkownik nie chce usługi, aby określić własne zabezpieczeń, zastępują `PreMessageLoop` i nie wywołuj `InitializeSecurity`, oraz COM następnie określić ustawienia zabezpieczeń z rejestru. Jest to wygodny sposób konfigurowania ustawień rejestru [DCOMCNFG](../atl/dcomcnfg.md) narzędzie omówione w dalszej części w tej sekcji.

Po określeniu zabezpieczeń obiektu są rejestrowane w modelu COM, dzięki czemu nowi klienci mogą łączyć się z programem. Ponadto program informuje Menedżera sterowania usługami (SCM), że jest uruchomiona, a program wprowadza pętlę komunikatów. Program jest uruchomiona, dopóki nie publikuje komunikat o po zamknięciu usługi.

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)   
[Klasa CSecurityDesc](../atl/reference/csecuritydesc-class.md)   
[Klasa CSid](../atl/reference/csid-class.md)   
[Klasa CDacl](../atl/reference/cdacl-class.md)   
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

