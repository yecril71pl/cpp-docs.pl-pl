---
title: "Błąd krytyczny C1083 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1083
dev_langs: C++
helpviewer_keywords: C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bce56a9e90ba8139b55bf013f19af47c587c2472
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1083"></a>Błąd krytyczny C1083

> Nie można otworzyć *filetype* pliku: "*pliku*": *wiadomości*  
  
Kompilator generuje błąd C1083 nie można znaleźć pliku, który wymaga. Istnieje wiele możliwych przyczyn tego błędu. Wyszukiwania include Niepoprawna ścieżka albo brakujące lub misnamed pliki nagłówka są najbardziej typowych przyczyn, ale inne typy plików i problemów może również spowodować C1083. Poniżej przedstawiono niektóre typowe przyczyny, dlaczego kompilator generuje ten błąd.  
  
## <a name="the-specified-file-name-is-wrong"></a>Określona nazwa pliku jest nieprawidłowa 
  
Być może źle wpisano nazwę pliku. Na przykład  

`#include <algorithm.h>`  
  
nie można było znaleźć potrzebnego pliku. Większość pliki nagłówkowe standardowej biblioteki C++ ma rozszerzenie nazwy pliku .h. \<Algorytm > to może nie znaleziono nagłówka `#include` dyrektywy. Aby rozwiązać ten problem, sprawdź, czy podano prawidłową nazwę pliku jest wprowadzony, jak w poniższym przykładzie:  

`#include <algorithm>`
  
Niektóre pliki nagłówkowe biblioteki wykonawczej C znajdują się w podkatalogu standardowego katalogu plików dołączanych. Na przykład, aby uwzględnić sys/types.h, musi zawierać nazwę podkatalogu sys w `#include` dyrektywy:  
  
`#include <sys/types.h>`  

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Plik nie znajduje się w ścieżce wyszukiwania include  
  
Kompilator nie może odnaleźć pliku za pomocą reguł wyszukiwania, które są oznaczone `#include` lub `#import` dyrektywy. Na przykład jeśli nazwa pliku nagłówka jest ujęta w cudzysłów,  
  
`#include "myincludefile.h"`  
  
Ta wartość informuje kompilator, aby wyszukać plik w tym samym katalogu, który zawiera plik źródłowy najpierw, a następnie sprawdź w innych lokalizacjach, określony przez środowisko kompilacji. Jeśli znaki cudzysłowu zawierają ścieżkę bezwzględną, kompilator szuka pliku tylko w tej lokalizacji. Jeśli znaki cudzysłowu zawierają ścieżkę względną, kompilator szuka pliku w katalogu względem katalogu źródłowego. 

Jeśli nazwa jest ujęta w nawiasy,  
  
`#include <stdio.h>`  
  
