---
title: 'TN035: Przy użyciu wielu plików zasobów i plików nagłówków z programem Visual C++'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 0493dd45caf5eb78da435987a4590442a908a5a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305518"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: Przy użyciu wielu plików zasobów i plików nagłówków z programem Visual C++

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje, jak edytor zasobów Visual C++ obsługuje wiele plików zasobów i plików nagłówkowych współdzielonych w jednym projekcie lub współdzielonych przez wiele projektów, a także jak można korzystać z zalet tej pomocy technicznej. Ta uwaga odpowiada na te pytania:

- Kiedy może chcesz podzielić projekt na wiele plików zasobów i/lub plików nagłówkowych i jak to zrobić

- Jak udostępnić typowego nagłówka. Plik H między dwoma. RC — pliki

- Jak podzielić zasoby projektu na wiele. RC — pliki

- Jak Ty (i narzędzi) zarządzać zależnościami kompilacji między. WERSJI RC. CPP, i. Pliki H

Należy pamiętać, że po dodaniu dodatkowego pliku zasobów do swojego projektu, ClassWizard nie rozpozna zasobów w dodanym pliku.

Ta uwaga są skonstruowane do na powyższe pytania w następujący sposób:

- **Omówienie sposobu Visual C++ zarządza plików zasobów i plików nagłówkowych** zawiera omówienie sposobu zestaw zasobów zawiera polecenie w programie Visual C++ umożliwia korzystanie z wielu plików zasobów i plików nagłówkowych w tym samym projekcie.

- **Analiza utworzona przez AppWizard. RC i. Pliki H** patrzy na wiele plików zasobów i nagłówkowych, które są używane przez aplikacje utworzone przez kreatora AppWizard. Te pliki stanowią dobry model dla dodatkowych plików zasobów i plików nagłówkowych, które możesz zechcieć dodać do projektu.

- **W tym dodatkowych plików nagłówkowych** opisano, gdzie możesz chcieć dołączyć wiele plików nagłówkowych i zawiera szczegółowe informacje, jak to zrobić.

- **Udostępnianie pliku nagłówkowego przez dwa. Pliki RC** pokazuje, jak można współdzielić jeden plik nagłówkowy między wieloma. RC — pliki w różnych projektach lub w tym samym projekcie.

- **Korzystanie z wielu plików zasobów, w tym samym projekcie** opisuje, w których warto rozważyć rozdzielenie projektu na wiele. RC pliki i zawiera szczegółowe informacje, jak to zrobić.

- **Wymuszanie nieedytowalne pliki Visual C++** w tym artykule opisano, jak można upewnić się, Visual C++ nie edytuje i przypadkowo formatowania niestandardowych zasobów.

- **Zarządzanie symbolami Współdzielonymi przez wiele Visual C++, edytować. Pliki RC** zawiera opis sposobu udostępniania tych samych symboli przez wiele. RC — pliki i jak należy unikać przypisywania zduplikowanych wartości liczbowych Identyfikatora.

- **Zarządzanie zależnościami między. WERSJI RC. CPP, i. Pliki H** w tym artykule opisano, jak Visual C++ pozwala uniknąć niepotrzebnego ponownego kompilowania. Pliki CPP, które są zależne od plików symboli zasobów.

- **Jak Visual C++ zarządza obejmuje informacji o zestawie** zawiera szczegółowe informacje techniczne dotyczące sposobu Visual C++ przechowuje informacje o wiele (zagnieżdżonych). RC — pliki i wiele plików nagłówkowych, które są # #include przez. Plik RC.

**Omówienie, jak Visual c++ zarządza plikami zasobów i plików nagłówkowych**

Visual C++ zarządza pojedynczym. Plik RC zasobów i odpowiadający mu. Plik nagłówkowy H jako parą ściśle powiązanych plików. Kiedy edytujesz i zapisujesz zasoby w. Plik RC, pośrednio edytujesz i zapisujesz symbole w odpowiadającym mu. Plik H. Mimo że można otwierać i edytować wiele. RC — pliki naraz (za pomocą interfejsu użytkownika interfejsu MDI programu Visual C++) dla każdego podane. Plik RC można pośrednio edytować dokładnie jeden odpowiedni plik nagłówkowy.

