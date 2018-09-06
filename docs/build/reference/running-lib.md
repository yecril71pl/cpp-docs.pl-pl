---
title: Uruchamianie LIB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff75c149ff3cfff5a360314386cc4828d00f4e8d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894606"
---
# <a name="running-lib"></a>Uruchamianie LIB

Różne opcje wiersza polecenia może służyć do sterowania LIB.

## <a name="lib-command-line"></a>Wiersz polecenia LIB

Uruchamianie LIB, wpisz polecenie `lib` następuje opcji i nazw plików dla zadania używasz biblioteki do wykonania. LIB akceptuje także wprowadzanie wiersza poleceń w plikach poleceń, które są opisane w poniższej sekcji. Lib — nie używać zmiennej środowiskowej.

> [!NOTE]
> Jeśli użytkownik jest przyzwyczajony do LINK32.exe i LIB32.exe narzędzi, pod warunkiem przy użyciu Microsoft Win32 oprogramowania Development Kit dla Windows NT, może używano albo polecenie `link32 -lib` lub polecenia `lib32` do zarządzania bibliotekami i tworzenie Importuj biblioteki. Pamiętaj zmienić swoje pliki reguł programu make i batch plików `lib` zamiast tego polecenia.

## <a name="lib-command-files"></a>Pliki poleceń LIB

Argumenty wiersza polecenia można przekazać do biblioteki w pliku poleceń, używając następującej składni:

> **LIB \@**  <em>commandfile</em>

Plik *commandfile* jest plikiem tekstowym. Nie spacji lub tabulatorów jest dozwolone między znakiem (**\@**) i nazwę pliku. Nie ma rozszerzenia domyślną; należy określić pełną nazwę pliku, łącznie z dowolnym rozszerzeniem. Nie można używać symboli wieloznacznych. Można określić ścieżkę bezwzględną lub względną z nazwą pliku.

W pliku poleceń argumenty mogą być oddzielone tabulacji lub spacji, jak w wierszu polecenia; mogą one być również rozdzielone znakami nowego wiersza. Użyj średnika (;), aby oznaczyć komentarz. LIB ignoruje cały tekst z średnik z powrotem do końca wiersza.

Można określić wszystkie lub część wiersza polecenia, które znajdują się w pliku poleceń, a następnie można użyć więcej niż jeden plik polecenia za pomocą polecenia LIB. LIB akceptuje dane wejściowe plik poleceń tak, jakby zostały określone w tej lokalizacji, w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżone. LIB funkcją zawartość plików poleceń, chyba że używana jest opcja/nologo.

## <a name="using-lib-options"></a>Za pomocą opcji LIB

Opcja składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), następuje nazwa opcji. Nie należy skracać nazwy opcji. Niektóre opcje przyjmować argument, określone po dwukropek (:). Nie spacje lub tabulatory są dozwolone w obrębie Specyfikacja opcji. Użyj miejsc do magazynowania lub karty do oddzielenia specyfikacje opcji w wierszu polecenia. Opcja nazwy i ich argumenty nazwy pliku lub słowo kluczowe nie są z uwzględnieniem wielkości liter, ale identyfikatory używane jako argumenty jest uwzględniana wielkość liter. LIB przetwarza opcje w kolejności określonej w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzany z różnymi argumentami, pierwszeństwo ma ostatni z nich do przetworzenia.

Poniższe opcje są stosowane do wszystkich rodzajów LIB:

> **/ ERRORREPORT** [**NONE** &AMP;#124; **MONITU** &AMP;#124; **KOLEJKI** &AMP;#124; **WYSYŁANIA**]

W przypadku niepowodzenia lib.exe w środowisku uruchomieniowym, można użyć/errorreport do wysyłania informacji do firmy Microsoft dotyczących tych błędów wewnętrznych.

Aby uzyskać więcej informacji na temat/errorreport zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).

> **/LTCG**

Powoduje, że biblioteka ma zostać utworzony przy użyciu Generowanie łączonych kodów czasowych.  Aby uzyskać więcej informacji, zobacz [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md).

> **/ MACHINE**

Określa platformę docelową dla programu. Zazwyczaj nie trzeba określić/Machine. LIB wnioskuje typ maszyny z plików .obj. W niektórych sytuacjach LIB nie można określić typu maszyny i wysyła komunikat o błędzie. Jeśli wystąpi taki błąd, należy określić/Machine. W trybie/extract ta opcja dotyczy tylko weryfikacji. Użyj `lib /?` w wierszu polecenia, aby wyświetlić typy dostępnych maszyn.

> **/NOLOGO**

Pomija wyświetlanie LIB praw autorskich komunikat i numer wersji i zapobiega wyświetlania pliku polecenia.

> **/VERBOSE**

Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików .obj, dodawane. Informacje są wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

> **/WX**[**: NO**]

Traktuj ostrzeżenia jako błędy. Zobacz [/WX (Traktuj ostrzeżenia konsolidatora jak błędy)](../../build/reference/wx-treat-linker-warnings-as-errors.md) Aby uzyskać więcej informacji.

Inne opcje są stosowane tylko do określonych rodzajów LIB. Te opcje są omówione w sekcji opisem każdego trybu.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](../../build/reference/lib-reference.md)