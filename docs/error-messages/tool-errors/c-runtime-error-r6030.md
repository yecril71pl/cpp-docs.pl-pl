---
title: R6030 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 7f5c61d9b39b1d655bcbf3d42ea870370ddf2842
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461623"
---
# <a name="c-runtime-error-r6030"></a>R6030 błąd środowiska uruchomieniowego języka C

Nie zainicjowano CRT

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Ten problem najczęściej jest spowodowany przez niektóre programy zabezpieczeń lub rzadko, usterki w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Oprogramowanie zabezpieczające może mieć określone instrukcje łagodzenia ten problem. Sprawdź z dostawcą oprogramowania zabezpieczeń witryny sieci Web, aby uzyskać szczegółowe informacje. Alternatywnie Sprawdź, czy zaktualizowane wersje oprogramowania zabezpieczeń lub spróbuj oprogramowania zabezpieczającego innej.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, jeśli używasz środowiska uruchomieniowego C (CRT), ale kod uruchamiający CRT nie zostało wykonane. Istnieje możliwość ten błąd, jeśli przełącznik konsolidatora [/Entry](../../build/reference/entry-entry-point-symbol.md) służy do zastępowania domyślny początkowy adres, zwykle **mainCRTStartup**, **wmainCRTStartup** dla konsoli EXE, **WinMainCRTStartup** lub **wWinMainCRTStartup** dla Windows EXE, lub **_DllMainCRTStartup** dla biblioteki DLL. Chyba że nosi nazwę jednej z powyższych funkcji podczas uruchamiania, środowisko wykonawcze języka C nie można zainicjować. Te funkcje uruchamiania zazwyczaj są nazywane domyślnie, gdy łącze do biblioteki środowiska uruchomieniowego C i użyć normalnych **głównego**, **wmain**, **WinMain**, lub  **DllMain** punkty wejścia.

Istnieje również możliwość ten błąd, gdy inny program pułapki pewne wywołania biblioteki DLL za pomocą techniki wstrzykiwania kodu. Niektóre programy zabezpieczeń bez wprowadzania niepożądanych używają tej techniki. W wersjach programu Visual C++ przed Visual Studio 2015 można użyć biblioteki CRT połączone statycznie, aby rozwiązać ten problem, ale nie jest to zalecane ze względów bezpieczeństwa i stosowanie aktualizacji. Naprawienia tego problemu może wymagać akcji przez użytkownika końcowego.