**Plik nagłówkowy symboli**

Domyślnie program Visual C++ zawsze nazywa odpowiedni plik nagłówkowy zasobów. Godz., niezależnie od nazwy pliku zasobów (np. MYAPP. RC). Za pomocą **zasób zawiera** polecenia **widoku** menu w Visual C++, można zmienić nazwę tego pliku nagłówkowego, aktualizując plik nagłówkowy symboli w **zestaw zawiera**okno dialogowe.

**Dyrektywy symboli tylko do odczytu**

Mimo że Visual C++ edytuje tylko jeden plik nagłówkowy dla każdego podane. Plik RC, Visual C++ obsługuje odwołania do symboli zdefiniowanych w dodatkowych plików nagłówkowych tylko do odczytu. Za pomocą **zasób zawiera** polecenia **widoku** menu w programie Visual C++ można określić dowolną liczbę dodatkowych plików nagłówkowych tylko do odczytu jako dyrektywy symboli tylko do odczytu. Ograniczenie "tylko do odczytu" oznacza, że podczas dodawania nowego zasobu w. Plik RC, można użyć symbolu zdefiniowanego w pliku nagłówkowym tylko do odczytu. ale jeśli usuniesz zasób, symbol nadal pozostaje zdefiniowany w pliku nagłówkowym tylko do odczytu. Nie można zmienić wartości numerycznej przypisanej do symbolu tylko do odczytu.

**Dyrektywy czasu kompilacji**

Visual C++ obsługuje również zagnieżdżanie plików zasobów, gdy jedna. Plik RC jest # dyrektywy #include w innym. Podczas edytowania danego. Plik RC przy użyciu języka Visual C++, wszystkie zasoby w # dyrektywy #include pliki nie są widoczne. Jednak podczas kompilacji. Plik RC # dyrektywy #include również są kompilowane pliki. Za pomocą **zasób zawiera** polecenia **widoku** menu w Visual C++, można określić dowolną liczbę # dyrektywy #include. RC — pliki jako dyrektywy czasu kompilacji.

Należy pamiętać, co się stanie, jeśli wczytasz do Visual C++. Plik RC #include inny. Plik RC, który jest *nie* określony jako dyrektywa czasu kompilacji. Ta sytuacja może powstać po przywróceniu do programu Visual C++. Plik RC, który użytkownik wcześniej utrzymywał ręcznie za pomocą edytora tekstów. Kiedy Visual C++ odczytuje # dyrektywy #include. Plik RC scala # wszytkie zasoby do obiektu nadrzędnego. Plik RC. Podczas zapisywania obiektu nadrzędnego. Plik RC # Instrukcja include w efekt, zostanie zastąpiony # wszytkie zasoby. Jeśli nie chcesz takiego połączenia, należy usunąć # instrukcję include z obiektu nadrzędnego. Plik RC *wcześniejsze* wczytaniem go do Visual C++; następnie przy użyciu języka Visual C++, dodać z powrotem takie same # instrukcję include jako dyrektywa czasu kompilacji.

Visual C++ zapisuje w. RC plik trzy rodzaje powyższych informacji zestaw zawiera (plik nagłówkowy symboli, dyrektywy symboli tylko do odczytu i dyrektywy czasu kompilacji) w # dyrektywy include *i* w zasobach TEXTINCLUDE. Zasoby TEXTINCLUDE, szczegóły implementacji, że nie trzeba zwykle do czynienia, są wyjaśnione w [jak Visual C++ zarządza zestawu zawiera informacje o](#_mfcnotes_tn035_set_includes).

**Analiza utworzona przez AppWizard. RC i. Pliki H**

Badanie kodu aplikacji, tworzonego przez AppWizard zapewnia wgląd w sposób Visual C++ zarządza wielu plików zasobów i plików nagłówkowych. Fragmenty kodu zbadane poniżej pochodzą z aplikacji MYAPP, stworzonej przez AppWizard przy użyciu opcji domyślnych.

Aplikacja utworzona przez AppWizard używa wielu plików zasobów i wielu plików nagłówkowych, zgodnie z opisem na poniższym diagramie:

```
RESOURCE.H     AFXRES.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    AFXRES.RC
    AFXPRINT.RC
```

