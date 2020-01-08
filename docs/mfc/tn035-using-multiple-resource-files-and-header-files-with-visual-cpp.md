---
title: 'TN035: używanie wielu plików zasobów i plików nagłówków z programem Visual C++'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 23d4fdeb82ed7eea97a104e111cd022a87626df4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302175"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: używanie wielu plików zasobów i plików nagłówków z programem Visual C++

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

Ta Uwaga opisuje, jak edytor C++ zasobów wizualnych obsługuje wiele plików zasobów i plików nagłówkowych udostępnianych w pojedynczym projekcie lub udostępnianych w wielu projektach oraz jak można korzystać z tej pomocy. Ta uwaga odpowiada na następujące pytania:

- Kiedy warto podzielić projekt na wiele plików zasobów i/lub plików nagłówkowych oraz jak to zrobić

- Jak udostępnić wspólny nagłówek. Plik H między dwoma. RC — pliki

- Jak podzielić Zasoby projektu na wiele. RC — pliki

- Jak ty (i narzędzia) Zarządzaj zależnościami kompilacji między. RC,. CPP i. Pliki H

Należy pamiętać, że po dodaniu dodatkowego pliku zasobów do projektu ClassWizard nie rozpoznaje zasobów w dodanym pliku.

Ta uwaga ma na celu udzielenie odpowiedzi na powyższe pytania w następujący sposób:

- **Omówienie sposobu, w C++ jaki program Visual zarządza plikami zasobów i plikami nagłówkowymi** zawiera omówienie sposobu, w jaki zestaw zasobów C++ zawiera polecenie w wizualizacji, umożliwia używanie wielu plików zasobów i plików nagłówkowych w tym samym projekcie.

- **Analiza AppWizard — utworzona. RC i. H pliki** przeszukują wiele plików zasobów i nagłówków, które są używane przez aplikację utworzoną przez AppWizard. Te pliki służą jako dobry model dla dodatkowych plików zasobów i plików nagłówkowych, które można dodać do projektu.

- **Dołączenie dodatkowych plików nagłówkowych** opisuje, gdzie można uwzględnić wiele plików nagłówkowych i zawiera szczegółowe informacje, jak to zrobić.

- **Udostępnianie pliku nagłówka między dwoma. Pliki RC** pokazują, jak można udostępnić jeden plik nagłówkowy między wieloma. RC pliki w różnych projektach lub prawdopodobnie w tym samym projekcie.

- **Użycie wielu plików zasobów w tym samym projekcie** opisuje, gdzie można podzielić projekt na wiele. RC i zawiera szczegółowe informacje, jak to zrobić.

- **Wymuszanie nieedytowalnych C++ plików wizualnych** opisuje, jak można się C++ upewnić, że Wizualizacja nie edytuje i przypadkowo ponownie sformatuje zasób niestandardowy.

- **Zarządzanie symbolami udostępnionymi przez C++wiele edytowanych wizualizacji. Pliki RC** opisują sposób udostępniania tych samych symboli w wielu. RC i jak unikać przypisywania zduplikowanych wartości liczbowych ID.

- **Zarządzanie zależnościami między. RC,. CPP i. H pliki** opisuje, jak C++ wizualnie unika niepotrzebne ponowne kompilowanie. Pliki CPP, które są zależne od plików symboli zasobów.

- **Sposób, C++ w jaki wizualne zarządzanie zestawem zawiera informacje** , zawiera C++ szczegółowe informacje techniczne na temat sposobu, w jaki Wizualizacja śledzi wiele (zagnieżdżone). Pliki RC i wiele plików nagłówkowych, które są #include pozostały przez. Plik RC.

## <a name="overview-of-how-visual-c-manages-resource-files-and-header-files"></a>Omówienie sposobu, w C++ jaki Wizualizacja zarządza plikami zasobów i plikami nagłówkowymi

Wizualizacja C++ zarządza pojedynczym. Plik zasobów RC i odpowiadający mu. H plik nagłówkowy jako ściśle sprzężoną parę plików. Podczas edytowania i zapisywania zasobów w programie. Plik RC, można pośrednio edytować i zapisywać symbole w odpowiednich. Plik H. Chociaż można otwierać i edytować wiele. RC — pliki w danym momencie (przy C++użyciu interfejsu użytkownika MDI wizualizacji) dla każdego z nich. Plik RC można pośrednio edytować dokładnie jeden odpowiedni plik nagłówkowy.

