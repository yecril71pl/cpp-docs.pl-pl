---
title: Błąd krytyczny C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: f51e93475f104f165895c9d7e2733d741af30502
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389782"
---
# <a name="fatal-error-c1083"></a>Błąd krytyczny C1083

> Nie można *otworzyć pliku* wieloplikowego: "*plik*": *komunikat*

Kompilator generuje błąd C1083, jeśli nie można odnaleźć wymaganego pliku. Istnieje wiele możliwych przyczyn tego błędu. Niepoprawna ścieżka wyszukiwania lub brakujące lub nienazwane pliki nagłówkowe są najbardziej typowymi przyczynami, ale inne typy plików i problemy mogą również powodować C1083. Poniżej przedstawiono niektóre typowe powody, dla których kompilator generuje ten błąd.

## <a name="the-specified-file-name-is-wrong"></a>Określona nazwa pliku jest nieprawidłowa

Być może źle wpisano nazwę pliku. Przykład:

`#include <algorithm.h>`

nie można było znaleźć potrzebnego pliku. Większość plików nagłówkowych standardowej biblioteki C++ nie ma rozszerzenia nazwy pliku. h. \<algorithm>Nagłówek nie zostanie znaleziony przez tę `#include` dyrektywę. Aby rozwiązać ten problem, sprawdź, czy wprowadzono poprawną nazwę pliku, jak w poniższym przykładzie:

`#include <algorithm>`

Niektóre pliki nagłówkowe biblioteki wykonawczej C znajdują się w podkatalogu standardowego katalogu plików dołączanych. Na przykład, aby dołączyć *`sys/types.h`* , należy uwzględnić *`sys`* nazwę podkatalogu w `#include` dyrektywie:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Plik nie jest uwzględniony w ścieżce wyszukiwania dołączanego

Kompilator nie może odnaleźć pliku przy użyciu reguł wyszukiwania, które są wskazywane przez `#include` lub `#import` dyrektywę. Na przykład, gdy nazwa pliku nagłówka jest ujęta w cudzysłów,

`#include "myincludefile.h"`

oznacza to, że kompilator szuka pliku w tym samym katalogu, który zawiera plik źródłowy, a następnie wyszukuje w innych lokalizacjach określonych przez środowisko kompilacji. Jeśli znaki cudzysłowu zawierają ścieżkę bezwzględną, kompilator szuka pliku tylko w tej lokalizacji. Jeśli znaki cudzysłowu zawierają ścieżkę względną, kompilator szuka pliku w katalogu względem katalogu źródłowego.

Jeśli nazwa jest ujęta w nawiasy kątowe,

`#include <stdio.h>`

Kompilator korzysta ze ścieżki wyszukiwania zdefiniowanej przez środowisko kompilacji, **`/I`** opcję kompilatora, **`/X`** opcję kompilatora i zmienną środowiskową **include** . Aby uzyskać więcej informacji, w tym szczegółowe informacje o kolejności wyszukiwania używanej do znajdowania pliku, zobacz [#include dyrektywie (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) i [#import](../../preprocessor/hash-import-directive-cpp.md).

Jeśli pliki dołączane znajdują się w innym katalogu względem katalogu źródłowego i używasz ścieżki względnej w dyrektywach dołączania, należy użyć podwójnych cudzysłowów zamiast nawiasów ostrych. Na przykład, jeśli plik nagłówka *`myheader.h`* znajduje się w podkatalogu ze źródłami projektu o nazwie Headers, ten przykład nie będzie mógł znaleźć pliku i spowoduje C1083:

`#include <headers\myheader.h>`

ale w tym przykładzie działa:

`#include "headers\myheader.h"`

Ścieżek względnych można również używać z katalogami w ścieżce wyszukiwania dołączania. W przypadku dodania katalogu do zmiennej środowiskowej **include** lub ścieżki **katalogów dołączanych** w programie Visual Studio, nie należy również dodawać części ścieżki do dyrektyw include. Na przykład, jeśli nagłówek znajduje się w lokalizacji *`\path\example\headers\myheader.h`* i dodasz *`\path\example\headers\`* do ścieżki **katalogów include** w programie Visual Studio, ale `#include` dyrektywa odwołuje się do pliku jako

`#include <headers\myheader.h>`

plik nie zostanie znaleziony. Użyj poprawnej ścieżki względem katalogu określonego w ścieżce wyszukiwania dołączania. W tym przykładzie można zmienić ścieżkę wyszukiwania dołączania na *`\path\example\`* lub usunąć *`headers\`* segment ścieżki z `#include` dyrektywy.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, rozważ użycie [`vcpkg`](../../vcpkg.md) Menedżera pakietów języka C++, aby zainstalować i skompilować bibliotekę. Program vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports), a także ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Plik znajduje się w projekcie, ale nie ścieżka wyszukiwania dołączania

Nawet wtedy, gdy pliki nagłówkowe są wymienione w **Eksplorator rozwiązań** w ramach projektu, pliki są znajdowane tylko przez kompilator, gdy są one określane przez lub przez `#include` `#import` dyrektywę w pliku źródłowym i znajdują się w ścieżce wyszukiwania dołączania. Różne rodzaje kompilacji mogą używać różnych ścieżek wyszukiwania. **`/X`** Opcja kompilatora może służyć do wykluczania katalogów ze ścieżki wyszukiwania dołączania. Dzięki temu różne kompilacje mogą stosować różne dołączane pliki, które mają taką samą nazwę, ale są przechowywane w różnych katalogach. Jest to alternatywa dla kompilacji warunkowej przy użyciu poleceń preprocesora. Aby uzyskać więcej informacji na temat **`/X`** opcji kompilatora, zobacz [ `/X` (Ignoruj standardowe ścieżki dołączane)](../../build/reference/x-ignore-standard-include-paths.md).

Aby rozwiązać ten problem, popraw ścieżkę, której kompilator używa do wyszukiwania dołączanego lub importowanego pliku. Nowy projekt używa domyślnych ścieżek wyszukiwania dołączania. Może być konieczne zmodyfikowanie ścieżki wyszukiwania dołączania, aby dodać katalog dla projektu. Jeśli kompilujesz w wierszu polecenia, Dodaj ścieżkę do zmiennej środowiskowej **include** lub **`/I`** opcji kompilatora, aby określić ścieżkę do pliku.

Aby ustawić ścieżkę katalogu dołączania w programie Visual Studio, Otwórz okno dialogowe **strony właściwości** projektu. Wybierz pozycję **Katalogi VC + +** w obszarze **Właściwości konfiguracji** w okienku po lewej stronie, a następnie Edytuj Właściwość **Dołącz katalogi** . Aby uzyskać więcej informacji na temat katalogów dla poszczególnych użytkowników i poszczególnych projektów przeszukiwanych przez kompilator w programie Visual Studio, zobacz [stronę właściwości katalogów VC + +](../../build/reference/vcpp-directories-property-page.md). Aby uzyskać więcej informacji na temat **`/I`** opcji kompilatora, zobacz [ `/I` (Dodatkowe katalogi dołączane)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>Nie ustawiono środowiska INCLUDE lub LIB wiersza polecenia.

Gdy kompilator jest wywoływany w wierszu polecenia, do określania ścieżek wyszukiwania zwykle używa się zmiennych środowiskowych. Jeśli ścieżka wyszukiwania opisana przez zmienną środowiskową **include** lub **lib** nie jest ustawiona poprawnie, można wygenerować błąd C1083. Zdecydowanie zalecamy użycie skrótu wiersza polecenia dla deweloperów, aby ustawić podstawowe środowisko dla kompilacji wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kompilacja C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md). Aby uzyskać więcej informacji o sposobach używania zmiennych środowiskowych, zobacz [How to: use Environment w Build](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Plik może być zablokowany lub w użyciu

Jeśli używasz innego programu do edytowania lub uzyskiwania dostępu do pliku, może on mieć zablokowany plik. Spróbuj zamknąć plik w innym programie. Czasami inny program może być programem Visual Studio, jeśli używasz opcji kompilacji równoległej. Jeśli wyłączysz opcję kompilowania równoległego, spowoduje to problem. Przyczyną tego problemu mogą być również inne równoległe systemy kompilacji. Należy zachować ostrożność, aby ustawić zależności między plikami i projektami, aby kolejność kompilacji była poprawna. W niektórych przypadkach należy rozważyć utworzenie projektu pośredniego w celu wymuszenia kolejności zależności kompilacji dla wspólnego pliku, który może być skompilowany przez wiele projektów. Czasami program antywirusowy tymczasowo blokuje ostatnio zmienione pliki do skanowania. Jeśli to możliwe, należy rozważyć wykluczenie katalogów kompilacji projektu ze skanera antywirusowego.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Dołączana jest niewłaściwa wersja nazwy pliku

Błąd C1083 może również wskazywać, że dołączana jest niewłaściwa wersja pliku. Na przykład kompilacja może zawierać niewłaściwą wersję pliku, który ma `#include` dyrektywę dla pliku nagłówkowego, który nie jest przeznaczony dla tej kompilacji. Na przykład niektóre pliki mogą dotyczyć tylko kompilacji x86 lub do debugowania kompilacji. Gdy plik nagłówkowy nie zostanie znaleziony, kompilator generuje błąd C1083. Aby rozwiązać ten problem, użyj właściwego pliku zamiast dodawać plik nagłówkowy lub katalog do kompilacji.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Wstępnie skompilowane nagłówki nie są jeszcze wstępnie skompilowane

Jeśli projekt jest skonfigurowany do używania prekompilowanych nagłówków, należy *`.pch`* utworzyć odpowiednie pliki, tak aby pliki korzystające z zawartości nagłówka mogły być kompilowane. Na przykład *`pch.cpp`* plik ( *`stdafx.cpp`* w programie Visual Studio 2017 i starsze) jest automatycznie tworzony w katalogu projektu dla nowych projektów. Najpierw skompiluj ten plik, aby utworzyć wstępnie skompilowane pliki nagłówkowe. W typowym projekcie procesu kompilacji jest to wykonywane automatycznie. Aby uzyskać więcej informacji, zobacz [Tworzenie prekompilowanych plików nagłówkowych](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Inne przyczyny

- Zainstalowano zestaw SDK lub bibliotekę innych firm, ale nie otwarto nowego okna wiersza polecenia dewelopera po zainstalowaniu zestawu SDK lub biblioteki. Jeśli zestaw SDK lub biblioteka dodaje pliki do ścieżki **dołączania** , może być konieczne otwarcie nowego okna wiersza polecenia dewelopera, aby pobrać te zmiany zmiennych środowiskowych.

- Plik używa kodu zarządzanego, ale nie określono opcji kompilatora **`/clr`** . Aby uzyskać więcej informacji, zobacz [ `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

- Plik jest kompilowany przy użyciu innego **`/analyze`** Ustawienia opcji kompilatora, niż służy do prekompilowania nagłówków. Gdy nagłówki projektu są wstępnie skompilowane, wszystkie powinny używać tych samych **`/analyze`** ustawień. Aby uzyskać więcej informacji, zobacz [ `/analyze` (analiza kodu)](../../build/reference/analyze-code-analysis.md).

- Plik lub katalog został utworzony przez podsystem Windows dla systemu Linux, uwzględniania wielkości liter dla katalogu, a określony przypadek ścieżki lub pliku nie pasuje do wielkości liter ścieżki lub pliku na dysku.

- Plik, katalog lub dysk jest tylko do odczytu.

- Program Visual Studio lub narzędzia wiersza polecenia nie mają wystarczających uprawnień do odczytu pliku lub katalogu. Może się tak zdarzyć na przykład wtedy, gdy pliki projektu mają różne własności niż proces z uruchomionym programem Visual Studio lub narzędzia wiersza polecenia. Czasami ten problem można naprawić przez uruchomienie programu Visual Studio lub wiersza polecenia dewelopera jako administrator.

- Nie są wystarczająco dużo uchwytów plików. Zamknij część aplikacji, a następnie skompiluj ponownie. W typowych okolicznościach ten warunek występuje bardzo rzadko. Jednak może wystąpić, gdy duże projekty są kompilowane na komputerze, który ma ograniczoną pamięć fizyczną.

## <a name="example"></a>Przykład

Poniższy przykład generuje błąd C1083, gdy plik nagłówkowy `"test.h"` nie istnieje w katalogu źródłowym ani w ścieżce wyszukiwania dołączania.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Aby uzyskać informacje o sposobach kompilowania projektów C/C++ w środowisku IDE lub w wierszu polecenia oraz informacje na temat ustawiania zmiennych środowiskowych, zobacz [projekty i systemy kompilacji](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Zobacz też

- [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties)
