---
title: Jak kontrola konta użytkownika (UAC) wpływa na aplikację?
ms.date: 11/04/2016
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 336260ddc1c9da795478d5541af73d9801633843
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556965"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak kontrola konta użytkownika (UAC) wpływa na aplikację?

Kontrola konta użytkownika (UAC) jest funkcją systemu Windows Vista, w którym użytkownik konta ma ograniczone uprawnienia. Można znaleźć szczegółowe informacje na temat funkcji Kontrola konta użytkownika w tych lokacjach:

- [Najlepsze rozwiązania dla deweloperów i wytyczne dotyczące aplikacji w środowisku o najniższych uprawnieniach](/windows/desktop/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Kompilowanie projektów po włączeniu funkcji Kontrola konta użytkownika

Jeśli tworzysz projekt Visual C++ w Windows Vista z funkcji kontroli konta użytkownika jest wyłączona, a później włączyć funkcji Kontrola konta użytkownika, należy wyczyścić i ponownie skompiluj projekt, aby mogła działać prawidłowo.

## <a name="applications-that-require-administrative-privileges"></a>Aplikacje, które wymagają uprawnień administratora

Domyślnie konsolidator Visual C++ osadza fragmentu funkcji Kontrola konta użytkownika do manifestu aplikacji z poziomem wykonywania `asInvoker`. Jeśli aplikacja wymaga uprawnień administracyjnych do poprawnego działania (na przykład w przypadku, gdy modyfikuje węzłem HKLM rejestru lub zapisuje w chronionych obszarach dysku, takie jak katalog Windows), należy zmodyfikować aplikację.

Pierwsza opcja jest zmodyfikowanie fragmentu UAC manifestu, aby zmienić poziom wykonywania *requireAdministrator*. Aplikacja następnie będzie monitować użytkownika o poświadczenia administracyjne, zanim zostanie ona uruchomiona. Aby dowiedzieć się, jak to zrobić, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

Drugą opcją jest osadzaj fragmentu funkcji Kontrola konta użytkownika do manifestu, określając `/MANIFESTUAC:NO` — opcja konsolidatora. W takim przypadku aplikacja jest uruchamiana zwirtualizowanych. Wszelkie zmiany wprowadzone do rejestru lub systemu plików zostanie usunięte podczas instalacji aplikacji została zakończona.

Następujące schemat blokowy opisano, jak aplikacja jest uruchamiana w zależności od tego, czy jest włączona funkcja Kontrola konta użytkownika i tego, czy aplikacja ma manifestu kontroli konta użytkownika:

![Windows Vista Loader zachowanie](media/uacflowchart.png "UACflowchart")

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące zabezpieczeń](security-best-practices-for-cpp.md)