Można przeglądać takie relacje plików za pomocą polecenia Plik Visual C++ +/ zestaw zawiera.

MYAPP. Plik zasobów aplikacji, który edytujesz za pomocą języka Visual C++ w wersji RC.

ZASÓB. Godz. jest to plik nagłówkowy charakterystyczny dla aplikacji. Zawsze nadaje mu nazwę ZASOBU. H przez AppWizard, zgodnie z domyślną Visual C++ nazwy pliku nagłówkowego. #Include dla tego pliku nagłówkowego to pierwsza instrukcja w pliku zasobów (MYAPP. RC):

```
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. RC2 zawiera zasoby, które nie będą edytowane przez Visual C++, ale zostaną uwzględnione w ostatecznym skompilowany. Plik EXE. Kreator AppWizard żadnych takich zasobów jest domyślnie tworzony przez, ponieważ Visual C++ może edytować wszystkie standardowe zasoby, łącznie z zasobami wersji (Nowa funkcja w tej wersji). Pusty plik jest generowana przez kreatora AppWizard w przypadku, gdy chcesz dodać swoje własne niestandardowo sformatowane zasoby do tego pliku.

Jeśli używasz niestandardowo sformatowane zasoby, możesz je dodać do RES\MYAPP. RC2 i edytować za pomocą edytora tekstu Visual C++.

AFXRES. RC i AFXPRINT. RC zawierają standardowe zasoby wymagane przez niektóre funkcje programu framework. Podobnie jak RES\MYAPP. Czy te dwa pliki zasobów dostarczone do framework RC2, # dołączony dyrektywą #include na końcu MYAPP. RC, dlatego są określone w dyrektywach czasu kompilacji w oknie dialogowym Zestaw zawiera. W związku z tym podczas bezpośrednio przeglądania lub edytowania tych zasobów platformy podczas edycji MYAPP. RC w programie Visual C++, ale są one kompilowane do pliku binarnego aplikacji. Plik RES i zakończenie. Plik EXE. Aby uzyskać więcej informacji na temat standardowych zasobów RAM, w tym procedur ich modyfikowania, zobacz [Uwaga techniczna 23](../mfc/tn023-standard-mfc-resources.md).

AFXRES. H definiuje standardowe symbole, takie jak `ID_FILE_NEW`, używane przez architekturę i używane konkretnie w AFXRES. RC. AFXRES. H również #include przez WINRES. Godz., który zawiera podzbiór systemu WINDOWS. H, które są wymagane przez wygenerowany Visual C++. RC — pliki, jak również AFXRES. RC. Symbole zdefiniowane w AFXRES. H są dostępne podczas edycji pliku zasobu aplikacji (MYAPP. RC). Na przykład `ID_FILE_NEW` jest używany dla elementu menu Plik nowy w MYAPP. RC w menu zasobów. Nie można zmienić ani usunąć tych symboli zdefiniowanych w platformie.

## <a name="_mfcnotes_tn035_including"></a> Włączanie dodatkowych plików nagłówkowych

Aplikacja utworzona przez AppWizard zawiera tylko dwa pliki nagłówkowe: ZASÓB. H i AFXRES. H. Tylko zasoby. H jest specyficzna dla aplikacji. Może być konieczne uwzględnienie dodatkowych plików nagłówkowych tylko do odczytu w następujących przypadkach:

Plik nagłówkowy jest dostarczany z zewnętrznego źródła lub chcesz współdzielić plik nagłówkowy między wieloma projektami lub wieloma częściami tego samego projektu.

Plik nagłówkowy ma formatowanie i komentarze, które chcesz Visual C++ zmienił lub odfiltrował podczas zapisywania pliku. Na przykład, być może chcesz zachować #define używające arytmetyki symbolicznej takich jak:

```
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

Można uwzględnić dodatkowych plików nagłówkowych tylko do odczytu za pomocą **zasób zawiera** polecenie, aby określić # instrukcję include jako drugą dyrektywę symboli tylko do odczytu, jak w programie:

```
#include "afxres.h"
#include "second.h"
```

Nowy diagram relacji pliku wygląda teraz następująco:

