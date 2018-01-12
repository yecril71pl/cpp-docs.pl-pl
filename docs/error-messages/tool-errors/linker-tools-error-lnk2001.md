---
title: "Błąd narzędzi konsolidatora LNK2001 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2001
dev_langs: C++
helpviewer_keywords: LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51f78f436d0e19779d0ebca499a559a60d12bcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2001"></a>Błąd narzędzi konsolidatora LNK2001
Nierozpoznany zewnętrzny symbol "*symbol*"  
  
Skompilowany kod sprawia, że odwołanie lub wywołanie *symbol*, ale ten symbol nie jest zdefiniowany w żadnym z biblioteki lub określono do konsolidatora plików obiektów.  
  
Ten komunikat o błędzie następuje błąd krytyczny [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Należy naprawić wszystkie LNK2001 i LNK2019 błędów, aby naprawić błąd LNK1120.  
  
## <a name="possible-causes"></a>Możliwe przyczyny  
  
Istnieje wiele sposobów, aby uzyskać ten błąd, ale dotyczą wszystkich z nich odwołanie do funkcji lub zmienna, która nie konsolidator *rozwiązać*, lub znaleźć definicji. Kompilator może wskazywać, gdy nie jest symbolem *zadeklarowany*, ale nie po nie jest *zdefiniowane*, ponieważ definicja może znajdować się w innym plikiem źródłowym lub biblioteki. Jeśli symbol jest określone, ale nigdy nie jest zdefiniowany, konsolidator generuje błąd.  
  
### <a name="coding-issues"></a>Kodowanie problemów  
  
Ten błąd może być spowodowane niezgodnymi przypadku w kodzie źródłowym lub definicji modułu (.def) pliku. Na przykład, jeśli nazwa zmiennej `var1` w języku C++ jeden plik źródłowy i spróbuj uzyskać dostęp jako `VAR1` w innym, ten błąd jest generowany. Aby rozwiązać ten problem, użyj spójnie wpisana i z uwzględnieniem wielkości liter nazwy.  
  
Ten błąd może być spowodowany w projekcie, który używa [ze śródwierszowaniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md) w przypadku definiowania funkcji w pliku źródłowym, a nie w pliku nagłówka. Wbudowane funkcje nie są widoczne poza plik źródłowy, który definiuje je. Aby rozwiązać ten problem, zdefiniuj funkcje wbudowane w nagłówkach, jeśli są one zgłaszane.  
  
Ten błąd może być spowodowany wywołania funkcji C programu C++ bez użycia `extern "C"` deklaracji funkcji C. Kompilator używa konwencji nazewnictwa inny symbol wewnętrzny dla kodu C i C++, a jest to nazwa symbolu wewnętrzny sprawdzający konsolidator podczas rozpoznawania symboli. Aby rozwiązać ten problem, należy użyć `extern "C"` otokę wszystkie deklaracje funkcji języka C, używany w kodzie C++, co powoduje, że kompilator, aby użyć wewnętrznego konwencji nazewnictwa C związanych z nimi. Opcje kompilatora [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) i [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) spowodować kompilator, aby skompilować plików jako C++ lub C, odpowiednio, niezależnie od rozszerzenia nazwy pliku. Te opcje mogą powodować funkcji wewnętrznej nazwy różne od oczekiwań.  
  
Przyczyną tego błędu może być próba odwołania funkcji lub danych, które nie mają połączenie zewnętrzne. W języku C++, wbudowanych funkcjach i `const` danych mieć powiązania wewnętrznego, chyba że jawnie określona jako `extern`. Aby rozwiązać ten problem, użyj jawnego `extern` deklaracje symboli określonych poza definiującego pliku źródłowego.  
  
Przyczyną tego błędu [Brak treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md) definicji. Ten błąd jest typowe zadeklarować, ale nie definiują, zmienne, funkcje i klasy w kodzie. Kompilator musi tylko prototypu funkcji lub `extern` deklaracja zmiennej, aby wygenerować plik obiektu bez błędów, ale konsolidator nie można rozpoznać wywołania funkcji lub odwołanie do zmiennej, ponieważ brakuje miejsca na kod lub zmienna — funkcja zastrzeżone. Aby rozwiązać ten problem, upewnij się, co funkcja przywoływany i zmienna jest pełni zdefiniowana w pliku źródłowym lub zawarte w link do biblioteki.  
  
Ten błąd może być spowodowany przez wywołanie funkcji używającej typy zwracane i parametru lub konwencji wywoływania, które nie pasują do definicji funkcji. W plikach obiektu języka C++ [nazwa decoration](../../error-messages/tool-errors/name-decoration.md) zawiera w nazwie końcowego ozdobione funkcji, który jest używany jako symbol do dopasowania, kiedy wywołań Konwencja wywoływania, zakres klasy lub obszaru nazw i typy zwracane i parametru funkcji Funkcja z innych plików obiektu zostaną rozpoznane. Aby rozwiązać ten problem, upewnij się, że deklaracji, definicji i wywołań funkcji wszystkie użyć tymi samymi zakresami, typy i konwencji wywoływania.  
  
Ten błąd może być spowodowany w kodzie C++ obejmują prototypu funkcji w definicji klasy, ale się nie powieść [obejmują implementacja](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkcji, a następnie wywołać ją. Aby rozwiązać ten problem, należy koniecznie zawierają definicje dla wszystkich wywołuje element członkowski klasy zadeklarowany.  
  
Próba wywołania czystej funkcji wirtualnej z abstrakcyjną klasę podstawową mogą być przyczyną tego błędu. Czystej funkcji wirtualnej ma żadnej implementacji klasy podstawowej. Aby rozwiązać ten problem, upewnij się, że wszystkie wywołuje funkcje wirtualne są implementowane.  
  
Ten błąd może być spowodowane korzystaniem Zmienna zadeklarowana wewnątrz funkcji ([zmiennej lokalnej](../../error-messages/tool-errors/automatic-function-scope-variables.md)) poza zakres tej funkcji. Aby rozwiązać ten problem, Usuń odwołanie do zmiennej, która nie znajduje się w zakresie lub przenieść zmienną do wyższych zakresu.  
  
Ten błąd może wystąpić podczas tworzenia wersji projektu ATL zwracające komunikat, że kod uruchomienia CRT jest wymagana. Aby rozwiązać ten problem, wykonaj jedną z następujących czynności:  
  
-   Usuń `_ATL_MIN_CRT` z listy preprocesora definiuje CRT uruchamiania kodu do uwzględnienia. Zobacz [ogólna strona właściwości (projekt)](../../ide/general-property-page-project.md) Aby uzyskać więcej informacji.  
  
-   Jeśli to możliwe Usuń wywołania funkcji CRT, które wymagają CRT uruchamiania kodu. Zamiast tego należy użyć ich odpowiedniki Win32. Na przykład użyć `lstrcmp` zamiast `strcmp`. Znane funkcji, które wymagają CRT uruchamiania kodu przedstawiono niektóre ciągu i przestawne funkcje punktu.  
  
### <a name="compilation-and-link-issues"></a>Problemy z kompilacji i link  
  
Ten błąd może wystąpić, gdy w projekcie brakuje odwołania do biblioteki (. LIB) lub w obiekcie (. Plik OBJ). Aby rozwiązać ten problem, Dodaj odwołanie do obiektu pliku lub biblioteki wymaganej do projektu. Aby uzyskać więcej informacji, zobacz [pliki .lib — wejście konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).  
  
Ten błąd może wystąpić, jeśli używasz [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) lub [/Zl](../../build/reference/zl-omit-default-library-name.md) opcje. Po określeniu tych opcji, bibliotek, które zawierają kodu nie są połączone w projekcie, chyba że jawnie zostały uwzględnione. Aby rozwiązać ten problem, jawnie obejmują wszystkie biblioteki, używanego w wierszu polecenia łącza. Jeśli widzisz wiele Brak CRT lub biblioteki standardowej nazwy funkcji, korzystając z tych opcji, jawnie Dołącz pliki CRT i standardowej biblioteki DLL lub biblioteki w łączu.  

Jeśli kompilacja przy użyciu **/CLR** opcji, mogą być brakujące odwołanie do .cctor. Aby rozwiązać ten problem, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md) Aby uzyskać więcej informacji.  
  
Ten błąd może wystąpić, gdy łącze do bibliotek tryb wersji, podczas kompilowania wersję do debugowania aplikacji. Podobnie jeśli używasz opcji **/MTd** lub **/mdd** lub zdefiniuj `_DEBUG` , a następnie łączyć się z bibliotekami wersji, można spodziewać się wielu potencjalnych externals nierozwiązane, między innymi problemami. Łączenie trybu kompilacji wydania z biblioteki debugowania powoduje także, że podobne problemy. Aby rozwiązać ten problem, upewnij się, można korzystać z bibliotek debugowania w kompilacjach do debugowania i kompilacje bibliotek sprzedaży detalicznej w sieci sprzedaży detalicznej.  
  
Ten błąd może wystąpić, jeśli kod odnosi się do symbolu z jednej wersji biblioteki, ale podasz inną wersję biblioteki do konsolidatora. Ogólnie rzecz biorąc nie można mieszać plików obiektu i bibliotek, które są tworzone dla różnych wersji kompilatora. Biblioteki, które są dostarczane w nowej wersji może zawierać symbole, których nie można znaleźć biblioteki dołączony do poprzednich wersji i na odwrót. Aby rozwiązać ten problem, należy utworzyć wszystkich plików obiektu i bibliotek w tej samej wersji kompilatora przed łącząc je ze sobą.  
  
-  Narzędzia &#124; Opcje &#124; Projekty &#124; Katalogi VC ++ okna dialogowego, w obszarze Wybieranie plików biblioteki, można zmienić kolejność wyszukiwania biblioteki. Folder konsolidatora w oknie dialogowym stron właściwości projektu może również zawierać ścieżek, które mogą być nieaktualne.  
  
-  Ten problem może występować, gdy nowy zestaw SDK jest zainstalowany (np. do innej lokalizacji), a kolejność wyszukiwania nie jest aktualizowany, aby wskazywał nową lokalizację. Zazwyczaj należy umieścić ścieżce do nowej wersji zestawu SDK obejmują i lib katalogów przed domyślnej lokalizacji Visual C++. Ponadto projektu zawierającego ścieżek osadzonych nadal może wskazywać stare ścieżek, które są prawidłowe, ale nieaktualny dla nowe funkcje dodane przez nową wersję zainstalowanego w innej lokalizacji.  
  
-   Jeśli kompilacji w wierszu polecenia i utworzono zmienne środowiskowe, sprawdź, czy ścieżki do narzędzi, bibliotek i pliki nagłówkowe, przejdź do wersji spójne. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
  
Nie ma obecnie standard [nazewnictwa C++](../../error-messages/tool-errors/name-decoration.md) między dostawców kompilatora lub nawet między różnymi wersjami kompilatora. W związku z tym konsolidacji plików obiektu skompilowanego z inne kompilatory mogą nie tworzyć sam schemat nazewnictwa, powodując błąd LNK2001.  
  
[Mieszania wbudowanego i z systemem innym niż wbudowany skompilować opcje](../../error-messages/tool-errors/function-inlining-problems.md) w różnych modułach może spowodować LNK2001. Jeśli biblioteka języka C++ tworzona jest włączona ze śródwierszowaniem funkcji (**/Ob1** lub **/ob2**), ale odpowiadający mu plik nagłówka opisujące funkcji ma ze śródwierszowaniem wyłączone (nie `inline` — słowo kluczowe), ten błąd występuje. Aby rozwiązać ten problem, zdefiniuj funkcji `inline` w pliku nagłówka obejmują w innych plikach źródłowych.  
  
Jeśli używasz `#pragma inline_depth` kompilatora dyrektywy, upewnij się, że masz [wartości 2 lub nowszym zestawu](../../error-messages/tool-errors/function-inlining-problems.md)i upewnij się, że używasz również [/Ob1](../../build/reference/ob-inline-function-expansion.md) lub [/ob2](../../build/reference/ob-inline-function-expansion.md) — opcja kompilatora.  
  
Ten błąd może wystąpić, jeśli pominięto łącze/noentry — opcja podczas tworzenia biblioteki DLL tylko z zasobami. Aby rozwiązać ten problem, dodaj opcję/noentry do polecenia łącze.  
  
Ten błąd może wystąpić, jeśli używasz ustawienia/Entry lub nieprawidłowa/Subsystem w projekcie. Na przykład, jeśli napisać aplikację konsoli i określ/Subsystem: Windows nierozwiązane zewnętrznych generowany jest błąd dla `WinMain`. Aby rozwiązać ten problem, upewnij się, że odpowiada opcji, aby typ projektu. Aby uzyskać więcej informacji o tych opcji i punkty wejścia, zobacz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) i [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje konsolidatora.  
  
### <a name="exported-symbol-issues"></a>Problemy z wyeksportowanego symbolu  
  
Ten błąd występuje, gdy nie można odnaleźć eksportu wymienione w pliku .def. Może to być, ponieważ nie istnieje, jest nieprawidłowo napisane lub korzysta z nazw C++ dekorowane. Plik .def nie przyjmuje nazwy ozdobione. Aby rozwiązać ten problem, usuń zbędne eksportu, a następnie użyj `extern "C"` deklaracje wyeksportowanego symboli.  
  
## <a name="what-is-an-unresolved-external-symbol"></a>Co to jest nierozpoznany zewnętrzny symbol?  
  
A *symbol* jest nazwą funkcji lub zmienna globalna używane wewnętrznie pliku obiektu skompilowanego lub biblioteki. Symbol jest *zdefiniowane* w pliku obiektu gdzie magazynu jest przydzielony do zmiennej globalnej lub funkcję, rozmieszczenia skompilowany kod ciała funkcji. *Zewnętrzny symbol* to symbol to jest *przywoływanego*, oznacza to, że używane lub o nazwie w jeden obiekt pliku, ale zdefiniowane w innym pliku biblioteki lub obiektu. *Wyeksportowane symbol* to taki, który ma zostać udostępnione publicznie przez plik obiektu lub biblioteki, który definiuje on. Konsolidator musi *rozwiązać*, lub odnaleźć pasującego definicji dla każdego symbolu zewnętrznego odwołuje pliku obiektu, gdy jest on połączony do aplikacji lub DLL. Konsolidator generuje błąd, gdy nie można rozpoznać symbolu zewnętrznego znajdując pasujące do wyeksportowanego symbolu w żadnym z połączonych plików.    
  
## <a name="use-the-decorated-name-to-find-the-error"></a>Znajdź błąd, użyj nazwy ozdobione
  
Użyj kompilatorze i konsolidatorze C++ [nazwij Dekorację](../../error-messages/tool-errors/name-decoration.md), znanej także jako *przekręcona nazwa*, aby zakodować dodatkowych informacji na temat typu zmienną lub typ zwracany, typów parametrów, zakresu i wywoływania Konwencja funkcję nazwę symbolu. Ta nazwa ozdobione jest nazwa symbolu konsolidator wyszukuje do rozpoznawania symboli zewnętrznych.  
  
Ponieważ dodatkowe informacje o stanie się częścią nazwy symbolu, błąd łącza może spowodować, jeśli deklaracja funkcji lub zmienna jest dokładnie zgodny z definicją funkcji lub zmienna. Może to nastąpić, nawet jeśli ten sam plik nagłówka jest używany zarówno kod wywołujący, jak i kod definiujący, jeśli flagi różnych kompilatora są używane podczas kompilowania plików źródłowych. Na przykład można uzyskać ten błąd, jeśli kod jest skompilowany do użycia `__vectorcall` Konwencja wywoływania, ale łącze do biblioteki, która oczekuje klientów w celu wywołania go przy użyciu domyślnego `__cdecl` lub `__fastcall` konwencji wywoływania. W takim przypadku symbole są niezgodne, ponieważ różnią się konwencji wywoływania   
  
Aby ustalić przyczynę tego typu błędów konsolidatora komunikat o błędzie zawiera zarówno "Przyjazna nazwa" Nazwa używana w kodzie źródłowym i dekoracyjną nazwę (w nawiasach) nierozpoznany zewnętrzny symbol. Nie trzeba znać sposób przetłumaczenia ozdobione nazwy, aby można było porównać je z innych nazwy ozdobione Można użyć narzędzia wiersza polecenia, które są dołączone kompilator, aby porównać nazwy oczekiwany symbol i nazwy rzeczywisty symbol:  

-   [/EKSPORTUJE](../../build/reference/dash-exports.md) i [/symbole](../../build/reference/symbols.md) opcje narzędzia wiersza polecenia DUMPBIN ułatwiają odnajdywanie symbole, które są zdefiniowane w plików dll i obiektu lub biblioteki. Służy to do sprawdzenia wyeksportowany dekorowane nazwy ozdobione konsolidator nazwy wyszukuje odpowiada.  
  
W niektórych przypadkach konsolidator tylko zgłosić dekoracyjną nazwę symbolu. Można użyć narzędzia wiersza polecenia UNDNAME uzyskać formularzu bez nazwy ozdobione.  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
  
Aby uzyskać więcej informacji o możliwe przyczyny i rozwiązania LNK2001, zobacz pytanie przepełnienie stosu [co to jest błąd zewnętrzny symbol Niezdefiniowany odwołanie/nierozpoznane i jak go naprawić?](http://stackoverflow.com/q/12573816/2002113).  

