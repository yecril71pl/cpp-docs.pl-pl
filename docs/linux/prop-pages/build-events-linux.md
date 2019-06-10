---
title: Zdarzenia kompilacji zdalnej (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 1e5c453da05fe65871fa7f6b0d4ca6528a96d4dd
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821478"
---
# <a name="build-event-properties-linux-c"></a>Tworzenie właściwości zdarzenia (Linux C++)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Zdarzenie sprzed kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można przekazać jako lokalną do par mapowania zdalnego przy użyciu składni: pełna_ścieżka_lokalna_1: = pełna_ścieżka_zdalna_1; pełna_ścieżka_lokalna_2: = pełna_ścieżka_zdalna_2, gdzie można skopiować plik lokalny do określonej lokalizacji zdalnej w systemie zdalnym.

## <a name="pre-link-event"></a>Zdarzenie Prekonsolidacyjne

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekonsolidacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekonsolidacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można przekazać jako lokalną do par mapowania zdalnego przy użyciu składni: pełna_ścieżka_lokalna_1: = pełna_ścieżka_zdalna_1; pełna_ścieżka_lokalna_2: = pełna_ścieżka_zdalna_2, gdzie można skopiować plik lokalny do określonej lokalizacji zdalnej w systemie zdalnym.

## <a name="post-build-event"></a>Zdarzenie po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można przekazać jako lokalną do par mapowania zdalnego przy użyciu składni: pełna_ścieżka_lokalna_1: = pełna_ścieżka_zdalna_1; pełna_ścieżka_lokalna_2: = pełna_ścieżka_zdalna_2, gdzie można skopiować plik lokalny do określonej lokalizacji zdalnej w systemie zdalnym.

## <a name="remote-pre-build-event"></a>Zdalne zdarzenie Prekompilacyjne

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można przekazać jako zdalną do lokalnych par mapowania przy użyciu składni: pełna_ścieżka_zdalna_1: = pełna_ścieżka_lokalna_1; pełna_ścieżka_zdalna_2: = pełna_ścieżka_lokalna_2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym.

## <a name="remote-pre-link-event"></a>Zdalne zdarzenie poprzedzające Link

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekonsolidacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekonsolidacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można przekazać jako zdalną do lokalnych par mapowania przy użyciu składni: pełna_ścieżka_zdalna_1: = pełna_ścieżka_lokalna_1; pełna_ścieżka_zdalna_2: = pełna_ścieżka_lokalna_2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym.

## <a name="remote-post-build-event"></a>Zdalne zdarzenie Pokompilacyjne

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można przekazać jako zdalną do lokalnych par mapowania przy użyciu składni: pełna_ścieżka_zdalna_1: = pełna_ścieżka_lokalna_1; pełna_ścieżka_zdalna_2: = pełna_ścieżka_lokalna_2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym.

::: moniker-end