```
    AFXRES.H
RESOURCE.H     SECOND.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    AFXRES.RC
    AFXPRINT.RC
```

**Udostępnianie pliku nagłówkowego przez dwa. RC — pliki**

Możesz chcieć współdzielić plik nagłówkowy między dwoma. RC — pliki znajdujące się w różnych projektach, lub ewentualnie tego samego projektu. Aby to zrobić, wystarczy zastosować technikę dyrektyw tylko opisane powyżej do obu. RC — pliki. W przypadku, gdy dwa. RC — pliki są do różnych aplikacji (różnych projektów), wynik jest zilustrowany na poniższym diagramie:

```
    RESOURCE.H AFXRES.H   RESOURCE.H
(for MYAPP1) SECOND.H   (for MYAPP2)
\       /     \       /
\     /       \     /
    MYAPP1.RC MYAPP2.RC */    \        /     \ */      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
    AFXPRINT.RC
```

Sytuacja, w którym drugi plik nagłówkowy jest współdzielony przez dwa. RC — pliki w tej samej aplikacji (projekt), omówiono poniżej.

**Korzystanie z wielu plików zasobów, w tym samym projekcie**

Visual C++ i kompilator zasobów obsługują wiele. RC — pliki w tym samym projekcie za pośrednictwem #include przez jednego. Plik RC w innym. Wielokrotne zagnieżdżanie jest dozwolone. Istnieją różne powody, aby podzielić zasoby projektu na wiele. RC — pliki:

- Łatwiej zarządzać dużą liczbą zasobów między wieloma członkami zespołu projektu, jeśli podzieli się zasoby na wiele. RC — pliki. Jeśli używasz pakietu zarządzania kontrolą źródła do wyewidencjonowywania plików i ewidencjonowania zmian, dzielenie zasobów na wielu. RC — pliki zapewniają bardziej precyzyjną kontrolę nad zarządzaniem zmianami w zasobach.

- Jeśli chcesz użyć dyrektyw preprocesora, takich jak #ifdef, #endif i #define, dla części zasobów, musisz odizolować je w zasobach tylko do odczytu, które zostaną skompilowane przez kompilator zasobów.

- Składnik. RC — pliki będzie załadować i zapisywane szybciej w programie Visual C++ niż jeden złożony. Plik RC.

- Jeśli chcesz obsługiwać zasób za pomocą edytora tekstów w czytelnej formie, powinieneś go utrzymywać. Plik RC oddzielnie od jednego edycje Visual C++.

- Jeśli trzeba utrzymywać zasób zdefiniowany przez użytkownika w postaci binarnej lub tekstowej, interpretowanej przez inny wyspecjalizowany Edytor danych, następnie należy go przechowywać w osobnym. Plik RC, Visual C++ nie zmienił jego formatu na dane szesnastkowe. . Zasoby plików WAV (dźwięk) w próbce zaawansowanych koncepcji MFC [SPEAKN](../overview/visual-cpp-samples.md) są dobrym przykładem.

Możesz #include sekundy. RC w dyrektywach czasu kompilacji w oknie dialogowym Zestaw zawiera:

```
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

Wynik jest zilustrowany na poniższym diagramie:

```
RESOURCE.H     AFXRES.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    SECOND.RC
    AFXRES.RC
    AFXPRINT.RC
```

Za pomocą dyrektywy czasu kompilacji, możesz organizować zasoby Visual C++ edytowalne i nieedytowalne w wielu. RC — pliki, których MYAPP "główną". RC nic nie robi, ale #include inne. RC — pliki. Jeśli używasz projektu Visual C++. Plik klucza MAK, a następnie użytkownik powinien zawierać gałęzią "główną". RC plik w projekcie tak że wszystkie # wszytkie zasoby są kompilowane z aplikacją.

**Wymuszanie nieedytowalnych plików Visual C++**

Utworzona przez AppWizard RES\MYAPP. Plik RC2 to przykład pliku, który zawiera zasoby, które można wykonać *nie* chcesz wczytać przypadkowo do Visual C++, a następnie zapisać go z powrotem, tracąc informacje o formatowaniu. Aby zabezpieczyć się przed tym, umieść następujące wiersze na początku RES\MYAPP. Plik RC2:

```
#ifdef APSTUDIO_INVOKED
#error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Kiedy Visual C++ kompiluje. Plik RC definiuje `APSTUDIO_INVOKED` także `RC_INVOKED`. Jeśli struktura pliku utworzona przez AppWizard jest uszkodzona i Visual C++ odczytuje wiersz #error znajdujący się wyżej, zgłasza błąd krytyczny i przerywa czytanie. Plik RC.

