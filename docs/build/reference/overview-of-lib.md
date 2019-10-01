---
title: Omówienie biblioteki LIB
description: Omówienie użycia i opcji narzędzia biblioteki lib. exe.
ms.date: 09/25/2019
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 7223ef0a624cf15c43bd067db8a7919efd27df17
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685492"
---
# <a name="overview-of-lib"></a>Omówienie biblioteki LIB

LIB (lib. exe) tworzy biblioteki standardowe, Importuj biblioteki i pliki eksportu, których można używać z [linkiem](linker-options.md) podczas kompilowania programu. LIB jest uruchamiany z wiersza polecenia.

LIB można używać w następujących trybach:

- [Kompilowanie lub modyfikowanie biblioteki COFF](managing-a-library.md)

- [Wyodrębnianie obiektu elementu członkowskiego do pliku](extracting-a-library-member.md)

- [Tworzenie pliku eksportu i biblioteki importowanej](working-with-import-libraries-and-export-files.md)

Te tryby wzajemnie się wykluczają; LIB można używać tylko w jednym trybie naraz.

## <a name="lib-options"></a>Opcje LIB

W poniższej tabeli wymieniono opcje biblioteki lib. exe z linkiem do dodatkowych informacji.

|Opcja|Opis|
|-|-|
|**/DEF**|Utwórz bibliotekę importu i plik eksportu.<br/><br/>Aby uzyskać więcej informacji, zobacz [Kompilowanie biblioteki importowania i eksportowanie pliku](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**|   Wyślij do firmy Microsoft informacje o błędach wewnętrznych w programie lib. exe.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/EXPORT**|   Eksportuje funkcję z programu.<br/><br/>Aby uzyskać więcej informacji, zobacz [Kompilowanie biblioteki importowania i eksportowanie pliku](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Utwórz plik obiektu (. obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki.<br/><br/>Aby uzyskać więcej informacji, zobacz [wyodrębnianie elementu członkowskiego biblioteki](extracting-a-library-member.md).|
|**/INCLUDE**|   Dodaje symbol do tabeli symboli.<br/><br/>Aby uzyskać więcej informacji, zobacz [Kompilowanie biblioteki importowania i eksportowanie pliku](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Zastępuje ścieżkę biblioteki środowiska.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/LINKREPRO**|   Tworzy artefakty, które są konieczne do odtworzenia pliku lib. exe lub błędu wewnętrznego.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/LINKREPROTARGET**|   Program generuje artefakty **/LINKREPRO** tylko wtedy, gdy lib. exe jest używany z określonym plikiem.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/LIST**|   Wyświetla informacje o bibliotece wyjściowej do wyjścia standardowego.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/LTCG**|   Powoduje, że biblioteka jest skompilowana przy użyciu generowania kodu w czasie konsolidacji.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/MACHINE**|   Określa platformę docelową programu.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/NAME**|   Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki DLL, dla której jest tworzona biblioteka importu.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/NODEFAULTLIB**|   Usuwa co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/NOLOGO**|   Pomija wyświetlanie komunikatu o prawach autorskich LIB i numeru wersji i uniemożliwia echo plików poleceń.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/OUT**|   Przesłania domyślną nazwę pliku wyjściowego.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/REMOVE**|   Pomija obiekt z biblioteki wyjściowej.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/SUBSYSTEM**|   Informuje system operacyjny, jak uruchomić program utworzony przez połączenie z biblioteką wyjściową.<br/><br/>Aby uzyskać więcej informacji, zobacz [Zarządzanie biblioteką](managing-a-library.md).|
|**/VERBOSE**|   Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików. obj, które są dodawane.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|
|**/WX**|   Traktuj ostrzeżenia jako błędy.<br/><br/>Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](running-lib.md).|

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki LIB](lib-reference.md)<br/>
[Pliki wejściowe LIB](lib-input-files.md)<br/>
[Pliki wyjściowe LIB](lib-output-files.md)<br/>
[Inne dane wyjściowe LIB](other-lib-output.md)<br/>
[Struktura biblioteki](structure-of-a-library.md)
