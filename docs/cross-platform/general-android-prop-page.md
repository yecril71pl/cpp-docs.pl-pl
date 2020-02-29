---
title: Ogólne właściwości projektu (Android C++)
ms.date: 10/23/2017
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
f1_keywords:
- VC.Project.VCConfiguration.Android.OutputDirectory
- VC.Project.VCConfiguration.Android.IntermediateDirectory
- VC.Project.VCConfiguration.Android.TargetName
- VC.Project.VCConfiguration.Android.TargetExt
- VC.Project.VCConfiguration.Android.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.Android.BuildLogFile
- VC.Project.VCConfiguration.Android.PlatformToolset
- VC.Project.VCConfiguration.Android.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: 694e69e063f73830c21976bd0615cf4d1d99b368
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177578"
---
# <a name="general-project-properties-android-c"></a>Ogólne właściwości projektu (Android C++)

Właściwość | Opis | Decyzji
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez ten projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez ten projekt. (Przykład: *. exe* lub *. dll*)
Rozszerzenia do usunięcia podczas czyszczenia | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, dla których pliki w katalogu pośrednim mają zostać usunięte podczas czyszczenia lub odbudowy.
Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone.
Zestaw narzędzi platformy | Określa zestaw narzędzi używany do tworzenia bieżącej konfiguracji; Jeśli nie zostanie ustawiona, używany jest domyślny zestaw narzędzi
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)** — Biblioteka dynamiczna ( *. tak*)<br>**Biblioteka statyczna (. a)** — Biblioteka statyczna ( *. a*)<br>**Narzędzia — narzędzie**<br>**Reguł programu make** — plik reguł programu make<br>
Docelowy poziom interfejsu API | Poziom interfejsu API NDK dla systemu Android, którego dotyczy ta konfiguracja.
Użycie STL | Określa, C++ która Biblioteka standardowa ma być używana dla tej konfiguracji. | **Minimalna C++ Biblioteka środowiska uruchomieniowego (system)**<br>**C++Biblioteka statyczna środowiska uruchomieniowego (Gabi + + _static)**<br>**C++udostępniona biblioteka środowiska uruchomieniowego (Gabi + + _shared)**<br>**Biblioteka statyczna środowiska uruchomieniowego STLport (stlport_static)**<br>**Biblioteka udostępniona środowiska uruchomieniowego STLport (stlport_shared)**<br>**Biblioteka statyczna GNU STL (gnustl_static)**<br>**Udostępniona biblioteka GNU STL (gnustl_shared)**<br>**Biblioteka statyczna LLVM libc + + (c++ _static)**<br>**Biblioteka udostępniona LLVM libc + + (c++ _shared)**<br>
Tryb przewijania | Generuj kod, który jest wykonywany dla mikroarchitektury przycisku przewijania. Dotyczy to tylko architektury ARM. | **Odcisk**<br>**ARM**<br>**Disabled (Wyłączone)**<br>
