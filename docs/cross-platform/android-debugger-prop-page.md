---
title: Właściwości debugera systemu AndroidC++()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 8ff6e539828d697e103c820d05565969f6afb910
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177529"
---
# <a name="android-debugger-properties"></a>Właściwości debugera systemu Android

Właściwość | Opis | Decyzji
--- | ---| ---
Typ debugera | Określa typ kodu do debugowania. | **Tylko natywny**<br>**Tylko Java**<br>
Element docelowy debugowania | Określa emulator lub urządzenie, które ma być używane na potrzeby debugowania. Jeśli nie są uruchomione żadne emulatory, użyj "Menedżera urządzeń wirtualnych systemu Android (AVD)", aby uruchomić urządzenie.
Pakiet do uruchomienia | Określa lokalizację elementu *. apk* , który będzie debugowany. Ta opcja uruchamia pakiet (APK), gdy aplikacja jest debugowana.
Działanie uruchamiania | Działanie systemu Android służące do uruchamiania aplikacji musi pasować do używanej w manifeście. Naciśnij przycisk Zastosuj, aby pobrać listę z *pliku AndroidManifest. XML* i wypełnić ją dynamicznie.
Dodatkowe ścieżki wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania dla symboli debugowania.
Dodatkowe ścieżki wyszukiwania źródła Java | Dodatkowe ścieżki wyszukiwania dla plików źródłowych Java. (Stosuje się tylko wtedy, gdy typ debugera jest tylko w języku Java).
