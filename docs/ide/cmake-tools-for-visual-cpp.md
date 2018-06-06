---
title: CMake projekty w programie Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/08/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3a65ae6cc58f649fee5f47b33a146263a3b6c55
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337434"
---
# <a name="cmake-projects-in-visual-c"></a>CMake projekty w programie Visual C++

W tym artykule przyjęto założenie, że czytelnik zna CMake, narzędzia i platform, open source do definiowania kompilacji procesy uruchomione na wielu platformach.

Niedawna użytkowników programu Visual Studio może użyć CMake generuje pliki projektu MSBuild, które IDE następnie używane przez funkcję IntelliSense, przeglądanie i kompilacji. W programie Visual Studio 2017 r. **Visual C++ Tools dla CMake** składnik używa **Otwórz Folder** funkcję, aby umożliwić IDE korzystają z plików projektu CMake (na przykład CMakeLists.txt) bezpośrednio do celów IntelliSense i przeglądania. Jeśli używasz programu Visual Studio generator pliku tymczasowego projektu jest generowana i przekazany do msbuild.exe, ale nigdy nie jest załadowany dla IntelliSense i przeglądania. 

**Visual Studio 2017 wersji 15 ustęp 3**: Pomoc techniczna jest świadczona dla generatory zarówno Nindżą, jak i programu Visual Studio.

**Visual Studio 2017 wersji 15.4**: Dodano obsługę CMake w systemie Linux. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake Linux](../linux/cmake-linux-project.md).

**Visual Studio 2017 wersji 15,5 cala**: importowanie istniejących pamięci podręcznej CMake dodano obsługę. Visual Studio automatycznie wyodrębnia niestandardowe zmienne i tworzy plik CMakeSettings.json wstępnie wypełnione.


## <a name="installation"></a>Instalacja

**Narzędzia Visual C++ Tools for CMake** jest instalowany domyślnie w ramach **tworzenia klasycznych aplikacji w języku C++** obciążenia.

![Składnik CMake obciążenia pracą pulpitu C++](media/cmake-install.png)
 
## <a name="ide-integration"></a>Integracja środowiska IDE

Po wybraniu **pliku | Otwórz | Folder** aby otworzyć folder zawierający plik CMakeLists.txt, stanie następujących czynności:

- Dodaje programu Visual Studio **CMake** element menu do menu głównego, z poleceniami do wyświetlania i edytowania CMake skryptów.
- **Eksplorator rozwiązań** Wyświetla struktury folderów i plików.
- Program Visual Studio działa CMake.exe i generuje CMake pamięci podręcznej dla domyślnej *konfiguracji*, która jest x86 debugowania. W wierszu polecenia CMake jest wyświetlany w **okno danych wyjściowych**, oraz dodatkowe dane wyjściowe z CMake.
- W tle Visual Studio rozpoczyna indeksu plików źródłowych, aby włączyć IntelliSense, przeglądanie informacji, refaktoryzacji i tak dalej. Podczas pracy programu Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować synchronizację ze źródłami jej indeks.
 
Możesz otworzyć foldery zawierające dowolną liczbę CMake projektów. Visual Studio wykrywa i konfiguruje wszystkie pliki CMakeLists.txt "root" w obszarze roboczym. Operacje CMake (Konfigurowanie, tworzenie, debugowanie) również C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![Projekt CMake z wielu elementów głównych](media/cmake-multiple-roots.png) 

## <a name="import-an-existing-cache"></a>Importuj istniejący pamięci podręcznej

Podczas importowania istniejącego pliku CMakeCache.txt programu Visual Studio automatycznie wyodrębnia niestandardowe zmienne i tworzy plik wstępnie wypełnione CMakeSettings.json na ich podstawie. Oryginalny pamięci podręcznej nie jest modyfikowany w jakikolwiek sposób i nadal może być używany, z poziomu wiersza polecenia lub z dowolnego narzędzia lub IDE zostało użyte do wygenerowania. Nowy plik CMakeSettings.json jest umieszczana wzdłuż głównego projektu CMakeLists.txt. Visual Studio generuje nowy plik ustawień na podstawie pamięci podręcznej. Nie wszystkie elementy w pamięci podręcznej zostaną zaimportowane.  Właściwości, takie jak generator i lokalizację kompilatory są zastępowane wartości domyślne, które działają prawidłowo w IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejący pamięci podręcznej

