---
title: 'Porady: porządkowanie plików wyjściowych projektu dla kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f139342e7ccb264d89f9012b8177ff57260f3738
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399798"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Porady: porządkowanie plików wyjściowych projektu dla kompilacji

W tym temacie opisano najlepsze metody organizowania plików wyjściowych projektu. Twórz błędy mogą wystąpić, gdy niepoprawna konfiguracja plików wyjściowych projektu. W tym temacie przedstawiono również zalety i wady każdego rozwiązania alternatywnego do organizowania plików danych wyjściowych projektu.

## <a name="referencing-clr-assemblies"></a>Odwoływanie się do zestawów CLR

#### <a name="to-reference-assemblies-with-using"></a>Aby zestawy odwołań przy użyciu #using

1. Odwoływać zestawu bezpośredniego używania w kodzie za pomocą # dyrektywy using, takich jak `#using <System.Data.dll>`. Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).

   Określony plik może być .dll, .exe, .netmodule lub .obj, tak długo, jak jest w MSIL. Wywoływany składnik może być skompilowana w dowolnym języku. Korzystając z tej opcji masz dostęp do technologii IntelliSense, ponieważ metadane zostaną wyodrębnione z MSIL. Dany plik musi być w ścieżce projektu. w przeciwnym razie nie można skompilować projekt i funkcja IntelliSense nie będą dostępne. Kliknij prawym przyciskiem myszy jest łatwym sposobem ustalenia, czy plik znajduje się w ścieżce #using wiersza, a następnie wybierz **otwartym dokumencie** polecenia. Użytkownik będzie powiadamiany, jeśli nie można odnaleźć pliku.

   Jeśli nie chcesz umieścić pełnej ścieżki do pliku, możesz użyć **/AI** opcję kompilatora, aby edytować ścieżkę wyszukiwania dla #using. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Aby odwoływać się do zestawów za pomocą /FU

1. Zamiast odwoływać się do zestawu bezpośrednio z pliku z kodem zgodnie z powyższym opisem, można użyć **/FU** — opcja kompilatora. Zaletą tej metody jest, że nie trzeba dodawać osobnej # instrukcję using do każdego pliku, który odwołuje się do danego zestawu.

   Aby ustawić tę opcję, otwórz **strony właściwości** dla projektu. Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **C/C++** a następnie wybierz węzeł **zaawansowane**. Dodaj żądane zestawy obok **życie #using**. Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Aby odwoływać się do zestawów za pomocą Dodaj nowe odwołanie

1. Jest to najłatwiejszy sposób na używanie zestawów CLR. Najpierw upewnij się, że projekt jest kompilowany za pomocą **/CLR** — opcja kompilatora. Następnie kliknij prawym przyciskiem myszy projekt z **Eksploratora rozwiązań** i wybierz **Dodaj**, **odwołania**. **Stron właściwości** pojawi się okno dialogowe.

1. Z **stron właściwości** okno dialogowe, wybierz opcję **Dodaj nowe odwołanie**. Okno dialogowe pojawi się lista wszystkich .NET, COM i innych podzespołów dostępnych w bieżącym projekcie. Wybierz żądany zestaw i kliknij przycisk **OK**.

   Po ustawieniu odwołanie projektu odpowiadające mu zależności są realizowane automatycznie. Ponadto ponieważ metadane są częścią zestawu, nie ma potrzeby można dodać pliku nagłówkowego ani prototypować elementów, które są używane z zarządzanych zestawów.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odwoływanie się do macierzystych bibliotek DLL lub bibliotek statycznych

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Aby odwoływać się do macierzystych bibliotek DLL lub bibliotek statycznych