### <a name="symbol-header-file"></a>Plik nagłówka symboli

Domyślnie Wizualizacja C++ zawsze nazywa odpowiedni zasób pliku nagłówkowego. H, niezależnie od nazwy pliku zasobów (np. MOJAAPL. RC). Za pomocą polecenia **zasób zawiera** z menu **Widok** w wizualizacji C++, można zmienić nazwę tego pliku nagłówka, aktualizując plik nagłówka symboli w oknie dialogowym **zestaw zawiera** .

### <a name="read-only-symbol-directives"></a>Dyrektywy symboli tylko do odczytu

Chociaż Wizualizacja C++ tylko edytuje jeden plik nagłówkowy dla danego elementu. Plik RC, Wizualizacja C++ obsługuje odwołania do symboli zdefiniowanych w dodatkowych plikach nagłówkowych tylko do odczytu. Za pomocą polecenia **zasób zawiera** z menu **Widok** w wizualizacji C++, można określić dowolną liczbę dodatkowych plików nagłówkowych tylko do odczytu jako dyrektywy symboli tylko do odczytu. Ograniczenie "tylko do odczytu" oznacza, że po dodaniu nowego zasobu w. Plik RC, można użyć symbolu zdefiniowanego w pliku nagłówkowym tylko do odczytu; Jeśli jednak usuniesz zasób, symbol nadal pozostaje zdefiniowany w pliku nagłówkowym tylko do odczytu. Nie można zmienić wartości numerycznej przypisanej do symbolu tylko do odczytu.

### <a name="compile-time-directives"></a>Dyrektywy czasu kompilacji

Wizualizacja C++ obsługuje również zagnieżdżanie plików zasobów, z których jeden. Plik RC jest #include w innym. Podczas edytowania danego elementu. Plik RC z użyciem C++wizualizacji, wszystkie zasoby w #include pliki nie są widoczne. Ale podczas kompilowania. Plik RC, #include pliki. Za pomocą polecenia **zasób zawiera** z menu **Widok** w wizualizacji C++możesz określić dowolną liczbę #include. RC pliki jako dyrektywy czasu kompilacji.

Zwróć uwagę na to, co się dzieje C++ , jeśli przeczytasz do wizualizacji. Plik RC, który #include inny. Plik RC, który *nie* jest określony jako dyrektywa czasu kompilacji. Ta sytuacja może wystąpić, gdy przejdziesz C++ do wizualizacji. Plik RC, który był wcześniej konserwowany ręcznie przy użyciu edytora tekstu. Gdy Wizualizacja C++ odczytuje #include. Plik RC Scala #include zasobów do elementu nadrzędnego. Plik RC. Po zapisaniu elementu nadrzędnego. Plik RC, Instrukcja #include, w efekcie, zostanie zastąpiony przez #include zasoby. Jeśli nie chcesz, aby scalanie było wykonywane, Usuń instrukcję #include z elementu nadrzędnego. Plik RC *przed* przeczytaniem go do C++wizualizacji; następnie używając wizualizacji C++, Dodaj tę samą instrukcję #include jako dyrektywę czasu kompilowania.

Wizualizacja C++ jest zapisywana. Plik RC trzy rodzaje powyższego zestawu obejmują informacje (plik nagłówka symboli, dyrektywy symboli tylko do odczytu i dyrektywy czasu kompilacji) w dyrektywach #include *i* w zasobach TEXTINCLUDE. Zasoby TEXTINCLUDE, szczegóły implementacji, które nie są zwykle potrzebne do obsłużenia, są wyjaśnione w [sposób, C++ w jaki program Visual zarządza zestaw zawiera informacje](#_mfcnotes_tn035_set_includes).

## <a name="analysis-of-appwizard-created-rc-and-h-files"></a>Analiza AppWizard — utworzona. RC i. Pliki H

Badanie kodu aplikacji utworzonego przez AppWizard zapewnia wgląd w sposób, w jaki Wizualizacja C++ zarządza wieloma plikami zasobów i plikami nagłówkowymi. Fragmenty kodu zbadane poniżej pochodzą z aplikacji MOJAAPL utworzonej przez AppWizard przy użyciu opcji domyślnych.

