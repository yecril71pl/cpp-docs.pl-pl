---
title: Błąd krytyczny C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 522bc4a36be59d4e2c9425e50b1238eb9f4aba61
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822200"
---
# <a name="fatal-error-c1083"></a>Błąd krytyczny C1083

> Nie można otworzyć *typ_pliku* pliku: "*pliku*": *wiadomości*

Kompilator generuje błąd C1083, gdy nie można odnaleźć pliku, który wymaga. Istnieje wiele możliwych przyczyn tego błędu. Wyszukiwanie niepoprawne dołączania ścieżki lub brakujące lub misnamed pliki nagłówkowe są najbardziej typowe przyczyny, ale inne typy plików i problemów, również mogą powodować C1083. Poniżej przedstawiono niektóre typowe przyczyny, dlaczego kompilator generuje błąd.

## <a name="the-specified-file-name-is-wrong"></a>Określona nazwa pliku jest nieprawidłowa

Być może źle wpisano nazwę pliku. Na przykład

`#include <algorithm.h>`

nie można było znaleźć potrzebnego pliku. Większość pliki nagłówkowe standardowej biblioteki języka C++ ma rozszerzenie nazwy pliku .h. \<Algorytm > nagłówka nie będzie można znaleźć to `#include` dyrektywy. Aby rozwiązać ten problem, sprawdź wprowadzenia poprawnej nazwy pliku, jak w poniższym przykładzie:

`#include <algorithm>`

Niektóre pliki nagłówkowe biblioteki wykonawczej C znajdują się w podkatalogu standardowego katalogu plików dołączanych. Na przykład, aby uwzględnić sys/types.h, należy dołączyć nazwę podkatalogu sys w `#include` dyrektywy:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Plik nie znajduje się w ścieżce wyszukiwania dołączanych

Kompilator nie może odnaleźć pliku przy użyciu reguł wyszukiwania, które są wskazywane przez `#include` lub `#import` dyrektywy. Na przykład, jeśli nazwa pliku nagłówkowego jest ujęta w znaki cudzysłowu

`#include "myincludefile.h"`

informuje kompilator, aby wyszukać plik w tym samym katalogu, który zawiera plik źródłowy najpierw, a następnie sprawdzać w innych lokalizacjach, określonych przez środowisko kompilacji. Jeśli znaki cudzysłowu zawierają ścieżkę bezwzględną, kompilator szuka pliku tylko w tej lokalizacji. Jeśli znaki cudzysłowu zawierają ścieżkę względną, kompilator szuka pliku w katalogu względem katalogu źródłowego.

Jeśli nazwa jest ujęta w nawiasy kątowe,

`#include <stdio.h>`