1. W menu głównym wybierz **pliku | Otwórz | CMake**:

   ![Otwórz CMake](media/cmake-file-open.png "pliku, Otwórz, CMake") 

   Spowoduje to wyświetlenie **CMake importu z pamięci podręcznej** kreatora. 
   
2. Przejdź do pliku CMakeCache.txt, który chcesz zaimportować, a następnie kliknij przycisk **OK**. **Importowanie CMake projektu z pamięci podręcznej** zostanie wyświetlony Kreator:

   ![Importuj pamięci podręcznej CMake](media/cmake-import-wizard.png "Otwórz kreatora CMake importu pamięci podręcznej") 

   Po zakończeniu działania kreatora można wyświetlić nowy plik CMakeCache.txt w **Eksploratora rozwiązań** obok głównego pliku CMakeLists.txt w projekcie.


## <a name="building-cmake-projects"></a>Kompilowanie projektów CMake

Aby utworzyć projekt CMake, masz tych opcji:

1. Wybierz obiekt docelowy w **debugowania** listy rozwijanej i naciśnij klawisz **F5**, lub kliknij przycisk **Uruchom** (zielony) trójkąt. Projekt automatycznie tworzy, podobnie jak rozwiązania Visual Studio.
1. Kliknij prawym przyciskiem myszy na CMakeLists.txt i wybierz **kompilacji** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderu, użytkownik może kompilacji wszystkie lub tylko jeden określony element docelowy, lub
1. Wybierz z menu głównego **kompilacji | Tworzenie rozwiązania** (**F7** lub **Ctrl + Shift + B**). Upewnij się, że docelowy CMake jest zaznaczona w **element startowy** listy rozwijanej w **ogólne** paska narzędzi.

![Polecenia menu kompilacji CMake](media/cmake-build-menu.png "Cmake kompilacji polecenia menu") 

Po wybraniu generator Visual Studio dla aktywnej konfiguracji MSBuild.exe jest wywoływana z `-m -v:minimal` argumentów. Aby dostosować kompilacji, w pliku CMakeSettings.json można określić argumentów wiersza polecenia do przekazania do kompilacji systemu za pośrednictwem `buildCommandArgs` właściwości:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Jak można oczekiwać w przedstawiono wyniki kompilacji **okno danych wyjściowych** i **listy błędów**.
 
![Błędy kompilacji CMake](media/cmake-build-errors.png "CMake błędy kompilacji")

W folderze z wieloma docelowymi kompilacji, można wybrać **kompilacji** elementu na **CMake** menu lub **CMakeLists.txt** menu kontekstowym, aby określić, która docelowa CMake do kompilacji. Naciśnięcie przycisku **Ctrl + Shift + B** w CMake projektu kompilacje bieżący aktywny dokument.

## <a name="debug-the-project"></a>Debugowanie projektu

Aby debugować projektu CMake, wybrać żądaną konfiguracją i naciśnij klawisz **F5**, lub naciśnij klawisz **Uruchom** przycisku w pasku narzędzi. Jeśli **Uruchom** przycisk mówi "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz element docelowy, który chcesz uruchomić. (W projekcie CMake "bieżący dokument" opcja jest prawidłowa tylko dla plików .cpp.) 

![Przycisk Uruchom CMake](media/cmake-run-button.png "przycisk Uruchom Cmake")


**Uruchom** lub **F5** polecenia najpierw skompilować projekt, jeśli zostały zmienione od czasu poprzedniej kompilacji.

## <a name="configure-cmake-debugging-sessions"></a>Skonfiguruj CMake sesji debugowania

Wszystkie elementy docelowe wykonywalnego CMake są wyświetlane w **element startowy** listy rozwijanej w **ogólne** paska narzędzi. Aby rozpocząć sesję debugowania, wystarczy wybrać jedną i uruchomić debugera.

![CMake uruchamiania elementu z listy rozwijanej](media/cmake-startup-item-dropdown.png "CMake uruchamiania elementu z listy rozwijanej")


Można również uruchomić sesję debugowania, w menu CMake.

