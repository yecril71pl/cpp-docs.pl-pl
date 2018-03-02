---
title: /MP (kompilacja z wieloma procesami) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
dev_langs:
- C++
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5aa190d2cb2d1e0b0d13979d5e0044291d7cd8a7
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="mp-build-with-multiple-processes"></a>/MP (Kompilacja z wieloma procesami)

**/MP** opcji zmniejsza całkowity czas do kompilowania plików źródłowych w wierszu polecenia. **/MP** opcja powoduje, że kompilator, aby utworzyć jeden lub więcej kopie sama każdej z nich w oddzielnych procesach. Następnie te kopie jednocześnie Kompiluj pliki źródłowe. W związku z tym łączny czas wymagany do kompilacji pliki źródłowe, można znacznie zmniejszyć.

## <a name="syntax"></a>Składnia

> **/MP**[*processMax*]

## <a name="arguments"></a>Argumenty

*processMax*<br/>
(Opcjonalnie) Maksymalna liczba procesów, które można utworzyć przez kompilator.

*ProcessMax* argumentu musi należeć do zakresu od 1 do 65536. W przeciwnym razie kompilator generuje komunikat ostrzegawczy **D9014**, ignoruje *processMax* argumentu, przyjęto założenie, maksymalna liczba procesów jest 1.

