---
title: Informacje o LIB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8fd3d370da4f841e85086e3d061508d68414e96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379201"
---
# <a name="overview-of-lib"></a>Informacje o LIB
LIB tworzy standardowych bibliotek, importowanie bibliotek i eksportowanie plików, których można używać z [łącze](../../build/reference/linker-options.md) podczas tworzenia programu. LIB uruchamiane z wiersza polecenia.  
  
 LIB można użyć w następujących trybach:  
  
-   [Tworzenie lub modyfikowanie biblioteki COFF](../../build/reference/managing-a-library.md)  
  
-   [Wyodrębnianie obiektu elementu członkowskiego do pliku](../../build/reference/extracting-a-library-member.md)  
  
-   [Tworzenie pliku eksportu i importu biblioteki](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 Te tryby są wzajemnie; LIB można użyć w tylko jednym trybie naraz.  
  
## <a name="lib-options"></a>Opcje lib  
 W poniższej tabeli wymieniono opcje lib.exe z łącza do dodatkowych informacji.  
  
 **/ DEF**  
 Tworzenie biblioteki importowanej oraz pliku eksportu.  
  
 Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ERRORREPORT**  
 Wyślij informacje do firmy Microsoft o wewnętrznych błędach z lib.exe.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
 **/EXPORT**  
 Eksportuje funkcję z programu.  
  
 Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ EXTRACT**  
 Utwórz plik obiektu (.obj), który zawiera kopię członkiem istniejącej biblioteki.  
  
 Aby uzyskać więcej informacji, zobacz [wyodrębnianie członka biblioteki](../../build/reference/extracting-a-library-member.md).  
  
 **/INCLUDE**  
 Dodaje symbol do tabeli symboli.  
  
 Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ LIBPATH**  
 Powoduje zastąpienie środowiska ścieżki biblioteki.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/ LIST**  
 Wyświetla informacje o bibliotece wyjściowej na wyjście standardowe.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/LTCG**  
 Powoduje, że biblioteka ma zostać utworzony przy użyciu Generowanie łączonych kodów czasowych.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
 **/ MACHINE**  
 Określa platformę docelową dla programu.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
 **/ NAZWA**  
 Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki dll, dla której jest tworzona biblioteki importu.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/ NODEFAULTLIB**  
 Usuwa co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/NOLOGO**  
 Pomija wyświetlanie LIB praw autorskich wiadomości oraz numer wersji i uniemożliwia wyświetlanie plików polecenia.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
 **/ OUT**  
 Przesłania domyślną nazwę pliku wyjściowego.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **LUB USUŃ**  
 Pomija obiekt z biblioteki wyjściowej.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/SUBSYSTEM**  
 Informuje system operacyjny, jak uruchomić program utworzony przez łączenie z biblioteki wyjściowej.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).  
  
 **/VERBOSE**  
 Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików .obj dodawany.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
 **/WX**  
 Traktuj ostrzeżenia jako błędy.  
  
 Aby uzyskać więcej informacji, zobacz [systemem LIB](../../build/reference/running-lib.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki LIB](../../build/reference/lib-reference.md)   
 [Pliki wyjściowe LIB](../../build/reference/lib-input-files.md)   
 [Pliki wyjściowe LIB](../../build/reference/lib-output-files.md)   
 [Inne dane wyjściowe LIB](../../build/reference/other-lib-output.md)   
 [Struktura biblioteki](../../build/reference/structure-of-a-library.md)