Aby dostosować ustawienia debugera dla dowolnego pliku wykonywalnego CMake docelowego w projekcie, kliknij prawym przyciskiem myszy w określonym pliku CMakeLists.txt, a następnie wybierz **debugowania i ustawienia uruchamiania**. Po wybraniu elementu docelowego CMake w podmenu jest tworzony plik o nazwie launch.vs.json. Ten plik jest wstępnie wypełnione informacjami o docelowym CMake, wybrana przez Ciebie i pozwala określić dodatkowe parametry, takie jak program argumentów lub typ debugera. Aby odwołać dowolny klawisz, w pliku CMakeSettings.json, należy poprzedzić go z "cmake." in launch.vs.json. W poniższym przykładzie przedstawiono plik prosty launch.vs.json ściągający wartości klucza "remoteCopySources" w pliku CMakeSettings.json dla aktualnie wybranej konfiguracji:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
   {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Bezpośrednio po zapisaniu pliku launch.vs.json wpis jest tworzony w **element startowy** listy rozwijanej z nową nazwą. Edytując plik launch.vs.json, można tworzyć, jak dla dowolnej liczby CMake celów, takich jak wiele konfiguracje debugowania.

**Visual Studio 2017 wersji 15.4**: Launch.vs.json obsługuje zmienne, które są zadeklarowane w CMakeSettings.json (patrz poniżej) i które są stosowane do obecnie wybranej konfiguracji. Ma klucz o nazwie "currentDir", który określa bieżącego katalogu uruchamiania aplikacji:


```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Po uruchomieniu aplikacji, wartość `currentDir` jest podobny do

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists.txt

Aby edytować plik CMakeLists.txt, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku pasek stanu żółty pojawia się i informuje o IntelliSense zostanie zaktualizowana i daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacje o CMakeLists.txt, zobacz [dokumentacji CMake](https://cmake.org/documentation/).

   ![Edytowanie pliku CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt edytowanie plików")


Bezpośrednio po zapisaniu pliku krok konfiguracji jest uruchamiana ponownie i automatycznie wyświetla informacje w **dane wyjściowe** okna. Błędy i ostrzeżenia są wyświetlane w **listy błędów** lub **dane wyjściowe** okna. Kliknij dwukrotnie w przypadku wystąpienia błędu w **listy błędów** można przejść do ataku wiersza w CMakeLists.txt.

   ![Błędy w pliku CMakeLists.txt](media/cmake-cmakelists-error.png "CMakeLists.txt błędy w pliku")

## <a name="cmake_settings"></a> CMake ustawienia i konfiguracje niestandardowe

Domyślnie program Visual Studio oferuje sześć domyślne konfiguracje CMake ("x86-Debug", "x86 wersja", "x64-Debug", "x64-wersja", "Linux-Debug" i "Linux wersja"). Te konfiguracje zdefiniuj, jak CMake.exe jest wywoływane w celu utworzenia pamięci podręcznej CMake dla danego projektu. Aby zmodyfikować te konfiguracje lub Utwórz nową konfigurację niestandardowe, wybierz **CMake | Zmień ustawienia CMake**, a następnie wybierz plik CMakeLists.txt, które ustawienia dotyczą. **Zmień ustawienia CMake** polecenia jest również dostępny w menu kontekstowym pliku w **Eksploratora rozwiązań**. To polecenie tworzy plik CMakeSettings.json w folderze projektu. Ten plik służy do ponownego utworzenia pliku pamięci podręcznej CMake, na przykład po **wyczyść** operacji. 

   ![Polecenia menu głównego CMake ustawienia zmian](media/cmake-change-settings.png)


JSON IntelliSense pomaga edytować plik CMakeSettings.json:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

W poniższym przykładzie przedstawiono Przykładowa konfiguracja, która służy jako punkt początkowy do tworzenia własnych w CMakeSettings.json:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

1. **Nazwa**: Nazwa wyświetlana na liście rozwijanej konfiguracji C++. Wartość tej właściwości mogą służyć jako makra, `${name}`, aby określić wartości innych właściwości. Na przykład zobacz **buildRoot** definicji w CMakeSettings.json.
1. **Generator**: mapuje **- G** przełącznika i określa generatora ma być używany. Ta właściwość umożliwia również jako makra, `${generator}`, aby określić wartości innych właściwości. Program Visual Studio obsługuje obecnie następujących generatory CMake:


    - "Nindżą"
    - "Visual Studio 14 2015"
    - "Programu visual Studio 14 2015 RAMIĘ"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "RAMIĘ programie visual Studio 15 2017"
    - "Visual Studio 15 2017 Win64"

Ponieważ Nindżą został zaprojektowany do szybkiego kompilacje prędkości zamiast elastyczność i funkcji, jest ustawiona domyślnie. Jednak niektóre projekty CMake może być nie można prawidłowo utworzyć przy użyciu Nindżą. W takim przypadku można nakazać CMake do generowania zamiast tego projektu programu Visual Studio.

Aby określić generator Visual Studio, otwórz CMakeSettings.json z poziomu menu głównego, wybierając **CMake | Zmień ustawienia CMake**. Usuń "Nindżą" i wpisz "V". Aktywuje IntelliSense, dzięki czemu można wybrać generator, który ma.

1. **buildRoot**: mapuje **-DCMAKE_BINARY_DIR** przełącznika i określa, gdzie zostanie utworzone w pamięci podręcznej CMake. Jeśli folder nie istnieje, jest tworzony.
1. **zmienne**: CMake zmiennych, które będą zostały przekazane jako pary nazwa wartość zawiera **-D**_nazwa_**=**_wartość_ do CMake. Instrukcje kompilacji projektu CMake określić dodanie wszelkie zmienne bezpośrednio do pliku pamięci podręcznej CMake, zaleca się dodanie je tutaj zamiast tego.
1. **cmakeCommandArgs**: określa żadnych dodatkowych przełączników, które mają zostać przekazane do CMake.exe.
1. **configurationType**: Określa typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane wartości to "Debug", "MinSizeRel", "Wersja" i "RelWithDebInfo".

### <a name="environment-variables"></a>Zmienne środowiskowe

CMakeSettings.json obsługuje również odbierającą zmienne środowiskowe w dowolnej właściwości wymienionych powyżej. Składnia jest `${env.FOO}` aby rozwinąć zmiennej środowiskowej % FOO %.
Masz również dostęp do wbudowanych makr wewnątrz tego pliku:

- `${workspaceRoot}` — zapewnia pełną ścieżkę folderu roboczego
- `${workspaceHash}` — Skrót lokalizacji obszaru roboczego. przydatne w przypadku tworzenia Unikatowy identyfikator dla bieżącego obszaru roboczego (na przykład do użycia w ścieżkach folderów)
- `${projectFile}` — Pełna ścieżka pliku CMakeLists.txt głównego
- `${projectDir}` — Pełna ścieżka do folderu głównego pliku CMakeLists.txt
- `${thisFile}` — Pełna ścieżka pliku CMakeSettings.json
- `${name}` — Nazwa konfiguracji
- `${generator}` — Nazwa generatora CMake używany w tej konfiguracji

### <a name="ninja-command-line-arguments"></a>Argumenty wiersza polecenia nindżą

Jeśli obiekty docelowe nieokreślony, tworzy element docelowy "default" (zobacz Podręcznik).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opcja|Opis|
|--------------|------------|
| --wersji  | Drukowanie nindżą wersja ("1.7.1")|
|   -C DIR   | Zmień katalog przed wykonaniem jakichkolwiek innych czynności|
|   -f pliku  | Określ plik wejściowy kompilacji (default=build.ninja)|
|   -j N     | równoległe wykonywanie zadań N (domyślne = 14 pochodzące z procesorów dostępnych)|
|   -k N     | Zachowaj przechodzi do momentu N zadanie zakończy się niepowodzeniem (domyślne = 1)|
|   -l N     | Nie uruchamiaj nowe zadania, jeśli średnia obciążenia jest większa niż N|
|   -n      | Uruchom wysuszyć (nie działają polecenia, ale działa jak one zakończyło się powodzeniem)|
|   -v       | Pokaż wszystkie wiersze poleceń podczas kompilowania|
|   -d tryb  | Włącz debugowanie (tryby listy do użycia -d)|
|   t — narzędzie  | Uruchom subtool (Użyj -t listy do narzędzi niższego poziomu). kończy opcje toplevel; dodatkowe flagi są przekazywane do narzędzia| 
|   -w flagi  | Dostosuj ostrzeżenia (Użyj -w listy do ostrzeżenia)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Dziedziczony środowisk (Visual Studio 2017 wersji 15,5 cala)
CMakeSettings.json obsługuje teraz dziedziczone środowiska. Ta funkcja umożliwia (1) dziedziczyć domyślnego środowiska i (2) Utwórz zmienne środowiskowe niestandardowych, które są przekazywane do CMake.exe, gdy jest uruchamiany.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

W powyższym przykładzie jest taka sama jak działa **wiersz polecenia dla programu VS 2017 deweloperów** z **-arch = amd64-host_arch = amd64** argumentów.

W poniższej tabeli przedstawiono domyślne wartości i ich odpowiedniki wiersza polecenia:

|Nazwa kontekstu|Opis|
|-----------|-----------------|
|vsdev|Domyślne środowisko Visual Studio|
|msvc_x86|Kompiluj x86 przy użyciu x86 narzędzia|
|msvc_arm| Kompiluj ARM przy użyciu x86 narzędzia|
|msvc_arm64|Kompilacji dla ARM64 przy użyciu x86 narzędzia|
|msvc_x86_x64|Kompiluj dla AMD64, przy użyciu x86 narzędzia|
|msvc_x64_x64|Kompiluj dla AMD64, za pomocą narzędzia 64-bitowy|
|msvc_arm_x64|Kompiluj ARM przy użyciu narzędzia 64-bitowy|
|msvc_arm64_x64|Kompilacji dla ARM64 przy użyciu narzędzia 64-bitowy|

### <a name="custom-environment-variables"></a>Zmienne środowiskowe niestandardowych
W CMakeSettings.json, można zdefiniować zmienne niestandardowe środowiska globalnie lub na konfigurację w **środowisk** właściwości. W poniższym przykładzie zdefiniowano jednej zmiennej globalnej, **BuildDir**, dziedziczoną w konfiguracjach x86 debugowania i x64 debugowania. Każdej konfiguracji użyto zmiennej do określenia wartości **buildRoot** właściwości dla tej konfiguracji. Należy też zauważyć, jak każdej konfiguracji używa **inheritEnvironments** właściwości w celu określenia zmiennej, która ma zastosowanie tylko do tej konfiguracji.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

W następnym przykładzie z konfiguracji debugowania x86 definiuje wartość dla **BuildDir** właściwości i ta wartość zastępuje wartość ustawioną przez globalnej **BuildDir** właściwości, aby  **BuildRoot** daje w wyniku `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir",
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ], 
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="cmake-configure-step"></a>CMake skonfigurować kroku

