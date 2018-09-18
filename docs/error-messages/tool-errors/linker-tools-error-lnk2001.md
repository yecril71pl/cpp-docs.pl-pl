---
title: Błąd narzędzi konsolidatora LNK2001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb8e560e46da06c4312ab4261016ccd5a5ddda68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017850"
---
# <a name="linker-tools-error-lnk2001"></a>Błąd narzędzi konsolidatora LNK2001

Nierozpoznany symbol zewnętrzny "*symbol*"

Skompilowany kod sprawia, że odwołanie lub wywołanie *symbol*, ale ta symbol nie jest zdefiniowany w żadnym z biblioteki lub określono konsolidatora plików obiektów.

Ten komunikat o błędzie następuje błąd krytyczny [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Należy naprawić wszystkie LNK2001 i LNK2019 błędów, aby naprawić błąd LNK1120.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów, aby uzyskać ten błąd, ale wszystkie z nich obejmują odwołania do funkcji lub zmienna, która nie konsolidator *rozwiązać*, lub znaleźć definicję. Kompilator może wskazywać, gdy nie jest symbolem *zadeklarowana*, ale nie Jeśli nie zostanie *zdefiniowane*, ponieważ definicja może znajdować się w innym plikiem źródłowym lub biblioteki. Jeśli symbol jest określone, ale nigdy nie jest zdefiniowany, konsolidator generuje błąd.

### <a name="coding-issues"></a>Występujące problemy z kodem

Ten błąd może być spowodowany przez przypadek niezgodnego kodu źródłowego lub definicji modułu (.def) pliku. Na przykład, jeśli nazwa zmiennej `var1` w języku C++ w jednym pliku źródłowego, a następnie spróbuj dostępu do niego jako `VAR1` w innym, ten błąd jest generowany. Aby rozwiązać ten problem, użyj spójnie Pisownia i z uwzględnieniem wielkości liter nazwy.

Przyczyną tego błędu może być w projekcie, który używa [ze śródwierszowaniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md) po zdefiniowaniu funkcji w pliku źródłowym, a nie w pliku nagłówkowym. Funkcje śródwierszowe nie są widoczne poza pliku źródłowego, który definiuje je. Aby rozwiązać ten problem, należy zdefiniować funkcje śródwierszowe w nagłówkach, gdzie są one zgłoszone.

Przyczyną tego błędu może być wywołanie funkcji C z program w języku C++, bez korzystania z `extern "C"` deklaracji pod kątem funkcji C. Kompilator używa innego symbolu wewnętrzne konwencje nazewnictwa dla kodu C i C++, a jest to nazwa wewnętrznego symboli, konsolidator szuka podczas rozpoznawania symboli. Aby rozwiązać ten problem, należy użyć `extern "C"` otokę wszystkie deklaracje funkcji języka C, używany w kodzie języka C++, który powoduje, że kompilator języka C Konwencja nazewnictwa wewnętrznego na użytek tych symboli. Opcje kompilatora [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) i [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) powodować, że kompilator do kompilowania plików jako C++ lub C, odpowiednio, niezależnie od rozszerzenia nazwy pliku. Te opcje mogą powodować nazwy wewnętrznej funkcji, które różni się od oczekiwań.

Ten błąd może być spowodowany przez próba odwoływać się do funkcji lub dane, które nie mają powiązania zewnętrzne. W języku C++, funkcje śródwierszowe a `const` dane mają wewnętrzne łączenie, chyba że wyraźnie określono jako `extern`. Aby rozwiązać ten problem, należy użyć jawnej `extern` deklaracje symboli określonych poza definiujące pliku źródłowego.

Ten błąd może być spowodowany przez [Brak treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md) definicji. Ten błąd jest typowa, gdy deklarowania, ale nie Definiuj, zmiennych, funkcji lub klasy w kodzie. Kompilator musi jedynie prototyp funkcji lub `extern` deklaracja zmiennej, aby wygenerować plik obiektu bez błędów, ale konsolidator nie można rozpoznać wywołania funkcji lub odwołanie do zmiennej, ponieważ nie ma już miejsca kodu lub zmienna — funkcja zastrzeżone. Aby rozwiązać ten problem, upewnij się, że każdego odwołania funkcji i zmiennych jest w pełni zdefiniowana w pliku źródłowym lub biblioteki uwzględnione w linku.

Ten błąd może być spowodowany przez wywołanie funkcji, korzystającą z typy zwracane i parametru lub konwencji wywoływania, które nie pasują do definicji funkcji. W plikach obiektowych C++ [nazwij dekorację](../../error-messages/tool-errors/name-decoration.md) dołącza do nazwy końcowego dekorowane — funkcja, która jest używana jako symbol do dopasowania, gdy wywołuje w celu konwencji wywoływania, zakres klasą lub przestrzenią nazw i typy zwracane i parametru funkcji Funkcja z innych plików obiektu są rozpoznawane. Aby rozwiązać ten problem, należy upewnić się czy deklaracji, definicji i wywołania funkcji wszystkich tymi samymi zakresami, typy i Konwencje wywoływania.

Ten błąd może być spowodowany w przypadku kodu C++, gdy zawierają prototypu funkcji w definicji klasy, ale nie można [obejmują implementacji](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkcji, a następnie wywołaj ją. Aby rozwiązać ten problem, należy podać definicję dla wszystkich o nazwie zadeklarowane elementy członkowskie klasy.

Ten błąd może być spowodowany przez próba wywołania czystej funkcji wirtualnej z abstrakcyjną klasę bazową. Czysta funkcja wirtualna nie ma klasy podstawowej implementacji. Aby rozwiązać ten problem, upewnij się, że wszystkie funkcje wirtualne nazywane są implementowane.

Ten błąd może być spowodowany przez próby użycia Zmienna zadeklarowana wewnątrz funkcji ([zmienną lokalną](../../error-messages/tool-errors/automatic-function-scope-variables.md)) poza zakresem tej funkcji. Aby rozwiązać ten problem, Usuń odwołanie do zmiennej, która nie znajduje się w zakresie lub przenieść zmienną do wyższych zakresu.

Ten błąd może wystąpić, gdy tworzenie dystrybucyjnej wersji projektu ATL produkujących komunikat, że kod uruchamiający CRT jest wymagana. Aby rozwiązać ten problem, wykonaj jedną z następujących pozycji,

- Usuń `_ATL_MIN_CRT` z listy preprocesora definiuje CRT uruchamiania kodu do uwzględnienia. Zobacz [strona właściwości ogólnych (projekt)](../../ide/general-property-page-project.md) Aby uzyskać więcej informacji.

- Jeśli to możliwe Usuń wywołania funkcji CRT, które wymagają CRT uruchamiania kodu. Zamiast tego należy użyć ich odpowiedników Win32. Na przykład użyć `lstrcmp` zamiast `strcmp`. Znane funkcje, które wymagają CRT uruchamiania kodu przedstawiono niektóre ciągu i zmiennoprzecinkowy funkcje punktu.

### <a name="compilation-and-link-issues"></a>Problemy związane z kompilacji i link

Ten błąd może wystąpić, gdy w projekcie brakuje odwołania do biblioteki (. LIB) lub obiekt (. Plik OBJ). Aby rozwiązać ten problem, Dodaj odwołanie do obiektu pliku lub biblioteki wymaganej do projektu. Aby uzyskać więcej informacji, zobacz [pliki .lib — wejście konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

Ten błąd może wystąpić, jeśli używasz [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) lub [/Zl](../../build/reference/zl-omit-default-library-name.md) opcje. Po określeniu tych opcji, bibliotek, które zawierają kod wymagany nie są połączone z projektem, chyba że jawnie zostały uwzględnione. Aby rozwiązać ten problem, należy jawnie dołączyć wszystkie biblioteki używane w wierszu polecenia łącza. Jeśli widzisz wiele Brak CRT i standardowej biblioteki nazwy funkcji, korzystając z tych opcji, należy jawnie dołączyć plików CRT i standardowe biblioteki DLL lub biblioteki w linku.

Jeśli kompilujesz przy użyciu **/CLR** opcji, może być brak odwołania do .cctor. Aby rozwiązać ten problem, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md) Aby uzyskać więcej informacji.

Ten błąd może wystąpić, jeśli łączysz się do bibliotek tryb wersji podczas kompilowania wersji debugowania aplikacji. Podobnie jeśli używasz opcji **/mtd** lub **/mdd** lub zdefiniować `_DEBUG` i następnie łączyć się z bibliotekami wersji, możesz spodziewać się wielu potencjalnych nierozpoznane obiekty zewnętrzne, wśród innych problemów. Łączenie kompilacji tryb wydania z biblioteki debugowania również powoduje, że podobne problemy. Aby rozwiązać ten problem, upewnij się, użyj biblioteki debugowania w kompilacjach do debugowania i kompilacji detalicznej biblioteki w sieci sprzedaży detalicznej.

Ten błąd może wystąpić, jeśli kod odwołuje się do określonego symbolu z jednej wersji biblioteki, ale Podaj inną wersję biblioteki do konsolidatora. Ogólnie rzecz biorąc nie można mieszać plików obiektu lub bibliotek, które są tworzone dla różnych wersji kompilatora. Biblioteki, które są dostarczane w nowej wersji mogą zawierać symbole, których nie można znaleźć w bibliotekach dołączone do poprzednich wersji i na odwrót. Aby rozwiązać ten problem, tworzy plików obiektów i bibliotek w tej samej wersji kompilatora przed łącząc je ze sobą.

-  Narzędzia &#124; opcje &#124; projektów &#124; katalogi VC ++ okno dialogowe, w obszarze Wybór plików biblioteki umożliwia zmianę kolejności przeszukiwania bibliotek. Folder łączący strony właściwości projektu w oknie dialogowym może również zawierać ścieżek, które mogą być nieaktualne.

-  Ten problem może występować, gdy nowy zestaw SDK jest zainstalowany (być może do innej lokalizacji), a kolejność wyszukiwania nie jest aktualizowana, aby wskazywał nową lokalizację. Zazwyczaj należy umieścić ścieżki do nowego zestawu SDK obejmują i lib katalogów przed domyślna lokalizacja Visual C++. Ponadto projektu zawierającego ścieżek osadzonych nadal mogą wskazywać na starej ścieżki, które są prawidłowe, ale jest zgodna z nowych funkcji dodanych przez nową wersję, który jest zainstalowany w innej lokalizacji.

- Jeśli kompilujesz w wierszu polecenia i w związku z tym zostały utworzone własne zmienne środowiskowe, sprawdź, czy ścieżki do narzędzia, biblioteki i pliki nagłówkowe, przejdź do wersji spójne. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

Obecnie nie istnieje standard dla [nazewnictwa C++](../../error-messages/tool-errors/name-decoration.md) między dostawcami kompilatora lub nawet między różnymi wersjami kompilatora. W związku z tym konsolidacji plików obiektu skompilowany za pomocą innych kompilatorów może nie generuje ten sam schemat nazewnictwa, powodując błąd LNK2001.

[Mieszanie wbudowane i innych niż inline opcji kompilacji](../../error-messages/tool-errors/function-inlining-problems.md) różnych modułów mogą powodować LNK2001. Jeśli biblioteka języka C++ jest tworzony za pomocą funkcji wbudowanie włączona (**/Ob1** lub **/ob2**), ale odpowiedni plik nagłówkowy opisujących funkcje wbudowanie wyłączone (nie `inline` — słowo kluczowe), ten błąd występuje. Aby rozwiązać ten problem, należy zdefiniować funkcje `inline` w pliku nagłówkowym, należy uwzględnić w innych plikach źródłowych.

Jeśli używasz `#pragma inline_depth` kompilatora dyrektywy, upewnij się, że masz [wartości 2 lub nowszy zestaw](../../error-messages/tool-errors/function-inlining-problems.md)i upewnij się, możesz także użyć [/Ob1](../../build/reference/ob-inline-function-expansion.md) lub [/ob2](../../build/reference/ob-inline-function-expansion.md) — opcja kompilatora.

Ten błąd może wystąpić, jeśli pominięto łącze opcja/noentry, tworząc DLL tylko dla zasobów. Aby rozwiązać ten problem, należy dodać opcję/noentry polecenia łącza.

Ten błąd może wystąpić, jeśli używasz ustawienia/Entry lub nieprawidłowa/Subsystem w projekcie. Na przykład, jeśli napisanie aplikacji konsolowej, a następnie określ/Subsystem: Windows, nierozpoznane zewnętrznych zostanie wygenerowany błąd dla `WinMain`. Aby rozwiązać ten problem, upewnij się, że zgodne z opcjami typu projektu. Aby uzyskać więcej informacji na temat tych opcji i punkty wejścia, zobacz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) i [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje konsolidatora.

### <a name="exported-symbol-issues"></a>Problemy z wyeksportowanego symbolu

Ten błąd występuje, gdy Eksport wymienione w pliku .def nie zostanie znaleziony. Być może on nie istnieje, jest wpisany niepoprawnie lub korzysta z nazw ozdobionych języka C++. Plik .def nie przyjmuje nazwy dekorowane. Aby rozwiązać ten problem, usuń zbędne eksporty i użyj `extern "C"` deklaracje dla eksportowanego symboli.

## <a name="what-is-an-unresolved-external-symbol"></a>Co to jest nierozpoznany symbol zewnętrzny?

A *symbol* jest nazwą funkcji lub zmienna globalna używane wewnętrznie pliku obiektu skompilowanego lub biblioteki. Symbol jest *zdefiniowane* w pliku obiektu której Magazyn jest przydzielany zmienną globalną lub funkcji, gdzie znajduje się skompilowany kod w treści funkcji. *Symbol zewnętrzny* jest symbolem to *odwołania*, oznacza to, że używane lub o nazwie w jeden obiekt pliku, ale zdefiniowane w innym pliku biblioteki lub obiektu. *Wyeksportowane symbol* to taki, który został udostępniony publicznie przez plik obiektu lub biblioteki, który go definiuje. Konsolidator musi *rozwiązać*, lub znaleźć pasujących definicji dla każdego symbol zewnętrzny przywoływane przez plik obiektu, gdy jest on połączony do aplikacji lub biblioteki DLL. Konsolidator generuje błąd, gdy nie można rozpoznać zewnętrzny symbol znajdując pasujące do wyeksportowanego symbolu w dowolnym z połączonych plików.

## <a name="use-the-decorated-name-to-find-the-error"></a>Użyj nazwy dekorowane, aby znaleźć błąd

Użyj kompilatora i konsolidatora C++ [nazwij Dekorację](../../error-messages/tool-errors/name-decoration.md), znane również jako *dekorowanie nazw*, aby zakodować dodatkowych informacji na temat typu zmiennej lub zwracany typ, typy parametrów, zakresu i wywoływania Konwencja funkcji w nazwę symbolu. To również nazwę uzupełnioną jest nazwa symbolu, konsolidator szuka Aby rozwiązać zewnętrzne symbole.

Ponieważ dodatkowych informacji staje się częścią nazwy symbolu, może spowodować błąd łącza, jeśli deklaracja funkcji lub zmienna nie jest dokładnie dopasowana definicji funkcji lub zmiennej. Można to zrobić, nawet jeśli ten sam plik nagłówkowy ma zarówno kod wywołujący, jak i kod definiujący, jeśli flagi kompilatora różnych są używane podczas kompilowania plików źródłowych. Na przykład możesz ten błąd może wystąpić, jeśli kod jest kompilowany do użycia `__vectorcall` konwencji wywoływania, ale łącze do biblioteki, który oczekuje, że klienci w celu wywołania go przy użyciu domyślnego `__cdecl` lub `__fastcall` konwencji wywoływania. W tym przypadku symbole nie są zgodne, ponieważ różnią się Konwencje wywoływania

Aby pomóc w znalezieniu przyczyny tego rodzaju błąd, komunikat o błędzie konsolidatora pokazuje zarówno "przyjaznej nazwy," Nazwa używana w kodzie źródłowym, a nazwę z atrybutami (w nawiasach) dla nierozpoznany symbol zewnętrzny. Nie musisz wiedzieć, jak przekształcać nazwę uzupełnioną, aby można było porównać je z innymi nazwy dekorowane. Można użyć narzędzia wiersza polecenia, które są dołączone przez kompilator, aby porównać nazwę oczekiwany symbol i nazwę rzeczywisty symbol:

- [/EKSPORTUJE](../../build/reference/dash-exports.md) i [/symbole](../../build/reference/symbols.md) opcje narzędzia wiersza polecenia DUMPBIN może pomóc odkryć, w której symbole są zdefiniowane w plikach dll i obiektu lub biblioteki. Możesz użyć tego, aby sprawdzić wyeksportowany dekorowane odpowiada nazwy dekoracyjne konsolidator nazwy wyszukuje.

W niektórych przypadkach konsolidator może zgłaszać tylko nazwę z atrybutami symbolu. Narzędzia wiersza polecenia UNDNAME umożliwia pobieranie niedekorowanego formularza dekorowaną nazwę.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji na temat możliwych przyczyn i rozwiązań dla LNK2001 zobacz pytanie dotyczące przepełnienia stosu [co to jest błąd zewnętrzny symbol Niezdefiniowany odwołania/nierozpoznanych i jak go naprawić?](http://stackoverflow.com/q/12573816/2002113).

