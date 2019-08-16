---
title: 'Funkcja CAtlServiceModuleT:: Run — funkcja'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 0c35020996852731a8f22c15860d4cceb7a8bdb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491518"
---
# <a name="catlservicemoduletrun-function"></a>Funkcja CAtlServiceModuleT:: Run — funkcja

`Run`zawiera wywołania do `PreMessageLoop`, `RunMessageLoop`, i `PostMessageLoop`. Po wywołaniu należy `PreMessageLoop` najpierw przechowywać identyfikator wątku usługi. Usługa użyje tego identyfikatora do zamknięcia, wysyłając wiadomość WM_QUIT przy użyciu funkcji Win32 API, [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew).

`PreMessageLoop`następnie wywołuje `InitializeSecurity`. Domyślnie program `InitializeSecurity` wywołuje [CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) z deskryptorem zabezpieczeń ustawionym na wartość null, co oznacza, że każdy użytkownik ma dostęp do obiektu.

Jeśli nie chcesz, aby usługa określiła własne zabezpieczenia, przesłonięcia `PreMessageLoop` i nie Wywołaj `InitializeSecurity`, a następnie com określi ustawienia zabezpieczeń z rejestru. Wygodnym sposobem konfigurowania ustawień rejestru jest narzędzie [DCOMCNFG](../atl/dcomcnfg.md) opisane w dalszej części tej sekcji.

Po określeniu zabezpieczeń obiekt jest zarejestrowany w modelu COM, dzięki czemu nowi klienci mogą łączyć się z programem. Na koniec program instruuje menedżera kontroli usług (SCM), że jest uruchomiony, a program wprowadza pętlę komunikatów. Program pozostaje uruchomiony do momentu opublikowania komunikatu zamknięcia po zamknięciu usługi.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)<br/>
[Klasa CSecurityDesc](../atl/reference/csecuritydesc-class.md)<br/>
[Klasa CSid](../atl/reference/csid-class.md)<br/>
[Klasa CDacl](../atl/reference/cdacl-class.md)<br/>
[Funkcja CAtlServiceModuleT:: Run](../atl/reference/catlservicemodulet-class.md#run)