Aplikacja utworzona przez AppWizard używa wielu plików zasobów i wielu plików nagłówkowych, jak przedstawiono na poniższym diagramie:

```Diagram
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

Te relacje wielu plików można wyświetlić za pomocą polecenia Visual C++ File/Set include.

MojaApl. Zwrot
Plik zasobów aplikacji, który można edytować za pomocą C++programu Visual.

Zasoby. H to plik nagłówka specyficzny dla aplikacji. Zawsze ma nazwę zasób. H przez AppWizard spójna z C++domyślnym nazewnictwem pliku nagłówkowego. #Include dla tego pliku nagłówkowego jest pierwszą instrukcją w pliku zasobów (MOJAAPL. RC):

```rc
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. Wersji
Zawiera zasoby, które nie będą edytowane przez wizualizację C++ , ale zostaną uwzględnione w końcowej kompilacji. Plik EXE. AppWizard domyślnie nie tworzy takich zasobów, ponieważ Wizualizacja C++ może edytować wszystkie zasoby standardowe, w tym zasób wersji (nową funkcję w tej wersji). Pusty plik jest generowany przez AppWizard w przypadku dodania własnych niestandardowych zasobów sformatowanych do tego pliku.

Jeśli używasz niestandardowych zasobów sformatowanych, możesz dodać je do RES\MYAPP. RC2 i edytuj je przy użyciu edytora C++ tekstu wizualnego.

Plik AFXRES. RC i AFXPRINT. RC zawiera zasoby standardowe wymagane przez niektóre funkcje platformy. Like RES\MYAPP. RC2 te dwa pliki zasobów udostępniane przez platformę są #include do końca MOJAAPL. RC i są one określone w dyrektywach czasu kompilacji w oknie dialogowym Zestaw zawiera. W ten sposób nie można bezpośrednio wyświetlać ani edytować tych zasobów platformy podczas edytowania programu MOJAAPL. RC w wizualizacji C++, ale są one kompilowane do pliku binarnego aplikacji. Plik RES i ostatni. Plik EXE. Aby uzyskać więcej informacji na temat standardowych zasobów platformy, w tym procedur ich modyfikacji, zobacz [Uwagi techniczne 23](../mfc/tn023-standard-mfc-resources.md).

Plik AFXRES. H definiuje standardowe symbole, takie jak `ID_FILE_NEW`, używane przez platformę i używane w plik AFXRES. Zwrot. Plik AFXRES. H również #include WINREs. H, która zawiera Podzestaw systemu WINDOWS. H, które są niezbędne przez wygenerowaną wizualizację C++ . RC, a także plik AFXRES. Zwrot. Symbole zdefiniowane w plik AFXRES. H są dostępne podczas edytowania pliku zasobów aplikacji (MOJAAPL. RC). Na przykład `ID_FILE_NEW` jest używany dla elementu menu nowy plik w programie MOJAAPL. Zasób menu RC. Nie można zmienić ani usunąć tych symboli zdefiniowanych przez strukturę.

## <a name="_mfcnotes_tn035_including"></a>Dołączanie dodatkowych plików nagłówkowych

Aplikacja utworzona AppWizard zawiera tylko dwa pliki nagłówkowe: RESOURCE. H i plik AFXRES. C. Tylko zasób. H to specyficzne dla aplikacji. Może być konieczne dołączenie dodatkowych plików nagłówkowych tylko do odczytu w następujących przypadkach:

Plik nagłówkowy jest dostarczany przez zewnętrzne źródło lub chcesz udostępnić plik nagłówkowy między wieloma projektami lub wieloma częściami tego samego projektu.

Plik nagłówkowy ma formatowanie i komentarze, które nie powinny być zmieniane ani odfiltrowane przez wizualizację C++ podczas zapisywania pliku. Na przykład może być konieczne zachowanie #define, która używa symbolicznej arytmetycznej, takiej jak:

