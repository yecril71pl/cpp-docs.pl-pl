---
title: Funkcja CAtlServiceModuleT::Run
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 3abb6908a64864463c45d8fc4dc24bfc813db586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458672"
---
# <a name="catlservicemoduletrun-function"></a>Funkcja CAtlServiceModuleT::Run

`Run` zawiera wywołania `PreMessageLoop`, `RunMessageLoop`, i `PostMessageLoop`. Po wywołaniu, `PreMessageLoop` najpierw przechowuje identyfikator usługi wątku. Usługa będzie Użyj tego Identyfikatora, aby zamknąć samego, wysyłając wiadomość WM_QUIT przy użyciu funkcji Win32 API [PostThreadMessage](https://msdn.microsoft.com/library/windows/desktop/ms644946).

`PreMessageLoop` następnie wywołuje `InitializeSecurity`. Domyślnie `InitializeSecurity` wywołania [funkcję CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity) deskryptora zabezpieczeń, wartość NULL, co oznacza, że każdy użytkownik ma dostęp do obiektu.

Jeśli użytkownik nie chce usługi, aby określić własne zabezpieczeń, zastępują `PreMessageLoop` i nie wywołuj `InitializeSecurity`, oraz COM następnie określić ustawienia zabezpieczeń z rejestru. Jest to wygodny sposób konfigurowania ustawień rejestru [DCOMCNFG](../atl/dcomcnfg.md) narzędzie omówione w dalszej części w tej sekcji.

Po określeniu zabezpieczeń obiektu są rejestrowane w modelu COM, dzięki czemu nowi klienci mogą łączyć się z programem. Ponadto program informuje Menedżera sterowania usługami (SCM), że jest uruchomiona, a program wprowadza pętlę komunikatów. Program jest uruchomiona, dopóki nie publikuje komunikat o po zamknięciu usługi.

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)<br/>
[Klasa CSecurityDesc](../atl/reference/csecuritydesc-class.md)<br/>
[Klasa CSid](../atl/reference/csid-class.md)<br/>
[Klasa CDacl](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