ścieżki wyszukiwania, która jest definiowana za pomocą środowiska kompilacji, następuje kompilator **/I** — opcja kompilatora, **/X** — opcja kompilatora i **INCLUDE** zmiennej środowiskowej. Aby uzyskać więcej informacji, łącznie konkretne szczegółowe informacje o kolejności wyszukiwania umożliwia znalezienie pliku, zobacz [#include — dyrektywa (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) i [#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md).

Plików dołączanych są w innym katalogu względem katalogu źródłowego i użyć ścieżki względnej w sieci zawiera dyrektywy, należy użyć cudzysłowów zamiast nawiasy. Na przykład jeśli Twoje myheader.h pliku nagłówka podkatalog źródeł projektu o nazwie nagłówków, następnie w tym przykładzie nie uda się znaleźć pliku i powoduje, że C1083:

`#include <headers\myheader.h>`

jednak działa w tym przykładzie:

`#include "headers\myheader.h"`

Można także ścieżek względnych z katalogów na ścieżkę wyszukiwania dyrektywy include. Jeśli dodasz katalog do **INCLUDE** zmiennej środowiskowej lub do Twojej **katalogi dołączenia** ścieżki w programie Visual Studio, nie należy również dodawać części ścieżki do dyrektywy include. Na przykład, jeśli nagłówek znajduje się pod adresem \path\example\headers\myheader.h i dodać \path\example\headers\ do Twojej **katalogi dołączenia** ścieżki w programie Visual Studio, ale Twoje `#include` dyrektywy odwołuje się do pliku
  
`#include <headers\myheader.h>`  

następnie nie odnaleziono pliku. Użyj poprawna ścieżka względna katalogu określonego w ścieżce wyszukiwania include. W tym przykładzie, można zmienić ścieżkę wyszukiwania dyrektywy include na \path\example\, lub usunąć segment ścieżki headers\ z `#include` dyrektywy.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Plik znajduje się w projekcie, ale nie ścieżkę wyszukiwania dyrektywy include

Nawet jeśli pliki nagłówka są wymienione w **Eksploratora rozwiązań** w ramach projektu, pliki mogą znajdować się tylko przez kompilator, gdy są one określone przez `#include` lub `#import` dyrektywy w źródle plików i znajdują się w ścieżki wyszukiwania załączania. Różne rodzaje kompilacji mogą używać różnych ścieżek wyszukiwania. **/X** — opcja kompilatora może służyć do wykluczenia katalogi z ścieżkę wyszukiwania dyrektywy include. Dzięki temu różne kompilacje mogą stosować różne dołączane pliki, które mają taką samą nazwę, ale są przechowywane w różnych katalogach. Jest to alternatywa dla kompilacji warunkowej przy użyciu poleceń preprocesora. Aby uzyskać więcej informacji na temat **/X** — opcja kompilatora, zobacz [/X (Ignoruj standardowe ścieżki dołączanych plików)](../../build/reference/x-ignore-standard-include-paths.md).  
  
Aby rozwiązać ten problem, popraw ścieżkę, której kompilator używa do wyszukiwania dołączanego lub importowanego pliku. Ścieżki wyszukiwania załączonych nowym domyślnym używa projektu. Należy zmodyfikować ścieżkę wyszukiwania dyrektywy include, aby dodać katalog dla projektu. Jeśli kompilacja w wierszu polecenia, Dodaj ścieżkę do **INCLUDE** zmiennej środowiskowej lub **/I** opcję kompilatora, aby określić ścieżkę do pliku. 

Aby ustawić ścieżkę katalogu include w programie Visual Studio, otwórz projekt **strony właściwości** okno dialogowe. Wybierz **katalogi VC ++** w obszarze **właściwości konfiguracji** w okienku po lewej stronie, a następnie Edytuj **katalogi dołączenia** właściwości. Aby uzyskać więcej informacji dotyczących użytkownika i -projekt katalogi przeszukiwane przez kompilator w programie Visual Studio, zobacz [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md). Aby uzyskać więcej informacji na temat **/I** — opcja kompilatora, zobacz [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md).  
  
## <a name="the-command-line-include-environment-is-not-set"></a>Nie ustawiono środowiska Dołącz wiersz polecenia

Gdy kompilator jest wywoływany w wierszu polecenia, do określania ścieżek wyszukiwania zwykle używa się zmiennych środowiskowych. Jeśli ścieżka wyszukiwania opisanego przez **INCLUDE** zmienna środowiskowa nie jest poprawnie ustawiona, może zostać wygenerowany błąd C1083. Stanowczo zaleca się, że kompilacje przy użyciu skrótu wiersza polecenia dewelopera można ustawić podstawowego środowiska dla wiersza polecenia. Aby uzyskać więcej informacji, zobacz zobacz [kompilacji C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md). Aby uzyskać więcej informacji o sposobie używania zmiennych środowiskowych, zobacz [porady: Użyj zmiennych środowiskowych w kompilacji](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).  

## <a name="the-file-may-be-locked-or-in-use"></a>Plik może być zablokowany lub w użyciu

Jeśli używasz innego programu do edycji lub uzyskać dostępu do pliku, może mieć zablokowany plik. Zamknij plik w innym programie. Czasami inny program może być Visual Studio, korzystając z opcji równoległych kompilacji. Jeśli wyłączenie opcji równoległych kompilacji sprawia, że błędu zniknie, a następnie na tym polega problem. Inne systemy równoległych kompilacji może być również ten problem. Należy zachować ostrożność, można ustawić plik do projektu, zależności, kolejność kompilacji jest poprawna. W niektórych przypadkach należy rozważyć utworzenie pośrednich projektu, aby wymusić kolejność zależności kompilacji dla typowych plików, które mogą zostać utworzone przez wiele projektów. Czasami antywirusowych tymczasowo zablokować ostatnio zmienionych plików do przeskanowania. Jeśli to możliwe należy rozważyć wykluczenie katalogów kompilacji projektu z skanera antywirusowego.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Dołączana jest niewłaściwa wersja nazwy pliku  
  
Błąd C1083 może również wskazywać, że dołączana jest niewłaściwa wersja pliku. Na przykład kompilacji może zawierać niewłaściwej wersji pliku, który ma `#include` dyrektywy nagłówek pliku, który nie jest przeznaczony dla tej kompilacji. Na przykład niektóre pliki mogą dotyczyć x86 kompilacje, lub do kompilacji do debugowania. Gdy plik nagłówkowy nie zostanie znaleziony, kompilator generuje błąd C1083. Aby rozwiązać ten problem, użyj właściwego pliku zamiast dodawać plik nagłówkowy lub katalog do kompilacji.  
  
## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Wstępnie skompilowane nagłówki nie są jeszcze wstępnie skompilowane  
  
Gdy konfigurujesz projekt tak, aby używał wstępnie skompilowanych nagłówków, musisz utworzyć odnośne pliki .pch, aby było możliwe skompilowanie plików, które korzystają z zawartości nagłówków. Na przykład plik stdafx.cpp automatycznie jest tworzony w katalogu projektu dla nowych projektów. Najpierw skompiluj ten plik, aby utworzyć wstępnie skompilowane pliki nagłówkowe. W projekcie procesu kompilacji typowe odbywa się to automatycznie. Aby uzyskać więcej informacji, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md).  
  