Kompilator postępuje ścieżki wyszukiwania, który jest definiowany przez środowisko kompilacji **/I** — opcja kompilatora, **/X** opcję kompilatora i **INCLUDE** zmiennej środowiskowej. Aby uzyskać więcej informacji, w tym szczegółowe informacje na temat kolejności wyszukiwania umożliwia znalezienie pliku, zobacz [#include — dyrektywa (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) i [#import Directive](../../preprocessor/hash-import-directive-cpp.md).

Jeśli pliki dołączania znajdują się w innym katalogu względem katalogu źródłowego i użyj ścieżki względnej w swojej dyrektyw, zamiast nawiasy kątowe, należy używać cudzysłowów. Na przykład jeśli Twoje myheader.h pliku nagłówka znajduje się w podkatalogu źródła projektu o nazwie nagłówków, następnie w tym przykładzie nie powiedzie się znaleźć plik i powoduje, że C1083:

`#include <headers\myheader.h>`

Jednak ten przykład działa:

`#include "headers\myheader.h"`

Ścieżki względnej można również z katalogów na ścieżkę wyszukiwania dołączenia. Jeśli możesz dodać katalog do **INCLUDE** zmiennej środowiskowej lub do Twojego **Dołącz katalogi** ścieżki w programie Visual Studio, nie należy również dodawać części ścieżki do dyrektywy include. Na przykład, jeśli nagłówek znajduje się w folderze \path\example\headers\myheader.h i Dodaj \path\example\headers\ do Twojej **Dołącz katalogi** ścieżki w programie Visual Studio, Twoja `#include` dyrektywy odwołuje się do pliku jako

`#include <headers\myheader.h>`

następnie nie znaleziono pliku. Użyj poprawnej ścieżki względem katalogu wskazanym na ścieżkę wyszukiwania dołączenia. W tym przykładzie można zmienić ścieżkę wyszukiwania dołączenia do \path\example\, lub Usuń segment ścieżki headers\ z `#include` dyrektywy.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteki innych firm i Vcpkg

Jeśli zostanie wyświetlony ten błąd, jeśli próbujesz skonfigurować biblioteki innych firm w ramach kompilacji, należy rozważyć użycie [Vcpkg](../../vcpkg.md), do Visual C++ Menedżera pakietów, instalowanie i tworzenie biblioteki. Vcpkg obsługująca duży i rosnący [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports)i ustawia właściwości konfiguracji i zależności wymagane do pomyślnej kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz powiązane [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) wpis.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Plik znajduje się w projekcie, ale nie ścieżkę wyszukiwania dołączenia

Nawet kiedy pliki nagłówkowe są wymienione w **Eksploratora rozwiązań** w ramach projektu, pliki mogą znajdować się tylko przez kompilator, gdy są one określone przez `#include` lub `#import` dyrektywy w źródle pliku i znajdują się w Ścieżka wyszukiwania plików dołączanych. Różne rodzaje kompilacji mogą używać różnych ścieżek wyszukiwania. **/X** — opcja kompilatora może służyć do wykluczać katalogi ze ścieżki wyszukiwania dołączanych. Dzięki temu różne kompilacje mogą stosować różne dołączane pliki, które mają taką samą nazwę, ale są przechowywane w różnych katalogach. Jest to alternatywa dla kompilacji warunkowej przy użyciu poleceń preprocesora. Aby uzyskać więcej informacji na temat **/X** — opcja kompilatora, zobacz [/X (Ignoruj standardowe ścieżki dołączanych plików)](../../build/reference/x-ignore-standard-include-paths.md).

Aby rozwiązać ten problem, popraw ścieżkę, której kompilator używa do wyszukiwania dołączanego lub importowanego pliku. Nowy projekt domyślny używa ścieżki wyszukiwania załączonych elementów. Może być konieczne zmodyfikowanie ścieżkę wyszukiwania dołączenia, aby dodać katalog dla projektu. Jeśli kompilujesz w wierszu polecenia, należy dodać ścieżkę do **INCLUDE** zmiennej środowiskowej lub **/I** opcję kompilatora, aby określić ścieżkę do pliku.

Aby ustawić ścieżkę katalogu plików dołączanych w Visual Studio, otwórz projekt **stron właściwości** okno dialogowe. Wybierz **katalogi VC ++** w obszarze **właściwości konfiguracji** w okienku po lewej stronie, a następnie Edytuj **Dołącz katalogi** właściwości. Aby uzyskać więcej informacji na temat na użytkownika i na projekt, przeszukiwanych przez kompilator w programie Visual Studio, zobacz [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md). Aby uzyskać więcej informacji na temat **/I** — opcja kompilatora, zobacz [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>Nie ustawiono wiersza polecenia INCLUDE lub środowiska LIB

Gdy kompilator jest wywoływany w wierszu polecenia, do określania ścieżek wyszukiwania zwykle używa się zmiennych środowiskowych. Jeśli ścieżka wyszukiwania opisana przez **INCLUDE** lub **LIB** zmienna środowiskowa nie jest ustawiona poprawnie, może zostać wygenerowany błąd C1083. Zdecydowanie zalecamy używania skrót do wiersza polecenia dla deweloperów, aby ustawić podstawowe środowisko wiersza polecenia kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacji C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md). Aby uzyskać więcej informacji o sposobie używania zmiennych środowiskowych, zobacz [jak: Użycie zmiennych środowiskowych w kompilacji](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Plik może być zablokowany lub w użyciu

Jeśli używasz innego programu do edycji lub uzyskać dostępu do pliku, może mieć plik jest zablokowany. Spróbuj zamknąć plik w innym programie. Czasami inny program może być Visual Studio, korzystając z opcji kompilacji równoległych. Jeśli wyłączenie opcji kompilacji równoległych sprawia, że błąd znika, a następnie na tym polega problem. Inne systemy równoległych kompilacji może być również ten problem. Uważaj ustawić zależności projektu i pliku, tak, aby kompilacja — kolejność jest poprawna. W niektórych przypadkach należy rozważyć utworzenie pośrednich projektu, aby wymusić kolejność zależności kompilacji dla wspólnego pliku, który może być kompilowany do wielu projektów. Programy antywirusowe czasami tymczasowo zablokować ostatnio zmienionych plików do przeskanowania. Jeśli to możliwe należy rozważyć wykluczenie katalogów kompilacji projektu za pomocą skanera oprogramowania antywirusowego.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Dołączana jest niewłaściwa wersja nazwy pliku

Błąd C1083 może również wskazywać, że dołączana jest niewłaściwa wersja pliku. Na przykład, kompilacja dołącza niewłaściwą wersję pliku, który ma `#include` dyrektywy w poszukiwaniu pliku nagłówkowego nieprzeznaczonego dla tej kompilacji. Na przykład, niektóre pliki mogą dotyczą tylko x86 kompilacji, lub do kompilacji do debugowania. Gdy plik nagłówkowy nie zostanie znaleziony, kompilator generuje błąd C1083. Aby rozwiązać ten problem, użyj właściwego pliku zamiast dodawać plik nagłówkowy lub katalog do kompilacji.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Wstępnie skompilowane nagłówki nie są jeszcze wstępnie skompilowane

Gdy konfigurujesz projekt tak, aby używał wstępnie skompilowanych nagłówków, musisz utworzyć odnośne pliki .pch, aby było możliwe skompilowanie plików, które korzystają z zawartości nagłówków. Na przykład plik stdafx.cpp jest automatycznie tworzony w katalogu projektu dla nowych projektów. Najpierw skompiluj ten plik, aby utworzyć wstępnie skompilowane pliki nagłówkowe. W typowej konstrukcji procesu kompilacji odbywa się to automatycznie. Aby uzyskać więcej informacji, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Inne przyczyny

- Zainstalowany zestaw SDK lub biblioteki innej firmy, ale nie została jeszcze otwarta nowego okna wiersza polecenia dewelopera po zestawie SDK lub biblioteki jest zainstalowany. Jeśli zestaw SDK lub bibliotekę dodaje pliki do **INCLUDE** ścieżki, może być konieczne otwarcie nowego okna wiersza polecenia dla deweloperów, aby pobrać te zmiany zmiennych środowiskowych.

- Plik używa kodu zarządzanego, ale opcja kompilatora **/CLR** nie zostanie określony. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

- Plik został skompilowany przy użyciu innego **/ analyze** ustawienia opcji kompilatora nie jest używany do wstępnej kompilacji nagłówków. Gdy są wstępnie skompilowane nagłówki dla projektu, wszystkie powinny używać tego samego **/ analyze** ustawienia. Aby uzyskać więcej informacji, zobacz [/ analyze (analiza kodu)](../../build/reference/analyze-code-analysis.md).

- Plik lub katalog został utworzony przez podsystem Windows dla systemu Linux, włączono rozróżnianie wielkości liter dla katalogu, a w przypadku określonego pliku lub ścieżki będzie niezgodna z wielkością liter, ścieżki lub plik na dysku.

- Plik, katalog lub dysk jest tylko do odczytu.

- Visual Studio lub narzędzia wiersza polecenia nie ma wystarczających uprawnień do odczytu pliku lub katalogu. Może to nastąpić, na przykład, jeśli pliki projektu mają własności innej niż proces uruchamiania programu Visual Studio lub narzędzia wiersza polecenia. Czasami ten problem, mogą zostać naprawione przez uruchomienie programu Visual Studio lub wiersza polecenia dewelopera jako Administrator.

- Nie są wystarczająco dużo uchwytów plików. Zamknij część aplikacji, a następnie skompiluj ponownie. W typowych okolicznościach ten warunek występuje bardzo rzadko. Jednak może wystąpić, gdy duże projekty są kompilowane na komputerze, który ma ograniczoną pamięć fizyczną.

## <a name="example"></a>Przykład

Poniższy przykład generuje błąd C1083 gdy plik nagłówkowy `"test.h"` nie istnieje w katalogu źródłowym lub na ścieżkę wyszukiwania dołączenia.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Aby uzyskać informacje dotyczące sposobu tworzenia projektów C/C++ w IDE lub w wierszu polecenia, a informacje dotyczące ustawiania zmiennych środowiskowych, zobacz [projektów i systemów kompilacji](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Zobacz także

- [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties)