1. Odwołanie do odpowiedniego pliku nagłówka w kodzie przy użyciu # dyrektywy include. Plik nagłówka musi być w ścieżce Włącz lub częścią bieżącego projektu. Aby uzyskać więcej informacji, zobacz [#include — dyrektywa (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Można również ustawić zależności projektu. Ustawianie zależności projektu gwarantuje dwie rzeczy. Po pierwsze zapewnia, że projekty są kompilowane w odpowiedniej kolejności, tak aby projekt zawsze znajdował potrzebne pliki zależne. Po drugie niejawnie dodaje katalog wyjściowy projektu zależnego do ścieżki tak, aby pliki można je znaleźć łatwo w czasie konsolidacji.

1. Aby wdrożyć aplikację, należy umieścić biblioteki DLL w odpowiednim miejscu. Może to być jeden z następujących czynności:

   1. Taką samą ścieżkę pliku wykonywalnego.

   1. Gdziekolwiek w ścieżce systemu ( **ścieżki** zmienną środowiskową).

   1. W zestawie side-by-side. Aby uzyskać więcej informacji, zobacz [zestawy języka C/C++ — równoczesne tworzenie](../build/building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Praca z wieloma projektami

Domyślnie projekty są kompilowane w taki sposób, że wszystkie pliki wyjściowe są tworzone w podkatalogu katalogu projektu. Katalog nosi nazwę na podstawie konfiguracji kompilacji (np. Debuguj lub Uwolnij). Aby projekty równorzędne do odwoływania się do siebie nawzajem każdy projekt musi jawnie dodać katalogi wyjściowe innych projektów do swojej ścieżki, aby łączenie powiodło się. Odbywa się to automatycznie po ustawieniu współzależności projektu. Jednak jeśli nie używasz zależności, należy starannie postępować, ponieważ kompilacje mogą stać się bardzo trudne do zarządzania. Na przykład gdy projekt ma konfiguracje Debug i Release, i obejmuje zewnętrzną bibliotekę z innego projektu, należy użyć innego pliku biblioteki w zależności od tego, która jest kompilowana konfiguracja. W związku z tym kodować tych ścieżek może być trudne.

Wszystkie podstawowe pliki wyjściowe (na przykład pliki wykonywalne, przyrostowe pliki konsolidatora i pliki PDB) są kopiowane do katalogu wspólnego rozwiązania. W związku z tym podczas pracy z rozwiązaniem, które zawiera wiele projektów w języku C++ z równoważnymi konfiguracjami, wszystkie pliki wyjściowe są scentralizowane dla uproszczonego łączenia i wdrażania. Można mieć pewność, że aplikacja/Biblioteka będą działać zgodnie z oczekiwaniami, jeśli oni zachować te pliki ze sobą (ponieważ pliki są musi być w ścieżce).

Lokalizacja plików danych wyjściowych może być poważnym problemem podczas wdrażania w środowisku produkcyjnym. Podczas wykonywania projektów w IDE, ścieżki do dołączonych bibliotek niekoniecznie takie same jak w środowisku produkcyjnym. Na przykład, jeśli masz `#using "../../lib/debug/mylib.dll"` w kodzie, ale potem wdrożysz bibliotekę mylib.dll w innym położeniu względnym, aplikacja ulegnie awarii w czasie wykonywania. Aby tego uniknąć, należy unikać używania ścieżek względnych w # instrukcji include w kodzie. Lepiej jest upewnić się, że niezbędne pliki znajdują się w ścieżce kompilowania projektu i podobnie zapewnić, że odpowiadające im pliki produkcyjne są prawidłowo umieszczone.

#### <a name="how-to-specify-where-output-files-go"></a>Jak określić, gdzie trafiają pliki wyjściowe

1. Lokalizacja projektu danych wyjściowych ustawienia można znaleźć w projekcie **stron właściwości**. Rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. Lokalizacja danych wyjściowych jest określona obok **katalog wyjściowy**. Aby uzyskać więcej informacji, zobacz [strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md).

## <a name="see-also"></a>Zobacz też

[Typy projektów Visual C++](../ide/visual-cpp-project-types.md)