```h
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

Możesz dołączyć dodatkowe pliki nagłówkowe tylko do odczytu za pomocą polecenia **zasób zawiera** , aby określić instrukcję #include jako drugą dyrektywę symboli tylko do odczytu, jak w:

```rc
#include "afxres.h"
#include "second.h"
```

Nowy Diagram relacji plików wygląda teraz następująco:

```Diagram
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

## <a name="sharing-a-header-file-between-two-rc-files"></a>Udostępnianie pliku nagłówka między dwoma. RC — pliki

Możesz chcieć udostępnić plik nagłówka między dwoma. RC pliki, które znajdują się w różnych projektach, lub prawdopodobnie w tym samym projekcie. W tym celu wystarczy zastosować technikę dyrektyw tylko do odczytu opisaną powyżej do obu. RC — pliki. W przypadku, gdy te dwa. Pliki RC są dla różnych aplikacji (różne projekty), wyniki są zilustrowane na poniższym diagramie:

```Diagram
     RESOURCE.H   AFXRES.H   RESOURCE.H  
    (for MYAPP1)  SECOND.H   (for MYAPP2)
          \       /     \       /
           \     /       \     /
          MYAPP1.RC      MYAPP2.RC
           /    \        /     \
          /      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
                AFXPRINT.RC
```

Przypadek, w którym drugi plik nagłówkowy jest współużytkowany przez dwa. Pliki RC w tej samej aplikacji (projekt) zostały omówione poniżej.

## <a name="using-multiple-resource-files-in-the-same-project"></a>Używanie wielu plików zasobów w tym samym projekcie

Wizualizacja C++ i kompilator zasobów obsługują wiele. RC pliki w tym samym projekcie za pomocą #include jednego z nich. Plik RC w innym. Dozwolone jest wielokrotne zagnieżdżanie. Istnieją różne przyczyny podzielenia zasobów projektu na wiele. RC — pliki:

- Łatwiejsze jest zarządzanie dużą liczbą zasobów wśród wielu członków zespołu projektu, jeśli zasoby zostaną podzielone na wiele. RC — pliki. Jeśli używasz pakietu zarządzania kontrolą źródła do wyewidencjonowywania plików i ewidencjonowania zmian, Podziel zasoby na wiele. Pliki RC zapewniają dokładniejszą kontrolę nad zarządzaniem zmianami zasobów.

- Jeśli chcesz użyć dyrektyw preprocesora, takich jak #ifdef, #endif i #define, w przypadku części zasobów należy je odizolować w zasobach tylko do odczytu, które będą kompilowane przez kompilator zasobów.

- Składnika. Pliki RC będą ładowane i zapisywane szybciej w wizualizacji C++ niż jeden kompozyt. Plik RC.

- Jeśli chcesz zachować zasób z edytorem tekstu w formularzu czytelnym dla człowieka, należy pozostawić go w. Plik RC jest oddzielony od jednej C++ edycji wizualizacji.

- Jeśli musisz zachować zdefiniowany przez użytkownika zasób w postaci binarnej lub tekstowej, który jest interpretowany przez inny wyspecjalizowany Edytor danych, należy pozostawić go w osobnym. Plik RC, dlatego C++ Wizualizacja nie zmienia formatu na dane szesnastkowe. Polu. W przypadku plików WAV (dźwięk) w zaawansowanej koncepcji MFC przykłady [SPEAKN](../overview/visual-cpp-samples.md) są dobrym przykładem.

Możesz #include sekundę. RC w dyrektywach czasu kompilacji w oknie dialogowym Zestaw zawiera:

```h
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

Wyniki są zilustrowane na poniższym diagramie:

```Diagram
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

Korzystając z dyrektyw czasu kompilowania, można organizować C++edytowalne i nieedytowalne zasoby widoczne na wiele elementów. RC — pliki, w których znajduje się "Master" MOJAAPL. RC nie robi nic, ale #include innych. RC — pliki. Jeśli używasz projektu programu Visual Studio C++ . Plik MAK, należy uwzględnić "Master". Plik RC w projekcie, aby wszystkie #include zasoby były kompilowane z aplikacją.

## <a name="enforcement-of-noneditable-visual-c-files"></a>Wymuszanie nieedytowalnych C++ plików wizualnych

