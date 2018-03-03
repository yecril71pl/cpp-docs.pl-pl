---
title: Uruchamianie LIB | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a487bb6f6ffd740f6479916c5115bf95d568655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="running-lib"></a>Uruchamianie LIB
Różne opcje wiersza polecenia mogą służyć do sterowania LIB.  
  
## <a name="lib-command-line"></a>Wiersz polecenia LIB  
 Aby uruchomić LIB, wpisz polecenie `lib` następuje opcje i nazwy zadania używasz LIB do wykonania. LIB akceptuje również danych wejściowych wiersza polecenia pliki poleceń, które zostały opisane w poniższej sekcji. Biblioteka nie używa zmiennej środowiskowej.  
  
> [!NOTE]
>  Jeśli użytkownik jest przyzwyczajony do LINK32.exe i LIB32.exe narzędzi pod warunkiem z Microsoft Win32 oprogramowania Development Kit dla systemu Windows NT, może był używany albo polecenie `link32 -lib` lub polecenia `lib32` zarządzanie bibliotekami i tworzenia Importuj biblioteki. Należy zmienić pliki reguł programu make i partii plików do użycia `lib` zamiast tego polecenia.  
  
## <a name="lib-command-files"></a>Pliki poleceń LIB  
 Argumenty wiersza polecenia można przekazać do LIB w pliku poleceń, używając następującej składni:  
  
```  
LIB @commandfile  
```  
  
 Plik `commandfile` jest plikiem tekstowym. Nie spację lub tabulator między może być znak @ (@) i nazwę pliku. Nie będzie domyślna zwiększenia; należy określić pełną nazwę pliku, w tym wszystkie rozszerzenia. Nie można używać symboli wieloznacznych. Można określić ścieżką bezwzględną ani względną z nazwą pliku.  
  
 W pliku poleceń argumentów może być oddzielone spacjami lub karty, jak w wierszu polecenia; mogą one również rozdzielone znakami nowego wiersza. Użyj średnika (;), aby oznaczyć komentarz. LIB ignoruje wszystkie po średniku do końca wiersza.  
  
 Całość lub część wiersza polecenia można określić w pliku poleceń, a następnie można użyć więcej niż jeden plik polecenia w poleceniu LIB. LIB akceptuje dane wejściowe polecenia pliku tak, jakby zostały określone w tej lokalizacji, w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżone. LIB echa zawartość pliki poleceń, chyba że używana jest opcja/nologo.  
  
## <a name="using-lib-options"></a>Przy użyciu opcji LIB  
 Opcja składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), a po niej nazwę opcji. Nie można stosować skrót nazw opcji. Niektóre opcje przyjmuje argumentu, podać po dwukropkiem (:). Bez spacji i karty są dozwolone w obrębie Specyfikacja opcji. Użyj spacji lub karty do oddzielania specyfikacje opcji w wierszu polecenia. Opcja nazwy i ich argumentów Nazwa pliku lub słowo kluczowe nie są z uwzględnieniem wielkości liter, ale identyfikatory używane jako argumenty jest uwzględniana wielkość liter. LIB przetwarza opcje w kolejności określonej w wierszu polecenia i pliki poleceń. Jeśli opcja jest powtarzany różnych argumentów, pierwszeństwo ma ostatnią do przetworzenia.  
  
 Następujące opcje są stosowane do wszystkich rodzajów LIB:  
  
 / ERRORREPORT [BRAK &#124; WIERSZ &#124; KOLEJKI &#124; WYŚLIJ]  
 Jeśli lib.exe zakończy się niepowodzeniem w czasie wykonywania, można użyć/errorreport wysyłać informacje do firmy Microsoft informacji o tych błędach wewnętrznych.  
  
 Aby uzyskać więcej informacji na temat/errorreport, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 / LTCG  
 Powoduje, że biblioteka ma zostać utworzony przy użyciu Generowanie łączonych kodów czasowych.  Aby uzyskać więcej informacji, zobacz [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 / MACHINE  
 Określa platformę docelową dla programu. Zwykle nie trzeba określić/Machine. LIB wnioskuje typ maszyny z plików .obj. W niektórych sytuacjach LIB nie można określić typu maszyny i generuje komunikat o błędzie. Jeśli takie wystąpienie błędu, należy określić/Machine. W trybie/extract ta opcja jest wyłącznie na potrzeby weryfikacji. Użyj `lib /?` w wierszu polecenia, aby wyświetlić typy dostępnych maszyny.  
  
 /NOLOGO  
 Pomija wyświetlanie LIB praw autorskich wiadomości oraz numer wersji i uniemożliwia wyświetlanie plików polecenia.  
  
 / VERBOSE  
 Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików .obj dodawany. Informacje są wysyłane na wyjście standardowe i mogą zostać przekierowane do pliku.  
  
 /WX [: NO]  
 Traktuj ostrzeżenia jako błędy. Zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](../../build/reference/wx-treat-linker-warnings-as-errors.md) Aby uzyskać więcej informacji.  
  
 Inne opcje są stosowane tylko do określonych rodzajów LIB. Te opcje są omówione w sekcjach zawierająca opis każdego trybu.  
  
## <a name="see-also"></a>Zobacz też  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)