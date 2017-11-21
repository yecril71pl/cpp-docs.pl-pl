---
title: "Debuger właściwości (Linux C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.RaspberryDebugger.DebuggerType
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.RaspberryDebugger.LaunchActivity
- VC.Project.LinuxDebugger.DebugChildProcesses
ms.openlocfilehash: d47645eab33ffb0ee6a203fdfb0cf30c856ea63f
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="c-debugging-properties-linux-c"></a>C++, debugowanie właściwości (Linux C++)

Właściwość | Opis | Opcje
--- | ---| ---
Wstępnie uruchomienia polecenia | Polecenie, które jest uruchamiane na powłoki przed uruchomieniem debugowania i przed debuger jest uruchomiony i może służyć do wpłyną na środowisko debugowania.
Program | Pełna ścieżka do programu do debugowania w systemie zdalnym. To jest ścieżka w systemie zdalnym. Jeśli zostawić puste lub bez zmian, jego domyślnie bieżące dane wyjściowe projektu.
Argumenty programu | Argumenty wiersza polecenia do przekazania do debugowanego programu.
Katalog roboczy | Katalog roboczy aplikacji zdalnej. Domyślnie katalogu macierzystego użytkownika.
Debuger dodatkowych poleceń | Gdb dodatkowe polecenia debugera do uruchomienia przed rozpoczęciem debugowania.
Numer portu debugera | Numer portu do komunikacji debugera z debugera zdalnego. Numer portu nie może być używane lokalnie. Ta wartość musi być dodatnią od 1 do 65535. Jeśli nie podano numeru portu wolne zostanie użyta.
Numer portu debugera zdalnego | Numer portu, na którym nasłuchuje serwer zdalny debuger (gdbserver) w systemie zdalnym. Numer portu nie może być używany w systemie zdalnym. Ta wartość musi być dodatnią od 1 do 65535. Jeśli nie podano numeru portu wolne, zaczynając od 4444 będą używane.
Tryb debugowania | Określa, jak interfejsy debugera z gdb. W trybie gdb debuger dysków gdb za pośrednictwem powłoki w systemie zdalnym. W trybie gdbserver gdb działa lokalnie i łączy gdbserver uruchamiany zdalnie. | **gdbserver**<br>**gdb**<br>
Dodatkowa ścieżka wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania dla symboli debugowania (solib ścieżki wyszukiwania).
Debugowanie procesów podrzędnych | Określa, czy włączyć debugowanie procesów podrzędnych.
Włącz Python funkcja Pretty Print | Włącz funkcja pretty Print wartości wyrażenia. Obsługiwane tylko w gdb tryb debugowania.
Plik wizualizacji | Domyślny wizualizacji natywny plik (.natvis) zawierających dyrektywy wizualizację typów SLT. Inne pliki .natvis, które należą do bieżącego rozwiązania będą ładowane automatycznie.
Mapy ścieżki plików dodatkowych źródeł | Dodatkowe ścieżki ekwiwalenty debugera do używania w celu mapowania systemu Windows ze źródłem nazwy pliku do nazwy pliku źródłowego systemu Linux. Format "\<ścieżki systemu windows > =\<ścieżka systemu linux >;...". Nazwa pliku źródłowego, znajdują się w ścieżce systemu Windows zostanie dodane odwołanie tak, jakby to zostało znalezione w tej samej pozycji względnej, ścieżka systemu Linux. Pliki znajdujące się w lokalnym projektu nie wymagają dodatkowych mapowania.