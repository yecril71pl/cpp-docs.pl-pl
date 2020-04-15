---
title: Zdarzenia kompilacji zdalnej (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441500"
---
# <a name="build-event-properties-linux-c"></a>Właściwości zdarzenia kompilacji (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Zdarzenie przed kompilacją

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia uruchamiania narzędzia zdarzeń przed kompilacją. |
| Opis | Określa opis narzędzia zdarzeń przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie należy określić lokalne i zdalne pary mapowania przy użyciu składni w ten sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny może być skopiowany do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="pre-link-event"></a>Zdarzenie wstępne

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia uruchamiania narzędzia zdarzeń przed łączem. |
| Opis | Określa opis narzędzia zdarzeń przed łączem do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie należy określić lokalne i zdalne pary mapowania przy użyciu składni w ten sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny może być skopiowany do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="post-build-event"></a>Zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń po kompilacji do uruchomienia. |
| Opis | Określa opis narzędzia zdarzeń po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie należy określić lokalne i zdalne pary mapowania przy użyciu składni w ten sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny może być skopiowany do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="remote-pre-build-event"></a>Zdarzenie zdalnego wstępnego budowania

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń pre-build do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzeń przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie należy określić zdalne do lokalnych par mapowania przy użyciu składni w ten sposób: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, gdzie zdalny plik może być skopiowany do określonej lokalizacji na komputerze lokalnym. |

## <a name="remote-pre-link-event"></a>Zdarzenie zdalnego łącza wstępnego

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń przed łączem do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzeń przed łączem do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie należy określić zdalne do lokalnych par mapowania przy użyciu składni w ten sposób: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, gdzie zdalny plik może być skopiowany do określonej lokalizacji na komputerze lokalnym. |

## <a name="remote-post-build-event"></a>Zdarzenie zdalnego po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń po kompilacji, które ma być uruchamiane w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzeń po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie należy określić zdalne do lokalnych par mapowania przy użyciu składni w ten sposób: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, gdzie zdalny plik może być skopiowany do określonej lokalizacji na komputerze lokalnym. |

::: moniker-end