RES\MYAPP. utworzony przez AppWizard Plik RC2 to przykład pliku, który zawiera zasoby, których *nie* chcesz przypadkowo odczytać do wizualizacji C++ , a następnie zapisać go z powrotem z informacjami o formatowaniu. Aby chronić przed tym, umieść następujące wiersze na początku RES\MYAPP. Plik RC2:

```rc2
#ifdef APSTUDIO_INVOKED
    #error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Gdy Wizualizacja C++ kompiluje. Plik RC, definiuje `APSTUDIO_INVOKED` i `RC_INVOKED`. Jeśli struktura plików utworzona przez AppWizard jest uszkodzona, a Wizualizacja C++ jest odczytywana z powyższej linii #error, raport o błędzie krytycznym i przerwanie odczytywania. Plik RC.

## <a name="managing-symbols-shared-by-multiple-visual-c-edited-rc-files"></a>Zarządzanie symbolami udostępnionymi przez C++wiele edytowanych wizualizacji. RC — pliki

Dwa problemy powstają podczas dzielenia zasobów na wiele. Pliki RC, które chcesz edytować oddzielnie w wizualizacji C++:

- Możesz chcieć udostępnić te same symbole dla wielu. RC — pliki.

- Musisz pomóc wizualizacji C++ , aby unikać przypisywania tych samych wartości NUMERYCZNych ID różnym zasobom (symbolom).

Na poniższym diagramie przedstawiono organizację. RC i. H plików, które są związane z pierwszym problemem:

```Diagram
              MYAPP.RC
             /         \
            /           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
     \    /    /      \   \    \
      \  /    /        \   \    \
      MYSTRS.RC         MYMENUS.RC
```

W tym przykładzie zasoby ciągów są przechowywane w jednym pliku zasobów, MYSTRS. RC, a menu są przechowywane w innych MENU. Zwrot. Niektóre symbole, takie jak dla poleceń, mogą wymagać udostępnienia między dwoma plikami. Na przykład ID_TOOLS_SPELL może być IDENTYFIKATORem polecenia menu dla elementu pisownia w menu Narzędzia. może również być IDENTYFIKATORem ciągu wiersza polecenia wyświetlanego przez platformę na pasku stanu głównego okna aplikacji.

Symbol ID_TOOLS_SPELL jest przechowywany w udostępnionym pliku nagłówkowym, współdzielona. C. Ten udostępniony plik nagłówka można zachować ręcznie przy użyciu edytora tekstu. Wizualizacja C++ nie jest bezpośrednio edytowana. W dwóch plikach zasobów MYSTRS. RC i webmenu. RC, należy określić #include. H w dyrektywach tylko do odczytu dla programu MOJAAPL. RC, za pomocą polecenia **zasób zawiera** , zgodnie z wcześniejszym opisem.

Najlepiej jest przewidzieć symbol, który zostanie udostępniony przed podjęciem próby użycia go do zidentyfikowania dowolnego zasobu. Dodaj symbol do udostępnionego pliku nagłówkowego i, jeśli nie został jeszcze #include pliku nagłówkowego, w dyrektywach tylko do odczytu dla. Plik RC, zrób to przed użyciem symbolu. Jeśli nie przewidujesz udostępniania symbolu w ten sposób, musisz ręcznie (przy użyciu edytora tekstów) przenieść instrukcję #define dla symbolu z, powiedzmy. H do współdzielenia. H przed użyciem go w MYSTRS. Zwrot.

W przypadku zarządzania symbolami w wielu. RC, należy również pomóc wizualnie C++ , aby unikać przypisywania tych samych wartości NUMERYCZNych ID różnym zasobom (symbolom). Dla każdego z nich. Plik RC, wizualnie C++ przypisuje identyfikatory w każdej z czterech domen identyfikatorów. Między edytowaniem sesji Wizualizacja C++ śledzi ostatni Identyfikator przypisany w każdej domenie w pliku nagłówkowym symboli dla. Plik RC. Poniżej przedstawiono wartości APS_NEXT dla pustego (nowego). Plik RC:

```rc
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` jest następną wartością symboliczną, która będzie używana dla zasobu okna dialogowego, zasobu menu i tak dalej. Prawidłowy zakres wartości symboli zasobów wynosi od 1 do 0x6FFF.

`_APS_NEXT_COMMAND_VALUE` jest następną wartością symboliczną, która będzie używana do identyfikacji polecenia. Prawidłowy zakres wartości symboli poleceń to 0x8000 do 0xDFFF.

`_APS_NEXT_CONTROL_VALUE` jest następną wartością symboliczną, która będzie używana dla kontrolki okna dialogowego. Prawidłowy zakres dla wartości symboli kontrolki okna dialogowego to 8 do 0xDFFF.

`_APS_NEXT_SYMED_VALUE` jest następną wartością symboliczną, która zostanie wystawiona po ręcznym przypisaniu wartości symbolu przy użyciu nowego polecenia w przeglądarce symboli.

Wizualizacja C++ rozpoczyna się od nieco wyższych wartości, których najniższa wartość prawna podczas tworzenia nowego. Plik RC. AppWizard będzie również inicjować te wartości bardziej odpowiednie dla aplikacji MFC. Aby uzyskać więcej informacji na temat zakresów wartości identyfikatorów, zobacz [Uwaga techniczna 20](../mfc/tn020-id-naming-and-numbering-conventions.md).

Teraz za każdym razem, gdy tworzysz nowy plik zasobów, nawet w tym samym projekcie, C++ Wizualizacja definiuje te same wartości `_APS_NEXT_`. Oznacza to, że w przypadku dodawania, mówiąc, wielu okien dialogowych w dwóch różnych. RC, że ta sama wartość #define zostanie przypisana do różnych okien dialogowych. Na przykład IDD_MY_DLG1 w pierwszej kolejności. Plik RC może mieć przypisaną taką samą liczbę 101, jak IDD_MY_DLG2 w drugim. Plik RC.

Aby tego uniknąć, należy zarezerwować odrębny zakres liczbowy dla każdej z czterech domen identyfikatorów w odpowiednich. RC — pliki. W tym celu należy ręcznie zaktualizować wartości `_APS_NEXT` w każdej z nich. RC pliki **przed** rozpoczęciem dodawania zasobów. Na przykład, jeśli pierwszy. Plik RC używa domyślnych wartości `_APS_NEXT`, następnie można przypisać następujące wartości `_APS_NEXT` do drugiej. Plik RC:

```rc
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

