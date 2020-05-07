---
title: 'Porady: porządkowanie plików wyjściowych projektu dla kompilacji'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: 13aa3d1f8e2993ca34163ecbc0515948db56eb79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328531"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Porady: porządkowanie plików wyjściowych projektu dla kompilacji

W tym temacie opisano najlepsze rozwiązania dotyczące organizowania plików wyjściowych projektu. Błędy kompilacji mogą wystąpić po niepoprawnym skonfigurowaniu plików wyjściowych projektu. W tym temacie przedstawiono również zalety i wady każdej alternatywy do organizowania plików wyjściowych projektu.

## <a name="referencing-clr-assemblies"></a>Odwołania do zestawów CLR

#### <a name="to-reference-assemblies-with-using"></a>Aby odwoływać się do zestawów za pomocą #using

1. Można odwołać się do zestawu bezpośrednio z kodu za pomocą dyrektywy #using, takiej jak `#using <System.Data.dll>`. Aby uzyskać więcej informacji, zobacz [#using dyrektywie](../preprocessor/hash-using-directive-cpp.md).

   Określony plik może być rozszerzeniem dll, exe,. webmodule lub obj, o ile jest w języku MSIL. Składnik, do którego istnieje odwołanie, można skompilować w dowolnym języku. Korzystając z tej opcji, będziesz mieć dostęp do technologii IntelliSense, ponieważ metadane zostaną wyodrębnione z MSIL. Dany plik musi być w ścieżce dla projektu; w przeciwnym razie projekt nie zostanie skompilowany i technologia IntelliSense nie będzie dostępna. Aby łatwo określić, czy plik znajduje się w ścieżce, kliknij prawym przyciskiem myszy wiersz #using i wybierz polecenie **Otwórz dokument** . Użytkownik zostanie powiadomiony, jeśli nie można znaleźć pliku.

   Jeśli nie chcesz umieszczać pełnej ścieżki do pliku, możesz użyć opcji kompilatora **/AI** , aby edytować ścieżkę wyszukiwania #using odwołań. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Aby odwoływać się do zestawów za pomocą/FU

1. Zamiast odwoływać się do zestawu bezpośrednio z pliku kodu, jak opisano powyżej, można użyć opcji kompilatora **/Fu** . Zalety tej metody polegają na tym, że nie trzeba dodawać oddzielnej instrukcji #using do każdego pliku, który odwołuje się do danego zestawu.

   Aby ustawić tę opcję, Otwórz **strony właściwości** projektu. Rozwiń węzeł **Właściwości konfiguracji** , a następnie rozwiń węzeł **C/C++** i wybierz pozycję **Zaawansowane**. Dodaj żądane zestawy obok **Wymuszenia #using**. Aby uzyskać więcej informacji, zobacz [/Fu (nazwa pliku wymuszonego #using)](reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Aby odwołać się do zestawów za pomocą Dodaj nowe odwołanie

1. Jest to najprostszy sposób na korzystanie z zestawów CLR. Najpierw upewnij się, że projekt został skompilowany przy użyciu opcji kompilatora **/CLR** . Następnie kliknij prawym przyciskiem myszy projekt z **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **odwołania**. Zostanie wyświetlone okno dialogowe **strony właściwości** .

1. W oknie dialogowym **strony właściwości** wybierz pozycję **Dodaj nowe odwołanie**. Zostanie wyświetlone okno dialogowe z listą wszystkich platform .NET, COM i innych dostępnych w bieżącym projekcie. Wybierz odpowiedni zestaw i kliknij przycisk **OK**.

   Po ustawieniu odwołania projektu odpowiednie zależności są automatycznie obsługiwane. Ponadto, ponieważ metadane są częścią zestawu, nie ma potrzeby dodawania pliku nagłówkowego ani prototypu elementów, które są używane z zestawów zarządzanych.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odwoływanie się do macierzystych bibliotek DLL lub bibliotek statycznych

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Aby odwoływać się do macierzystych bibliotek DLL lub bibliotek statycznych

1. Odwołuje się do odpowiedniego pliku nagłówkowego w kodzie za pomocą dyrektywy #include. Plik nagłówkowy musi znajdować się w ścieżce include lub w części bieżącego projektu. Aby uzyskać więcej informacji, zobacz [#include dyrektywie (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Można również ustawić zależności projektu. Ustawienie zależności projektu gwarantuje dwie rzeczy. Najpierw zapewnia, że projekty są kompilowane w odpowiedniej kolejności, tak aby projekt zawsze znajdował potrzebne pliki zależne. Po drugie niejawnie dodaje katalog wyjściowy projektu zależnego do ścieżki, aby można było łatwo znaleźć pliki w czasie konsolidacji.

1. Aby wdrożyć aplikację, należy umieścić bibliotekę DLL w odpowiednim miejscu. Może to być jedna z następujących:

   1. Ta sama ścieżka, w której znajduje się plik wykonywalny.

   1. Gdziekolwiek w ścieżce systemowej (zmienna środowiskowa **Path** ).

   1. W zestawie równoległym. Aby uzyskać więcej informacji, zobacz [Kompilowanie równoległych zestawów C/C++](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Praca z wieloma projektami

Domyślnie projekty są kompilowane w taki sposób, że wszystkie pliki wyjściowe są tworzone w podkatalogu katalogu projektu. Katalog jest nazwany w oparciu o konfigurację kompilacji (np. debugowanie lub wydanie). Aby projekty równorzędne odwołują się do siebie nawzajem, każdy projekt musi jawnie dodać inne katalogi wyjściowe projektu do ich ścieżki w celu pomyślnego nawiązaniu połączenia. Jest to wykonywane automatycznie podczas ustawiania zależności projektu. Niemniej jednak, jeśli nie używasz zależności, należy uważnie obsłużyć ten fakt, ponieważ kompilacje mogą stać się bardzo trudne do zarządzania. Na przykład, gdy projekt ma konfiguracje debugowania i wydania i zawiera zewnętrzną bibliotekę z tego samego projektu, należy użyć innego pliku biblioteki w zależności od tego, która konfiguracja jest skompilowana. Oznacza to, że stałe kodowanie tych ścieżek może być trudne.

Wszystkie podstawowe pliki wyjściowe (takie jak pliki wykonywalne, przyrostowe plików konsolidatora i pliki PDB) są kopiowane do katalogu wspólnego rozwiązania. W ten sposób podczas pracy z rozwiązaniem zawierającym wiele projektów C++ z równoważnymi konfiguracjami wszystkie pliki wyjściowe są scentralizowane dla uproszczonego łączenia i wdrażania. Możesz mieć pewność, że ich aplikacja/biblioteka będzie działać zgodnie z oczekiwaniami, jeśli przechowują te pliki razem (ponieważ pliki są gwarantowane w ścieżce).

Lokalizacja plików wyjściowych może być głównym problemem podczas wdrażania w środowisku produkcyjnym. W przypadku uruchamiania projektów w środowisku IDE ścieżki do dołączonych bibliotek nie muszą być takie same jak w przypadku środowiska produkcyjnego. Na przykład jeśli masz `#using "../../lib/debug/mylib.dll"` w kodzie, a następnie wdróż mylib. dll w innej pozycji względnej, aplikacja zakończy się niepowodzeniem w czasie wykonywania. Aby tego uniknąć, należy unikać używania ścieżek względnych w instrukcji #include w kodzie. Lepszym rozwiązaniem jest upewnienie się, że niezbędne pliki znajdują się w ścieżce kompilacji projektu i w podobny sposób zapewniają, że odpowiednie pliki produkcyjne są prawidłowo umieszczone.

#### <a name="how-to-specify-where-output-files-go"></a>Jak określić miejsce użycia plików wyjściowych

1. Lokalizację ustawień wyjściowych projektu można znaleźć na **stronach właściwości**projektu. Rozwiń węzeł obok pozycji **Właściwości konfiguracji** , a następnie wybierz pozycję **Ogólne**. Lokalizacja wyjściowa jest określana obok **katalogu wyjściowego**. Aby uzyskać więcej informacji, zobacz [Ogólne strony właściwości (projekt)](reference/general-property-page-project.md).

## <a name="see-also"></a>Zobacz też

[Typy projektów C++ w programie Visual Studio](reference/visual-cpp-project-types.md)
