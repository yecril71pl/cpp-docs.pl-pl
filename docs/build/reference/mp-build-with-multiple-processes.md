---
title: /MP (kompilacja z wieloma procesami) | Dokumentacja firmy Microsoft
ms.custom: ''
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
ms.workload:
- cplusplus
ms.openlocfilehash: bb24ed970d3b02835d5545cb0eaf1d9fd8e81c7e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713430"
---
# <a name="mp-build-with-multiple-processes"></a>/MP (Kompilacja z wieloma procesami)

**/MP** opcji może zmniejszyć całkowity czas do kompilowania plików źródłowych w wierszu polecenia. **/MP** opcja powoduje, że kompilator, aby utworzyć co najmniej jeden kopie sama każdego w oddzielnym procesie. Następnie te kopie jednocześnie kompilacji plików źródłowych. W związku z tym łączny czas wymagany do tworzenia plików źródłowych można znacznie zmniejszyć.

## <a name="syntax"></a>Składnia

> **/MP**[*processMax*]

## <a name="arguments"></a>Argumenty

*processMax*<br/>
(Opcjonalnie) Maksymalna liczba procesów, które kompilator może utworzyć.

*ProcessMax* argumentu musi należeć do zakresu od 1 do 65536. W przeciwnym razie kompilator generuje komunikat ostrzegawczy **D9014**, ignoruje *processMax* argument, a przyjęto założenie, maksymalna liczba procesów jest 1.