## <a name="additional-causes"></a>Inne przyczyny  
  
- Zainstalowano zestaw SDK lub biblioteki innych firm, ale nie otwarto nowe okno wiersza polecenia dewelopera po zestawie SDK lub biblioteka jest zainstalowany. Jeśli zestaw SDK lub biblioteki dodaje pliki **INCLUDE** ścieżki, należy otworzyć nowe okno wiersza polecenia dewelopera, aby pobrać te zmiany zmiennej środowiskowej.

- Plik korzysta z kodu zarządzanego, ale opcja kompilatora **/CLR** nie jest określona. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
- Plik został skompilowany przy użyciu innej **/ analyze** opcji kompilatora od wstępnej kompilacji nagłówków. Gdy są prekompilowanych nagłówków dla projektu, wszystkie powinny używać tego samego **/ analyze** ustawienia. Aby uzyskać więcej informacji, zobacz [/ analyze (analiza kodu)](../../build/reference/analyze-code-analysis.md).  
  
- Plik, katalog lub dysk jest tylko do odczytu.  
  
- Visual Studio lub narzędzia wiersza polecenia nie masz wystarczających uprawnień do odczytu pliku lub katalogu. Może to nastąpić, na przykład, jeśli pliki projektu własność innego niż procesu uruchamiania programu Visual Studio lub narzędzia wiersza polecenia. Czasami ten problem można naprawić, uruchamiając program Visual Studio lub z wiersza polecenia dewelopera jako Administrator.  
  
- Nie są wystarczająco dużo uchwytów plików. Zamknij część aplikacji, a następnie skompiluj ponownie. W typowych okolicznościach ten warunek występuje bardzo rzadko. Jednak może wystąpić, gdy duże projekty są kompilowane na komputerze, który ma ograniczoną pamięć fizyczną.  
  
## <a name="example"></a>Przykład

Poniższy przykład generowany jest błąd C1083 podczas plik nagłówka `"test.h"` nie istnieje w katalogu źródłowym lub na ścieżkę wyszukiwania dyrektywy include.  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"  // OK  
```  
  
Aby uzyskać informacje dotyczące sposobu tworzenia projektów C/C++ w środowisku IDE lub w wierszu polecenia i informacji na temat ustawiania zmiennych środowiskowych, zobacz [kompilowanie programów C/C++](../../build/building-c-cpp-programs.md).
 
## <a name="see-also"></a>Zobacz też

[Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties)