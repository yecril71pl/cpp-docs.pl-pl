---
title: Zdarzenia (Linux C++) kompilacji zdalnej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 25e51a7df39c649ec8425f4aee332086acc408d6
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="build-event-properties-linux-c"></a>Tworzenie właściwości zdarzenia (Linux C++) 

## <a name="pre-build-event"></a>Zdarzenia Prekompilacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listy można podać jako lokalnego z parami mapowania zdalnego przy użyciu składni następująco: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, w której plik lokalny mogą zostać skopiowane do określonej lokalizacji zdalnego w systemie zdalnym.

## <a name="pre-link-event"></a>Zdarzenia Prekonsolidacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekonsolidacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekonsolidacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listy można podać jako lokalnego z parami mapowania zdalnego przy użyciu składni następująco: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, w której plik lokalny mogą zostać skopiowane do określonej lokalizacji zdalnego w systemie zdalnym.

## <a name="post-build-event"></a>Zdarzenie mające miejsce po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listy można podać jako lokalnego z parami mapowania zdalnego przy użyciu składni następująco: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, w której plik lokalny mogą zostać skopiowane do określonej lokalizacji zdalnego w systemie zdalnym.

## <a name="remote-pre-build-event"></a>Zdalne zdarzenia Prekompilacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki, aby skopiować z systemu zdalnego. Opcjonalnie listy można podać jako zdalnej z parami mapowania lokalnych przy użyciu składni następująco: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, w której pliku zdalnego mogą zostać skopiowane do określonej lokalizacji na komputerze lokalnym.

## <a name="remote-pre-link-event"></a>Zdalne zdarzenia Prekonsolidacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekonsolidacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekonsolidacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki, aby skopiować z systemu zdalnego. Opcjonalnie listy można podać jako zdalnej z parami mapowania lokalnych przy użyciu składni następująco: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, w której pliku zdalnego mogą zostać skopiowane do określonej lokalizacji na komputerze lokalnym.

## <a name="remote-post-build-event"></a>Zdalne zdarzenie mające miejsce po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki, aby skopiować z systemu zdalnego. Opcjonalnie listy można podać jako zdalnej z parami mapowania lokalnych przy użyciu składni następująco: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, w której pliku zdalnego mogą zostać skopiowane do określonej lokalizacji na komputerze lokalnym.