W przypadku istotnych zmian do CMakeSettings.json lub CMakeLists.txt pliki, Visual Studio automatycznie ponownie uruchamia CMake skonfigurować kroku. Jeśli krok Konfiguruj zakończy działanie bez błędów, zbieranych informacji jest dostępnych w usługach języka i IntelliSense dla C++ i również w kompilacji i debugowania operacji.

Korzystając z wielu projektów CMake taką samą nazwę konfiguracji CMake (na przykład x86-Debug), wszystkie z nich są konfigurowane i wbudowane (folder główny własnych kompilacji) po wybraniu tej konfiguracji. Można debugować elementy docelowe ze wszystkich projektów CMake uczestniczących w tej konfiguracji CMake.

   ![Tworzenie CMake tylko element menu](media/cmake-build-only.png "kompilacji CMake tylko element menu")

Aby ograniczyć kompilacji i debugowania sesji do podzbioru projekty w obszarze roboczym, Utwórz nową konfigurację o unikatowej nazwie w pliku CMakeSettings.json i dotyczą tylko tych projektów. Po wybraniu tej konfiguracji polecenia IntelliSense i kompilacji i debugowania są włączone tylko dla określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej CMake

Aby uzyskać więcej informacji o stanie CMake pamięci podręcznej, aby zdiagnozować problem, otwórz **CMake** menu głównego lub **CMakeLists.txt** menu kontekstowego w **Eksploratora rozwiązań**na jeden z tych poleceń:

- **Wyświetlanie pamięci podręcznej** otwiera plik CMakeCache.txt z folderu głównego kompilacji w edytorze. (Wszystkie zmiany wprowadzone w tym miejscu CMakeCache.txt są czyszczone Jeśli czyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są zachowywane po czyszczeniu pamięci podręcznej, zobacz [CMake ustawienia i konfiguracje niestandardowe](#cmake_settings) we wcześniejszej części tego artykułu.)
- **Otwórz Folder pamięci podręcznej** zostanie otwarte okno Eksploratora do folderu głównego kompilacji.  
- **Czyszczenie pamięci podręcznej** usuwa folder główny kompilacji, aby dalej CMake skonfigurowanie uruchamia krok z czystą pamięci podręcznej.
- **Generowanie pamięci podręcznej** wymusza krok Generuj do uruchomienia, nawet jeśli program Visual Studio uwzględnia aktualnego środowiska.
