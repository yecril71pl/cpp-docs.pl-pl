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

W tym temacie opisano najlepsze rozwiązania dotyczące organizowania plików wyjściowych projektu. Błędy kompilacji mogą wystąpić podczas niepoprawnej konfiguracji plików wyjściowych projektu. W tym temacie opisano również zalety i wady każdej alternatywy do organizowania plików wyjściowych projektu.

## <a name="referencing-clr-assemblies"></a>Odwoływanie się do zespołów CLR

#### <a name="to-reference-assemblies-with-using"></a>Aby odwoływać się do zestawów za pomocą #using

1. Zestaw można odwoływać się bezpośrednio z kodu przy użyciu dyrektywy `#using <System.Data.dll>`#using, takiej jak . Aby uzyskać więcej informacji, zobacz [#using dyrektywy](../preprocessor/hash-using-directive-cpp.md).

   Określony plik może być .dll, .exe, .netmodule lub .obj, o ile jest w MSIL. Składnik, do którego istnieje odwołanie, można zbudować w dowolnym języku. Korzystając z tej opcji, będziesz mieć dostęp do IntelliSense, ponieważ metadane zostaną wyodrębnione z MSIL. Plik, o który mowa, musi znajdować się na ścieżce dla projektu; w przeciwnym razie projekt nie zostanie skompilowany i IntelliSense nie będzie dostępny. Łatwym sposobem określenia, czy plik znajduje się na ścieżce, jest kliknięcie prawym przyciskiem myszy wiersza #using i wybranie polecenia **Otwórz dokument.** Zostaniesz powiadomiony, jeśli nie można znaleźć pliku.

   Jeśli nie chcesz umieszczać pełnej ścieżki do pliku, możesz użyć opcji kompilatora **/AI,** aby edytować ścieżkę wyszukiwania dla odwołań #using. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych).](reference/ai-specify-metadata-directories.md)

#### <a name="to-reference-assemblies-with-fu"></a>Aby odwołać się do zespołów z /FU

1. Zamiast odwoływać się do zestawu bezpośrednio z pliku kodu, jak opisano powyżej, można użyć opcji kompilatora **/FU.** Zaletą tej metody jest to, że nie trzeba dodawać oddzielną instrukcję #using do każdego pliku, który odwołuje się do danego zestawu.

   Aby ustawić tę opcję, otwórz **strony Właściwości** dla projektu. Rozwiń węzeł **Właściwości konfiguracji,** a następnie rozwiń węzeł **C/C++** i wybierz pozycję **Zaawansowane**. Dodaj żądane złożenia obok pozycji **Wymuś #using**. Aby uzyskać więcej informacji, zobacz [/FU (Nazwa wymuszona #using pliku)](reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Aby odwołać się do zestawów za pomocą dodaj nowe odniesienie

1. Jest to najprostszy sposób użycia zestawów CLR. Najpierw upewnij się, że projekt jest skompilowany za pomocą opcji kompilatora **/clr.** Następnie kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj**, **Odwołania**. Zostanie wyświetlone okno dialogowe **Strony właściwości.**

1. W oknie dialogowym **Strony właściwości** wybierz pozycję Dodaj **nowe odniesienie**. Pojawi się okno dialogowe z listą wszystkich .NET, COM i innych zestawów dostępnych w bieżącym projekcie. Wybierz żądany zespół i kliknij przycisk **OK**.

   Po ustawieniu odwołania do projektu odpowiednie zależności są obsługiwane automatycznie. Ponadto ponieważ metadane są częścią zestawu, nie ma potrzeby dodawania pliku nagłówka lub prototypu elementów, które są używane z zarządzanych zestawów.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odwoływanie się do natywnych bibliotek DLL lub bibliotek statycznych

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Aby odwoływać się do natywnych bibliotek DLL lub bibliotek statycznych

1. Odwołaj się do odpowiedniego pliku nagłówka w kodzie przy użyciu dyrektywy #include. Plik nagłówka musi znajdować się w ścieżce dołączania lub części bieżącego projektu. Aby uzyskać więcej informacji, zobacz [#include dyrektywy (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Można również ustawić zależności projektu. Ustawianie zależności projektu gwarantuje dwie rzeczy. Po pierwsze zapewnia, że projekty są budowane w odpowiedniej kolejności, dzięki czemu projekt zawsze można znaleźć pliki zależne, których potrzebuje. Po drugie niejawnie dodaje katalog wyjściowy projektu zależnego do ścieżki, dzięki czemu pliki można łatwo znaleźć w czasie łącza.

1. Aby wdrożyć aplikację, należy umieścić bibliotekę DLL w odpowiednim miejscu. Może to być jedna z następujących czynności:

   1. Ta sama ścieżka co plik wykonywalny.

   1. W dowolnym miejscu ścieżki systemowej (zmienna środowiskowa **ścieżki).**

   1. W zespole side-by-side. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów C/C++ side-by-side](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Praca z wieloma projektami

Domyślnie projekty są tworzone w taki sposób, że wszystkie pliki wyjściowe są tworzone w podkatalogu katalogu projektu. Nazwa katalogu jest oparta na konfiguracji kompilacji (np. debugowania lub wydania). Aby projekty równorzędne odwoływały się do siebie nawzajem, każdy projekt musi jawnie dodać inne katalogi danych wyjściowych projektu do ich ścieżki, aby łączenie zakończyło się pomyślnie. Odbywa się to automatycznie po ustawieniu zależności projektu. Jednak jeśli nie używasz zależności, należy dokładnie obsłużyć to, ponieważ kompilacje mogą stać się bardzo trudne do zarządzania. Na przykład, gdy projekt ma konfiguracje debugowania i wydania i zawiera bibliotekę zewnętrzną z projektu równorzędnego, należy użyć innego pliku biblioteki w zależności od konfiguracji, która jest budowana. W związku z tym, twarde kodowanie tych ścieżek może być trudne.

Wszystkie niezbędne pliki wyjściowe (takie jak pliki wykonywalne, pliki konsolidatora przyrostowego i pliki PDB) są kopiowane do wspólnego katalogu rozwiązań. W związku z tym podczas pracy z rozwiązaniem, które zawiera wiele projektów języka C++ z równoważnych konfiguracji, wszystkie pliki wyjściowe są scentralizowane dla uproszczonego łączenia i wdrażania. Możesz mieć pewność, że ich aplikacja/biblioteka będzie działać zgodnie z oczekiwaniami, jeśli przechowują te pliki razem (ponieważ pliki są gwarantowane, aby znajdować się w ścieżce).

Lokalizacja plików wyjściowych może być poważnym problemem podczas wdrażania w środowisku produkcyjnym. Podczas uruchamiania projektów w IDE ścieżki do dołączonych bibliotek nie muszą być takie same jak w środowisku produkcyjnym. Na przykład jeśli `#using "../../lib/debug/mylib.dll"` masz w kodzie, ale następnie wdrożyć mylib.dll w innej pozycji względnej, aplikacja zakończy się niepowodzeniem w czasie wykonywania. Aby temu zapobiec, należy unikać używania ścieżek względnych w #include instrukcji w kodzie. Lepiej jest upewnić się, że niezbędne pliki znajdują się w ścieżce kompilacji projektu i podobnie zapewniając, że odpowiednie pliki produkcyjne są prawidłowo umieszczone.

#### <a name="how-to-specify-where-output-files-go"></a>Jak określić, gdzie trafiają pliki wyjściowe

1. Lokalizację ustawień wyjściowych projektu można znaleźć na **stronach właściwości**projektu . Rozwiń węzeł obok **pozycji Właściwości konfiguracji** i wybierz pozycję **Ogólne**. Lokalizacja danych wyjściowych jest określona obok pozycji **Katalog wyjściowy**. Aby uzyskać więcej informacji, zobacz [Strona właściwości ogólnych (projekt)](reference/general-property-page-project.md).

## <a name="see-also"></a>Zobacz też

[Typy projektów języka C++ w programie Visual Studio](reference/visual-cpp-project-types.md)