Oczywiście, nadal jest możliwe, że Wizualizacja C++ przypisze wiele identyfikatorów w pierwszej kolejności. RC, że wartości liczbowe zaczynają nakładać się na zarezerwowanych dla drugiej. Plik RC. Należy zarezerwować wystarczająco duże zakresy, aby to nie miało miejsce.

## <a name="managing-dependencies-between-rc-cpp-and-h-files"></a>Zarządzanie zależnościami między. RC,. CPP i. Pliki H

Gdy Visual C++ zapisuje. Plik RC, zapisuje także zmiany symboli w odpowiednim zasobie. Plik H. Dowolna z nich. Pliki CPP odwołujące się do zasobów w programie. Plik RC musi #include zasób. H plik, zazwyczaj z poziomu głównego pliku nagłówkowego projektu. Prowadzi to do niepożądanego efektu ubocznego ze względu na wewnętrzne zarządzanie projektami środowiska programistycznego, które skanuje pliki źródłowe pod kątem zależności nagłówka. Za każdym razem, gdy dodajesz nowy symbol C++w wizualizacji, wszystkie. Pliki CPP, które #include zasób. Należy ponownie skompilować H.

Wizualizacja C++, omija zależność od zasobu. H przez uwzględnienie następującego komentarza jako pierwszego wiersza zasobu. Plik H:

```h
//{{NO_DEPENDENCIES}}
```

Środowisko programistyczne interpretuje ten komentarz poprzez ignorowanie zmian w zasobie. H, tak, aby była zależna. Nie trzeba ponownie kompilować plików CPP.