**Zarządzanie symbolami Współdzielonymi przez wiele Visual C++, edytować. RC — pliki**

Kiedy podzielisz swoje zasoby na wiele, wystąpią dwa problemy. RC — pliki, które chcesz edytować oddzielnie w programie Visual C++:

- Można udostępniać te same symbole w wielu. RC — pliki.

- Musisz pomóc Visual C++ unikać przypisywania tych samych wartości numerycznych ID różnych zasobom (symbolom).

Poniższy diagram ilustruje organizację. RC i. H pliki, które zajmuje za pierwszą kwestię:

```
    MYAPP.RC */         \ */           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
\    /    /      \   \    \
\  /    /        \   \    \
    MYSTRS.RC MYMENUS.RC
```

W tym przykładzie zasoby ciągów są przechowywane w jednym pliku zasobów, MYSTRS. RC i menu są przechowywane w innym, MYMENUS. RC. Niektóre symbole, takie jak w przypadku poleceń, trzeba być współużytkowane przez dwa pliki. Na przykład ID_TOOLS_SPELL może być Identyfikatorem polecenia menu dla elementu sprawdzanie pisowni w menu Narzędzia. a może to być również identyfikator ciągu wiersza poleceń wyświetlany przez platformę, na pasku stanu głównego okna aplikacji.

ID_TOOLS_SPELL symbol jest przechowywany w pliku nagłówkowym udostępnionego, MYSHARED. H. To Ty masz ten współdzielony plik nagłówkowy ręcznie za pomocą edytora tekstów; Visual C++ nie edytuje go bezpośrednio. W zasobie dwa pliki MYSTRS. RC i MYMENUS. Określ RC, #include MYSHARED. H w dyrektywach tylko do odczytu dla MYAPP. RC, za pomocą **zasób zawiera** polecenia zgodnie z wcześniejszym opisem.

Najwygodniej przewidzieć symbol, będziesz udostępniać przed próbą użycia jej do identyfikacji jakiegoś zasobu. Dodaj symbol do udostępnionego pliku nagłówka i, jeśli jeszcze tego nie zrobiono # dyrektywy #include z udostępnionym plikiem nagłówkowym w dyrektywach tylko do odczytu dla. RC plików, Uczyń to przed używaniem symbolu. Jeśli nie przewidujesz współdzielenia symbolu w ten sposób, a następnie trzeba będzie ręcznie (przy użyciu edytora tekstów) przenieść #define instrukcji dla symbolu z np MYMENUS. H-MYSHARED. Godz. przed użyciem go w MYSTRS. RC.

Kiedy zarządzasz symbolami w wielu. RC — pliki, musisz również pomóc Visual C++ unikać przypisywania tych samych wartości numerycznych ID różnych zasobom (symbolom). Dla każdego, biorąc pod uwagę. Plik RC, Visual C++ przyrostowo przypisuje identyfikatory w każdej z czterech domen identyfikatorów. Między edycji sesje, Visual C++ przechowuje informacje o ostatni identyfikator, który przypisał w każdej domeny w pliku nagłówkowym symboli dla. Plik RC. Oto, co to są wartości APS_NEXT dla pustego (nowego). Plik RC:

```
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` jest następną wartością symboliczną, która będzie służyć do zasobu okna dialogowego, zasobu menu i tak dalej. Prawidłowy zakres dla wartości symboli zasobu to 1 do 0x6FFF.

`_APS_NEXT_COMMAND_VALUE` jest następną wartością symboliczną, która będzie służyć do identyfikacji polecenia. Prawidłowy zakres dla wartości symboli polecenia to 0x8000 do 0xDFFF.

`_APS_NEXT_CONTROL_VALUE` jest następną wartością symboliczną, która będzie służyć do sterowania oknem dialogowym. Prawidłowy zakres dla wartości symboli formantu dialogu to 8 do 0xDFFF.