W przypadku pominięcia *processMax* argumentu, kompilator pobiera numer [procesorów skuteczne](#effective_processors) na komputerze z systemu operacyjnego i utworzenie procesu dla każdego procesora.

## <a name="remarks"></a>Uwagi

**/MP** — opcja kompilatora mogą znacznie ograniczyć czas kompilacji podczas kompilowania wielu plików. Aby skrócić czas kompilacji, kompilator tworzy do *processMax* kopii, a następnie używa tych kopii do kompilowania plików źródłowych w tym samym czasie. **/MP** opcja ma zastosowanie do kompilacji, ale nie do łączenia lub w czasie konsolidacji generowania kodu. Domyślnie **/MP** opcja jest wyłączona.

Ulepszenia w czasie kompilacji zależy od tego, liczba procesorów na komputerze, to liczba plików do kompilowania i dostępności zasobów systemowych, takich jak wydajność We/Wy. Eksperymentować **/MP** opcję, aby określić ustawienie Najlepsze do kompilacji określonego projektu. Aby uzyskać wskazówki ułatwiające podjęcie decyzji, zobacz [wytyczne](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Niezgodne opcje i funkcje językowe

**/MP** opcja jest niezgodna z niektórych opcji kompilatora i funkcje językowe. Korzystając z opcji kompilatora niezgodne z **/MP** opcja, kompilator generuje ostrzeżenie **D9030** ignoruje **/MP** opcji. Jeśli używasz funkcji języka niezgodne kompilator generuje błąd [C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) , a następnie kończy się lub będzie kontynuowane w zależności od bieżącej kompilator ostrzeżenie opcję poziomu.

> [!NOTE]
> Większość opcji są niezgodne, ponieważ jeśli zostały one dopuszczone, współbieżnie wykonywanego kompilatory zapisać ich dane wyjściowe w tym samym czasie w konsoli lub do określonego pliku. W związku z tym dane wyjściowe będą intermix i jest zniekształcony. W niektórych przypadkach kombinację opcji spowodowałoby co gorsza wydajności.

W poniższej tabeli wymieniono opcje kompilatora i funkcje językowe, które są niezgodne z **/MP** opcji:

|Opcja lub funkcji języka|Opis|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy preprocesora|Konwertuje typy w bibliotece typów w klasach C++, a następnie zapisuje te klasy w pliku nagłówka.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego (**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Umożliwia przyrostowe ponownej kompilacji.|
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|Zapisuje listy plików dołączanych do standardowego błędu (**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Zapisuje prekompilowanego pliku nagłówkowego.|

## <a name="diagnostic-messages"></a>Komunikaty diagnostyczne

Jeśli określisz funkcji opcji lub języka, który jest niezgodny z **/MP** opcji, zostanie wyświetlony komunikat diagnostycznych. W poniższej tabeli wymieniono komunikaty i zachowania kompilatora:

|Komunikat diagnostycznych|Opis|Zachowanie kompilatora|
|------------------------|-----------------|-----------------------|
|**C2813**|**#Import** dyrektywy nie jest zgodny z **/MP** opcji.|Kompilacja kończy się, chyba że [poziom ostrzeżeń kompilatora](../../build/reference/compiler-option-warning-level.md) opcja określa, w przeciwnym razie wartość.|
|**D9014**|Określono nieprawidłową wartość dla *processMax* argumentu.|Kompilator ignoruje nieprawidłową wartość i przyjmuje wartość 1.|
|**D9030**|Określona opcja jest niezgodna z **/MP**.|Kompilator ignoruje **/MP** opcji.|

## <a name="guidelines"></a> Wskazówki

### <a name="measure-performance"></a>Miara wydajności

Użyj kompilacji łączny czas pomiaru wydajności. Czas kompilacji można zmierzyć fizycznych zegara, lub skorzystać z oprogramowania, który oblicza różnicę między podczas kompilacji uruchamiania i zatrzymywania. Jeśli komputer ma wiele procesorów, fizycznych zegara może dać dokładniejsze wyniki niż pomiar czasu oprogramowania.

### <a name="effective_processors"></a> Skuteczne procesorów

Na komputerze może być jeden lub więcej procesorów wirtualnych, które są również znane jako *procesorów skuteczne*, dla każdego z jego procesorów fizycznych. Poszczególnych zasobów fizycznych — procesora może mieć co najmniej jeden rdzeni, a jeśli system operacyjny umożliwia wielowątkowość podstawowych, każdy core wydaje się być dwa procesory wirtualne.

Na przykład komputer ma jeden procesor skuteczne, jeśli ma ona jednego procesora fizycznego, który ma jeden rdzeń i wielowątkowość jest wyłączona. Z kolei komputera ma osiem procesorów skuteczne, jeśli składa się z dwóch procesorów fizycznych, z których każdy ma dwa rdzenie, a wszystkie rdzenie ma treading. Oznacza to, że (8 procesorów skuteczne) = (2 procesorów fizycznych) x (2 rdzenie dla każdego procesora fizycznego) x (2 procesory skuteczne na podstawowe z powodu wielowątkowość).

W przypadku pominięcia *processMax* argument **/MP** opcja, kompilator uzyskuje liczbę procesorów skuteczne z systemu operacyjnego, a następnie tworzy jeden proces dla każdego procesora, skuteczne. Jednak kompilator nie może zagwarantować procesu, który wykonuje na określonym procesorze; system operacyjny sprawia, że tej decyzji.

### <a name="number-of-processes"></a>Liczba procesów

Kompilator oblicza liczbę procesów, który będzie używany do kompilowania plików źródłowych. Czy wartość jest mniejsza liczba plików źródłowych, które określają w wierszu polecenia i liczby procesów, które jawnie lub niejawnie określono z **/MP** opcji. Maksymalna liczba procesów można ustawić jawnie, jeśli podasz *processMax* argument **/MP** opcji. Możesz użyć domyślnej, która jest równa liczbie skuteczne procesorów w komputerze, jeśli pominięto *processMax* argumentu.

Załóżmy na przykład wprowadzić następujący wiersz polecenia:

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

W takim przypadku kompilator wykorzystuje pięć procesów, ponieważ jest mniejszy z pięć plików źródłowych i nie więcej niż siedmiu procesów. Alternatywnie Załóżmy, że ten komputer ma dwa procesory skuteczne i wprowadzić następujący wiersz polecenia:

`cl /MP a.cpp b.cpp c.cpp`

W takim przypadku system operacyjny raporty dwa procesory; w związku z tym kompilator używa dwóch procesów w obliczeniu. W związku z tym kompilator będzie wykonywał kompilacji z dwoma procesami, ponieważ jest to mniejszy z dwóch procesów i trzy pliki źródłowe.

### <a name="source-files-and-build-order"></a>Pliki źródłowe i kolejność kompilacji

Pliki źródłowe nie może zostać skompilowany w takiej samej kolejności, w jakiej występują w wierszu polecenia. Mimo że kompilator tworzy zestaw procesów, które zawierają kopie kompilatora, system operacyjny planuje podczas każdego procesu. W rezultacie nie może zagwarantować, że pliki źródłowe zostanie skompilowany w określonej kolejności.

Plik źródłowy jest kompilowana, gdy proces jest dostępne go skompilować. W przypadku większej liczby plików niż procesy pierwszego zestawu plików jest kompilowana przez procesy dostępne. Pozostałe pliki są przetwarzane, gdy proces zakończy obsługi poprzedniego pliku i jest dostępny do pracy na jednym z pozostałych plików.

Nie określaj tego samego pliku źródłowego wiele razy w wierszu polecenia. Taka sytuacja może wystąpić, na przykład, jeśli narzędzie automatycznie tworzy [pliku reguł programu make](../../build/contents-of-a-makefile.md) opartego na informacje o zależności w projekcie. Jeśli nie określisz **/MP** opcja, kompilator sekwencyjnie przetwarza listę plików i rekompiluje każde wystąpienie pliku. Jednak jeśli określisz **/MP** opcji różnych kompilatory może skompilować tego samego pliku w tym samym czasie. W rezultacie różnych kompilatory podejmie próbę zapisu do tego samego pliku danych wyjściowych w tym samym czasie. Jeden kompilatora będzie uzyskać wyłącznego dostępu zapisu do pliku wyjściowego i powiedzie się i inne kompilatory zakończy się niepowodzeniem z powodu błędu dostępu do pliku.

### <a name="using-type-libraries-import"></a>Korzystanie z bibliotek typów (#import)

Kompilator nie obsługuje korzystania z [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy z **/MP** przełącznika. Jeśli to możliwe wykonaj następujące kroki w celu obejścia tego problemu:

- Przenieś wszystkie `#import` dyrektywy w sieci z różnych plików do jednego lub więcej plików źródłowych, a następnie skompilować pliki bez **/MP** opcji. Wynik to zestaw plików wygenerowany nagłówek.

- W pozostałe pliki źródłowe, Wstaw [#include](../../preprocessor/hash-include-directive-c-cpp.md) dyrektywy, które Określ wygenerowanego nagłówków, a następnie skompilować pozostałe pliki źródłowe przy użyciu **/MP** opcji.

### <a name="visual-studio-project-settings"></a>Ustawienia projektu programu Visual Studio

#### <a name="the-msbuildexe-tool"></a>Narzędzia MSBUILD.exe

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] używa [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) narzędziem do tworzenia rozwiązań i projektów. **/Maxcpucount:**_numer_ (lub **/m:**_numer_) opcji wiersza polecenia narzędzia MSBuild.exe można tworzyć wiele projektów w tym samym czasie. I **/MP** — opcja kompilatora można tworzyć wielu jednostkach kompilacji, w tym samym czasie. Jeśli jest to odpowiednie dla aplikacji, skrócić czas kompilacji rozwiązania przy użyciu jednego lub obu **/MP** i **/maxcpucount**.

Czas kompilacji rozwiązania częściowo zależy od liczby procesów, które wykonują kompilacji. *Numer* argument [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) opcja MSBuild określa maksymalną liczbę projektów do kompilacji w tym samym czasie. Podobnie *processMax* argument **/MP** — opcja kompilatora określa maksymalną liczbę jednostek kompilacji do kompilacji w tym samym czasie. Jeśli **/maxcpucount** opcja określa *P* projektów i **/MP** opcja określa *C* przetwarza maksymalnie *P*  x *C* wykonania procesów w tym samym czasie.

 Wytyczna podjęcie decyzji o użyciu MSBuild lub **/MP** technologii wygląda następująco:

- Jeśli istnieje wiele projektów z kilku plików w każdym projekcie, należy użyć narzędzia MSBuild.

- Jeśli istnieje kilka projektów z wielu plików w każdym projekcie, użyj **/MP** opcji.

- Jeśli liczba projektów i pliki w projekcie jest rozmieszczana, użyj obu MSBuild i **/MP**. Ustawiany **/maxcpucount** możliwość liczbę projektów do kompilacji i **/MP** opcję, aby liczba procesorów na tym komputerze. Mierzenie wydajności, a następnie Dostosuj ustawienia w celu uzyskania najlepszych wyników. Powtórz cyklu aż do uzyskania z czasem całkowita kompilacji.

#### <a name="the-gm-compiler-option"></a>/Gm — opcja kompilatora

Domyślnie projektu kompilacji umożliwia **/GM ponowną** — opcja kompilatora (kompilacji przyrostowej) dla kompilacji do debugowania i wyłącza dla wersji kompilacji. W związku z tym **/MP** — opcja kompilatora jest automatycznie wyłączana w kompilacjach debugowania, ponieważ powoduje on konflikt z domyślnym **/GM ponowną** — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Dokumentacja wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/ZF (Generowanie szybciej PDB)](zf.md)<br/>