Jeżeli pominięto *processMax* argument, kompilator pobiera numer [skuteczne procesorów](#effective_processors) na komputerze z systemu operacyjnego i tworzy proces dla każdego procesora.

## <a name="remarks"></a>Uwagi

**/MP** — opcja kompilatora może znacznie skrócić czas kompilacji podczas kompilacji z wielu plików. Aby poprawić czas kompilacji, kompilator tworzy maksymalnie *processMax* kopii, a następnie używa tych kopii widoczne do kompilowania plików źródłowych w tym samym czasie. **/MP** opcja ma zastosowanie do kompilacji, ale nie do łączenia lub linku w czasie generowania kodu. Domyślnie **/MP** opcja jest wyłączona.

Ulepszanie w czasie kompilacji zależy od liczby procesorów w komputerze, liczba plików do kompilacji i dostępność zasobów systemowych, takich jak wydajność We/Wy. Poeksperymentuj z **/MP** opcję, aby określić najlepsze ustawienie do utworzenia danego projektu. Aby uzyskać porady ułatwiające podjęcie decyzji, zobacz [wytycznych](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Opcje niezgodne i funkcje językowe

**/MP** opcja jest niezgodna z niektóre opcje kompilatora i funkcje języka. Jeśli używasz opcji kompilatora niezgodne z **/MP** opcja, kompilator generuje ostrzeżenie **D9030** i ignoruje **/MP** opcji. Jeśli używasz funkcji języka niezgodne, kompilator generuje błąd [C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) , a następnie kończy się lub jest kontynuowane w zależności od bieżącej ostrzeżenia poziomu opcję kompilatora.

> [!NOTE]
> Większość opcji są niezgodne, ponieważ jeśli one były dozwolone, kompilatory współbieżnie wykonywanego napisać swoje dane wyjściowe w tym samym czasie konsoli lub do określonego pliku. W rezultacie dane wyjściowe będzie intermix i być uszkodzony. W niektórych przypadkach kombinację opcji czyniłyby gorsza wydajności.

W poniższej tabeli wymieniono opcje kompilatora i funkcje językowe, które są niezgodne z **/MP** opcji:

|Opcja lub funkcja językowa|Opis|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy preprocesora|Konwertuje typy w bibliotece typów na klasy C++, a następnie zapisuje te klasy w pliku nagłówka.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego (**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Umożliwia przyrostowe ponownej kompilacji.|
|[/ showincludes](../../build/reference/showincludes-list-include-files.md)|Zapisuje listę wszystkich plików dołączanych do błędu standardowego (**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Zapisuje prekompilowanego pliku nagłówkowego.|

## <a name="diagnostic-messages"></a>Komunikaty diagnostyczne

W przypadku określenia opcji lub język funkcji, która jest niezgodna z **/MP** opcję, otrzymają komunikat diagnostyczny. W poniższej tabeli wymieniono komunikaty i zachowanie kompilatora:

|Komunikat diagnostyczny|Opis|Zachowanie kompilatora|
|------------------------|-----------------|-----------------------|
|**C2813**|**#Import** dyrektywy nie jest zgodny z **/MP** opcji.|Kompilacja kończy się, chyba że [poziom ostrzeżeń kompilatora](../../build/reference/compiler-option-warning-level.md) opcja określa, w przeciwnym razie.|
|**D9014**|Określono nieprawidłową wartość dla *processMax* argumentu.|Kompilator ignoruje nieprawidłową wartość i przyjmuje wartość 1.|
|**D9030**|Określona opcja jest niezgodna z **/MP**.|Kompilator ignoruje **/MP** opcji.|

## <a name="guidelines"></a> Wytyczne dotyczące

### <a name="measure-performance"></a>Miara wydajności

Użyj kompilacji łączny czas do pomiaru wydajności. Można zmierzyć czas kompilacji, z fizycznego zegar, lub można korzystać z oprogramowania, który oblicza różnicę między podczas uruchamiania i zatrzymywania w kompilacji. Jeśli komputer ma wiele procesorów, fizycznego zegar może przynieść bardziej precyzyjne wyniki niż pomiaru czasu oprogramowania.

### <a name="effective_processors"></a> Skuteczne procesorów

Komputer może mieć jeden lub więcej procesorów wirtualnych, które są również nazywane *skuteczne procesorów*, dla każdego z jego procesorów fizycznych. Każdy fizyczny procesor może mieć jeden lub więcej rdzeni, a jeśli system operacyjny umożliwia wielowątkowość za rdzeń, każdego rdzenia wydaje się być dwa procesory wirtualne.

Na przykład komputer ma jeden procesor skuteczne, jeśli ma on jeden procesora fizycznego, który ma jednego rdzenia, a wielowątkowość jest wyłączona. Z kolei komputera ma ośmiu procesorów skuteczne, jeśli ma dwa procesory fizyczne, z których każdy ma dwa rdzenie, a wszystkie rdzenie mają włączoną wielowątkowość. Oznacza to, że (8 procesorów skuteczne) = (2 procesory fizyczne) x (2 rdzenie na procesora fizycznego) x (2 procesory skuteczne na rdzeń procesora ze względu na wielowątkowość).

Jeżeli pominięto *processMax* argument **/MP** opcji kompilatora uzyskuje liczbę procesorów obowiązujące od systemu operacyjnego, a następnie tworzy jeden proces na procesor skuteczne. Jednak kompilator nie może zagwarantować, który proces jest wykonywany na określonym procesorze; system operacyjny sprawia, że tej decyzji.

### <a name="number-of-processes"></a>Liczba procesów

Kompilator oblicza liczbę procesów, który będzie używany do kompilowania plików źródłowych. Czy wartość jest mniejsza liczba plików źródłowych, które należy określić w wierszu polecenia i liczbę procesów, należy jawnie lub niejawnie określić za pomocą **/MP** opcji. Można jawnie ustawić maksymalną liczbę procesów, jeśli podasz *processMax* argument **/MP** opcji. Możesz też domyślna, która jest równa liczbie skuteczne procesorów w komputerze, jeśli pominięto *processMax* argumentu.

Załóżmy na przykład wprowadzić następujący wiersz polecenia:

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

W tym przypadku kompilator używa pięć procesów, ponieważ jest mniejsza od pięciu pliki źródłowe i maksymalnie siedem procesów. Alternatywnie Załóżmy, że komputer ma dwa procesory skuteczne i wprowadzić następujący wiersz polecenia:

`cl /MP a.cpp b.cpp c.cpp`

W takim przypadku system operacyjny raporty dwa procesory; w związku z tym kompilator używa dwóch procesów podczas jej obliczania. Co w efekcie kompilator wykona kompilacji przy użyciu dwóch procesów, ponieważ jest mniejszy z dwóch procesów i trzy pliki źródłowe.

### <a name="source-files-and-build-order"></a>Pliki źródłowe i kolejność kompilacji

Pliki źródłowe może nie zostać skompilowany w tej samej kolejności, w jakiej są wyświetlane w wierszu polecenia. Mimo że kompilator tworzy zbiór procesów, które zawierają kopie kompilatora, system operacyjny planuje podczas wykonywania poszczególnych procesów. W związku z tym nie może zagwarantować, że pliki źródłowe zostanie skompilowany w określonej kolejności.

Plik źródłowy jest kompilowana, gdy proces jest dostępny do kompilowania go. W przypadku więcej plików niż procesy pierwszego zestawu plików jest kompilowany przy dostępne procesy. Pozostałe pliki są przetwarzane, gdy proces zakończy się obsługa poprzedni plik jest dostępny do pracy na jednym z pozostałych plików.

Nie określaj tym samym pliku źródłowym wiele razy w wierszu polecenia. Taka sytuacja może wystąpić, na przykład, jeśli narzędzie automatycznie tworzy [pliku reguł programu make](../../build/contents-of-a-makefile.md) opartego na informacje o zależnościach w projekcie. Jeśli nie określisz **/MP** opcja, kompilator przetwarza sekwencyjnie listę plików i następuje rekompilacja każde wystąpienie pliku. Jednak w przypadku określenia **/MP** opcji różne kompilatory może skompilować ten sam plik w tym samym czasie. W konsekwencji różne kompilatory podejmie próbę zapisu do tego samego pliku wyjściowego, w tym samym czasie. Jeden kompilatora będzie uzyskać wyłącznego dostępu zapisu do pliku wyjściowego i powiedzie się i innych kompilatorów zakończy się niepowodzeniem z powodu błędu dostępu do pliku.

### <a name="using-type-libraries-import"></a>Korzystanie z bibliotek typów (#import)

Kompilator nie obsługuje użycia [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy z **/MP** przełącznika. Jeśli to możliwe wykonaj następujące kroki, aby obejść ten problem:

- Przenieś wszystkie `#import` dyrektywy w swojej różnych plików do jednego lub więcej plików źródłowych, a następnie skompilować te pliki bez **/MP** opcji. Wynik jest zestaw plików wygenerowany nagłówek.

- W pozostałe pliki źródłowe, wstawić [#include](../../preprocessor/hash-include-directive-c-cpp.md) dyrektyw, które Określ wygenerowanego nagłówki, a następnie skompilować pozostałe pliki źródłowe przy użyciu **/MP** opcji.

### <a name="visual-studio-project-settings"></a>Ustawienia projektu programu Visual Studio

#### <a name="the-msbuildexe-tool"></a>Narzędzie MSBUILD.exe

Program Visual Studio używa [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) narzędziem do tworzenia rozwiązań i projektów. **/Maxcpucount:**_numer_ (lub **/m:**_numer_) opcji wiersza polecenia narzędzia MSBuild.exe, można tworzyć wiele projektów w tym samym czasie. I **/MP** — opcja kompilatora mogą tworzyć wiele jednostek kompilacji w tym samym czasie. Jeśli jest ona odpowiednia dla aplikacji, zwiększyć czas kompilacji swoje rozwiązanie przy użyciu jednego lub obu **/MP** i **/maxcpucount**.

Czas kompilacji rozwiązania częściowo zależy od liczby procesów, które wykonują kompilacji. *Numer* argument [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild opcja określa maksymalną liczbę projektów do kompilacji w tym samym czasie. Podobnie *processMax* argument **/MP** — opcja kompilatora określa maksymalną liczbę jednostek kompilacji do kompilacji w tym samym czasie. Jeśli **/maxcpucount** opcja określa *P* projektów i **/MP** opcja określa *C* przetwarza maksymalnie *P*  x *C* procesy zrealizowane w tym samym czasie.

Wytycznych dotyczących decydowania, czy należy użyć programu MSBuild lub **/MP** technologia jest w następujący sposób:

- W przypadku wielu projektów za pomocą kilku plików w każdym projekcie, należy użyć narzędzia MSBuild.

- W przypadku kilku projektów zawierających wiele plików w każdym projekcie użyj **/MP** opcji.

- Jeśli liczba projektów i plików na projekt jest równoważone, należy użyć zarówno programu MSBuild i **/MP**. Początkowo ustawić **/maxcpucount** możliwość liczby projektów do kompilacji i **/MP** opcję, aby liczba procesorów na tym komputerze. Mierzenie wydajności, a następnie Dostosuj ustawienia umożliwiające uzyskanie najlepsze rezultaty. Powtórz ten cykl, dopóki jesteś zadowolony z czasem kompilacji łączna liczba.

#### <a name="the-gm-compiler-option"></a>/Gm — opcja kompilatora

Domyślnie, projekt kompilacji umożliwia **/Gm** — opcja kompilatora (kompilacje przyrostowe) dla kompilacji do debugowania i wyłącza opiera się on do wydania. W związku z tym **/MP** — opcja kompilatora jest automatycznie wyłączone w kompilacjach debugowania, ponieważ powoduje on konflikt z domyślnym **/Gm** — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Dokumentacja wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf (Szybsze generowanie pliku PDB)](zf.md)<br/>