`_APS_NEXT_SYMED_VALUE` jest następną wartością symboliczną, która zostanie wydana po ręcznym przypisaniu wartości symboliczną za pomocą nowego polecenia w przeglądarce symboli.

Visual C++ rozpoczyna z nieco wyższymi wartościami niż najniższa dopuszczalna wartość podczas tworzenia nowego. Plik RC. Kreator AppWizard również zainicjuje te wartości na coś bardziej odpowiedniego dla aplikacji MFC. Aby uzyskać więcej informacji dotyczących zakresów wartości Identyfikatora, zobacz [Uwagi techniczne 20](../mfc/tn020-id-naming-and-numbering-conventions.md).

Po każdorazowym utworzeniu nowego pliku zasobu, nawet w tym samym projekcie Visual C++ definiuje takie same `_APS_NEXT_` wartości. Oznacza to, że jeśli dodasz, powiedz, wiele okien dialogowych na w dwóch różnych. RC — pliki, istnieje duże prawdopodobieństwo, że takie same #define do różnych okien dialogowych zostanie przypisana wartość. Na przykład, IDD_MY_DLG1 w pierwszym. Plik RC mogą mieć przypisany taki sam numer, 101, jak IDD_MY_DLG2 w ciągu sekundy. Plik RC.

Aby tego uniknąć, należy zarezerwować oddzielny zakres numeryczny dla każdej z czterech domen identyfikatorów we właściwej. RC — pliki. W tym celu ręczne aktualizowanie `_APS_NEXT` wartości we wszystkich. RC — pliki **przed** rozpoczniesz Dodawanie zasobów. Na przykład jeśli pierwszy. Plik RC używa domyślnego `_APS_NEXT` wartości, a następnie można przypisać następujące `_APS_NEXT` wartości do drugiego. Plik RC:

