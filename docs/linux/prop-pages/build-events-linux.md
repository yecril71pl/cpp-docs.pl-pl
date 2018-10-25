---
title: Zdalne tworzenie zdarzenia (Linux C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 2ea01c5d92cbdb6066dc87675221eae6865af354
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070988"
---
# <a name="build-event-properties-linux-c"></a>Tworzenie właściwości zdarzenia (Linux C++)

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
