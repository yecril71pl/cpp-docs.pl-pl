---
title: Właściwości debugera systemu Android (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374199"
---
# <a name="android-debugger-properties"></a>Właściwości debugera systemu Android

| Właściwość | Opis | Choices |
|--|--|--|
| Typ debugera | Określa typ kodu do debugowania. | **Tylko natywny**<br /><br />**Tylko Java** |
| Obiekt docelowy debugowania | Określa emulator lub urządzenie do debugowania. Jeśli nie są uruchomione żadne emulatory, użyj "Menedżera urządzeń wirtualnych systemu Android (AVD), aby uruchomić urządzenie. |
| Pakiet do uruchomienia | Określa lokalizację pliku *.apk,* która zostanie debugowana. Ta opcja uruchamia pakiet (APK) po debugowaniu aplikacji. |
| Działanie uruchamiania | Działanie systemu Android do uruchomienia aplikacji, musi odpowiadać tej używanej w manifeście. Naciśnij przycisk Zastosuj, aby pobrać listę z *pliku AndroidManifest.xml* i wypełnić ją dynamicznie. |
| Dodatkowe ścieżki wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania symboli debugowania. |
| Dodatkowe ścieżki wyszukiwania źródła Java | Dodatkowe ścieżki wyszukiwania plików źródłowych oprogramowania Java. (Ma zastosowanie tylko wtedy, gdy typ debugera jest tylko w języku Java). |