```
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

Oczywiście jest nadal możliwe, że Visual C++ przypisze tak wiele identyfikatorów w pierwszym. Plik RC wartości numeryczne zaczną się pokrywać dla drugiego. Plik RC. Należy zarezerwować dostatecznie duże zakresy, dzięki czemu nie jest to realizowane.

**Zarządzanie zależnościami między. WERSJI RC. CPP, i. Pliki H**

Kiedy Visual C++ zapisuje. Plik RC zapisuje również zmiany symboli do odpowiednich zasobów. Plik H. Jedną z sieci. Plikach CPP, które odwołują się do zasobów. Plik RC musi # include. Plik H, zazwyczaj z poziomu projektu głównego pliku nagłówkowego. Prowadzi to do niepożądanych skutków ubocznych ze względu na zarządzanie projektami wewnętrznego środowisko programistyczne, które skanuje pliki źródłowe dla nagłówka zależności. Za każdym razem, gdy dodasz nowy symbol w programie Visual C++, wszystkie. Plik CPP #include. H musi być ponownie kompilowane.

Visual C++ obchodzi zależność od ZASOBU. H przez dołączenie poniższego komentarza jako pierwszy wiersz ZASOBU. Plik H:

```
//{{NO_DEPENDENCIES}}
```

Środowisko programistyczne interpretuje ten komentarz, ignorując zmiany w ZASOBIE. Godz. Dlatego zależne. Plikach CPP nie trzeba ponownie skompilowana.

Wizualne C++ zawsze dodaje //{{NO_DEPENDENCIES}} komentarz wiersz. Plik RC podczas zapisywania pliku. W niektórych przypadkach obejście zależności kompilacji dla ZASOBU. H może prowadzić do błędów czasu wykonywania niewykrytych w czasie. Na przykład, jeśli używasz przeglądarki symboli można zmienić wartości numerycznej przypisanej do symbolu dla zasobu, zasób będzie nie być poprawnie znaleziono i ładowany w przypadku czasu wykonywania aplikacji. Plik CPP odwołujące się do zasobu nie jest ponownie kompilowana. W takich przypadkach należy jawnie zrekompilować żadnego. Plikach CPP, które mają wpływ zmiany symboli w ZASOBACH. H lub wybierz **Kompiluj wszystko ponownie**. Jeśli potrzebujesz często zmieniać wartości symboli dla określonej grupy zasobów, prawdopodobnie znajdziesz go bardziej wygodne i bezpieczniejsze umożliwiające rozbicie tych symboli w pliku oddzielne nagłówkowych tylko do odczytu, zgodnie z opisem w powyższej sekcji [łącznie Dodatkowych plików nagłówkowych](#_mfcnotes_tn035_including).

## <a name="_mfcnotes_tn035_set_includes"></a> Jak Visual C++ zarządza zestaw zawiera informacje o **

Jak wspomniano powyżej, polecenie zestaw zawiera menu Plik pozwala określić trzy typy informacji:

- Plik nagłówkowy symboli

- Dyrektywy symboli tylko do odczytu

- Dyrektywy czasu kompilacji

Poniżej opisano, jak Visual C++ przechowuje te informacje w. Plik RC. Nie potrzebujesz tych informacji, aby używać Visual C++, ale może pomóc lepiej zrozumieć, więc, że aby bardziej optymalnie korzystać z funkcji zestaw zawiera.

Każdy z trzech powyższych rodzajów informacji zestaw zawiera są przechowywane w. Plik RC w dwóch formach: (1) jako #include lub inne dyrektywy interpretowane przez kompilator zasobów i (2) jako specjalne zasoby TEXTINCLUDE interpretowane interpretowanej tylko przez Visual C++.

Zasób TEXTINCLUDE ma na celu bezpiecznego przechowywania informacji o w formularzu, który jest łatwo zawartości w programie Visual C++ **zestaw zawiera** okno dialogowe. TEXTINCLUDE to *typ zasobu* zdefiniowany przez Visual C++. Visual C++ rozpoznaje trzy określone zasoby TEXTINCLUDE, które mają numery identyfikacyjne 1, 2 i 3 zasobu:

|Identyfikator zasobu TEXTINCLUDE|Rodzaj informacji zestaw zawiera|
|-----------------------------|--------------------------------------|
|1|Plik nagłówkowy symboli|
|2|Dyrektywy symboli tylko do odczytu|
|3|Dyrektywy czasu kompilacji|

Każdy z trzech rodzajów informacji zestaw zawiera jest zilustrowany przez domyślne MYAPP. RC i zasobów. Pliki H utworzone przez AppWizard, zgodnie z poniższym opisem. Dodatkowe \0 i "" tokenów pomiędzy blokami BEGIN i END są wymagane przez składnię RC do określania ciągów zakończonych wartością zerową i znaku podwójnego cudzysłowu, odpowiednio.

## <a name="symbol-header-file"></a>Plik nagłówkowy symboli

Formularz informacji pliku nagłówkowym symboli interpretowana przez kompilator zasobów jest po prostu # instrukcję include:

```
#include "resource.h"
```

Odpowiedni zasób TEXTINCLUDE to:

```
1 TEXTINCLUDE DISCARDABLE
BEGIN
"resource.h\0"
END
```

## <a name="read-only-symbol-directives"></a>Dyrektywy symboli tylko do odczytu

Dyrektywy symboli tylko do odczytu są uwzględniane w górnej części MYAPP. RC w następującej formie interpretowanej przez kompilator zasobów:

```
#include "afxres.h"
```

Odpowiedni zasób TEXTINCLUDE to:

```
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

## <a name="compile-time-directives"></a>Dyrektywy czasu kompilacji

Dyrektywy czasu kompilacji są umieszczane na końcu MYAPP. RC w następującej formie interpretowanej przez kompilator zasobów:

```
#ifndef APSTUDIO_INVOKED
///////////////////////
//
// From TEXTINCLUDE 3
//
#include "res\myapp.rc2"  // non-Visual C++ edited resources

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
#endif  // not APSTUDIO_INVOKED
```

Dyrektywa #ifndef APSTUDIO_INVOKED nakazuje Visual C++ pominąć dyrektywy czasu kompilacji.

Odpowiedni zasób TEXTINCLUDE to:

```
3 TEXTINCLUDE DISCARDABLE
BEGIN
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"
"\r\n"
"#include ""afxres.rc""  // Standard components\r\n"
"#include ""afxprint.rc""  // printing/print preview resources\r\n"
"\0"
END
```

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