Element C++ wizualny zawsze dodaje wiersz komentarza//{{NO_DEPENDENCIES}} do elementu. RC plik. W niektórych przypadkach obejście zależności kompilacji względem zasobu. H może prowadzić do błędów czasu wykonywania wykrytych w czasie łącza. Jeśli na przykład użyjesz przeglądarki symboli do zmiany wartości liczbowej przypisanej do symbolu zasobu, zasób nie zostanie prawidłowo znaleziony i załadowany w czasie wykonywania aplikacji, jeśli. Plik CPP odwołujący się do zasobu nie został ponownie skompilowany. W takich przypadkach należy jawnie ponownie skompilować wszystkie. Pliki CPP, na które wiadomo, mają wpływ zmiany symboli w zasobie. H lub wybierz opcję **Kompiluj ponownie wszystko**. Jeśli potrzebujesz często zmieniać wartości symboliczne dla określonej grupy zasobów, prawdopodobnie okaże się, że jest to bardziej wygodne i bezpieczniejsze, aby podzielić te symbole na osobny plik nagłówkowy tylko do odczytu, zgodnie z opisem w powyższej sekcji, w [tym o dodatkowych plikach nagłówkowych](#_mfcnotes_tn035_including).

## <a name="_mfcnotes_tn035_set_includes"></a>Sposób, C++ w jaki program Visual zarządza zestawem zawiera informacje

Jak wspomniano powyżej, zestaw menu plik zawiera polecenie umożliwia określenie trzech typów informacji:

- Plik nagłówka symboli

- Dyrektywy symboli tylko do odczytu

- Dyrektywy czasu kompilacji

Poniżej opisano sposób, w C++ jaki Wizualizacja utrzymuje te informacje w. Plik RC. Te informacje nie są potrzebne do korzystania z wizualizacji C++, ale mogą wzmocnić swoje zrozumienie, aby można było łatwiej korzystać z funkcji Set includes.

Każdy z powyższych trzech typów zestawu zawiera informacje są przechowywane w. Plik RC w dwóch formach: (1) jako #include lub inne dyrektywy interpretowane przez kompilator zasobów oraz (2) jako specjalne Zasoby TEXTINCLUDE interpretowane tylko przez wizualizację C++.

Celem zasobu TEXTINCLUDE jest bezpieczne przechowywanie zestawu informacji o dołączeniu w formularzu, który jest łatwo do przedprezentowania w oknie C++dialogowym **zestaw** elementów w programie Visual. TEXTINCLUDE jest *typem zasobu* zdefiniowanym przez wizualizację C++. Wizualizacja C++ rozpoznaje trzy określone zasoby TEXTINCLUDE, które mają numery identyfikacyjne zasobów 1, 2 i 3:

|Identyfikator zasobu TEXTINCLUDE|Typ zestawu zawiera informacje|
|-----------------------------|--------------------------------------|
|1|Plik nagłówka symboli|
|2|Dyrektywy symboli tylko do odczytu|
|3|Dyrektywy czasu kompilacji|

Każdy z trzech typów zestawu zawiera informacje, które są zilustrowane przez domyślny MOJAAPL. RC i RESOURCE. H plików utworzonych przez AppWizard, zgodnie z poniższym opisem. Tokeny ekstra \ 0 i "" między blokami BEGIN i END są wymagane przez składnię RC, aby określić zero zakończonych ciągów i znak cudzysłowu.

### <a name="symbol-header-file"></a>Plik nagłówka symboli

Forma informacji o pliku nagłówkowym symboli interpretowana przez kompilator zasobów jest po prostu instrukcją #include:

```rc
#include "resource.h"
```

Odpowiedni zasób TEXTINCLUDE to:

```rc
1 TEXTINCLUDE DISCARDABLE
BEGIN
    "resource.h\0"
END
```

### <a name="read-only-symbol-directives"></a>Dyrektywy symboli tylko do odczytu

Dyrektywy symboli tylko do odczytu są zawarte w górnej części MOJAAPL. RC w następującej formie interpretowanej przez kompilator zasobów:

```rc
#include "afxres.h"
```

Odpowiedni zasób TEXTINCLUDE to:

```rc
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

### <a name="compile-time-directives"></a>Dyrektywy czasu kompilacji

Dyrektywy czasu kompilacji są uwzględniane na końcu MOJAAPL. RC w następującej formie interpretowanej przez kompilator zasobów:

```rc
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

Dyrektywa APSTUDIO_INVOKED #ifndef powoduje, że Wizualizacja C++ zostanie pominięta w dyrektywach czasu kompilacji.

Odpowiedni zasób TEXTINCLUDE to:

```rc
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

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)\
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
