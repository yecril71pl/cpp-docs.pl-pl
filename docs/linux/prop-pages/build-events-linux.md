---
title: Zdalne zdarzenia kompilacji (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441500"
---
# <a name="build-event-properties-linux-c"></a>Właściwości zdarzenia kompilacji (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Zdarzenie sprzed kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia przed kompilacją, które ma zostać uruchomione. |
| Opis | Określa opis narzędzia zdarzenia przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie możesz określić pary mapowania lokalnego do zdalnego przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="pre-link-event"></a>Zdarzenie poprzedzające połączenie

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia poprzedzającego połączenie, które ma zostać uruchomione. |
| Opis | Określa opis narzędzia zdarzenia poprzedzającego połączenie, które ma być wyświetlane. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie możesz określić pary mapowania lokalnego do zdalnego przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="post-build-event"></a>Zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia po kompilacji, które ma zostać uruchomione. |
| Opis | Określa opis narzędzia zdarzenia po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie możesz określić pary mapowania lokalnego do zdalnego przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

## <a name="remote-pre-build-event"></a>Zdalne zdarzenie sprzed kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia przed kompilacją do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzenia przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie możesz określić zdalne do lokalnych par mapowania przy użyciu składni podobnej do następującej: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym. |

## <a name="remote-pre-link-event"></a>Zdalne zdarzenie poprzedzające link

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia poprzedzającego połączenie do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzenia poprzedzającego połączenie, które ma być wyświetlane. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie możesz określić zdalne do lokalnych par mapowania przy użyciu składni podobnej do następującej: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym. |

## <a name="remote-post-build-event"></a>Zdalne zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia po kompilacji do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzenia po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie możesz określić zdalne do lokalnych par mapowania przy użyciu składni podobnej do następującej: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym. |

::: moniker-end
