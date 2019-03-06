---
title: Informacje o LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: a66f78d225a5899b53a931c7eb6a0564de689ca1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423290"
---
# <a name="overview-of-lib"></a>Informacje o LIB

LIB tworzy standardowych bibliotek, importowanie bibliotek i eksportowanie plików za pomocą [łącze](../../build/reference/linker-options.md) podczas tworzenia programu. Lib — jest uruchamiany z poziomu wiersza polecenia.

Lib — można użyć w następujących trybach:

- [Tworzenie lub modyfikowanie biblioteki COFF](../../build/reference/managing-a-library.md)

- [Trwa wyodrębnianie obiektu elementu członkowskiego do pliku](../../build/reference/extracting-a-library-member.md)

- [Tworzenie pliku eksportu i bibliotekę importu](../../build/reference/working-with-import-libraries-and-export-files.md)

Te tryby są wzajemnie się wykluczają; LIB w tylko jednym trybie służy w danym momencie.

## <a name="lib-options"></a>Opcje lib

Poniższa tabela zawiera listę opcji lib.exe Link, aby uzyskać więcej informacji.

|Opcja|Opis|
|-|-|
|**/DEF**|Tworzenie biblioteki importowanej oraz pliku eksportu.<br/><br/>Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**|   Wysyła do firmy Microsoft informacje o wewnętrznych błędach za pomocą lib.exe.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|
|**/EXPORT**|   Eksportuje funkcję z programu.<br/><br/>Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ EXTRACT**|   Utwórz plik obiektowy (.obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki.<br/><br/>Aby uzyskać więcej informacji, zobacz [wyodrębnianie członka biblioteki](../../build/reference/extracting-a-library-member.md).|
|**/INCLUDE**|   Dodaje symbol do tabeli symboli.<br/><br/>Aby uzyskać więcej informacji, zobacz [kompilowanie biblioteki importowanej oraz pliku eksportu](../../build/reference/building-an-import-library-and-export-file.md).|
|**/ LIBPATH**|   Zastępuje ścieżki biblioteki środowiska.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/ LIST**|   Wyświetla informacje o bibliotece wyjściowej na wyjście standardowe.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/LTCG**|   Powoduje, że biblioteka ma zostać utworzony przy użyciu Generowanie łączonych kodów czasowych.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|
|**/ MACHINE**|   Określa platformę docelową dla programu.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|
|**/ NAME**|   Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki dll, dla których jest ona kompilowana biblioteki importu.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/NODEFAULTLIB**|   Usuwa co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/NOLOGO**|   Pomija wyświetlanie LIB praw autorskich komunikat i numer wersji i zapobiega wyświetlania pliku polecenia.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|
|**/ OUT**|   Przesłania domyślną nazwę pliku wyjściowego.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/ REMOVE**|   Pomija obiekt z biblioteki wyjściowej.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/SUBSYSTEM**|   Informuje system operacyjny, jak uruchomić program, utworzone przez łączenie z biblioteki wyjściowej.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](../../build/reference/managing-a-library.md).|
|**/VERBOSE**|   Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików .obj, dodawane.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|
|**/WX**|   Traktuj ostrzeżenia jako błędy.<br/><br/>Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](../../build/reference/running-lib.md).|

## <a name="see-also"></a>Zobacz także

[LIB — dokumentacja](../../build/reference/lib-reference.md)<br/>
[Pliki wejściowe LIB](../../build/reference/lib-input-files.md)<br/>
[Pliki wyjściowe LIB](../../build/reference/lib-output-files.md)<br/>
[Inne dane wyjściowe LIB](../../build/reference/other-lib-output.md)<br/>
[Struktura biblioteki](../../build/reference/structure-of-a-library.md)
