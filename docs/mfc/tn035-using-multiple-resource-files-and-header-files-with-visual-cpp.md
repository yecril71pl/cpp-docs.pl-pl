---
title: "TN035: Używanie wielu plików zasobów i plików nagłówków z programem Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.resources
dev_langs: C++
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9c03c642dfc3524f69f4aa8d1a397f750b42db27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: używanie wielu plików zasobów i plików nagłówków z programem Visual C++
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano, jak edytora zasobów języka Visual C++ obsługuje wielu plików zasobów i pliki nagłówkowe udostępnionych w jednej projektu lub współużytkowane przez wiele projektów i jak można korzystać z tej pomocy technicznej. Ta uwaga odpowiedzi na te pytania:  
  
-   Gdy może chcesz podzielić projektu do wielu plików zasobów i/lub pliki nagłówka i jak to zrobić  
  
-   Jak udostępnić wspólnej nagłówka. H pliku między dwiema. RC — pliki  
  
-   Jak można podzielić zasoby projektu na wielu. RC — pliki  
  
-   Jak można (oraz narzędzia) zarządzać kompilacji zależności między. RC. CPP, i. Pliki H  
  
 Należy pamiętać, że po dodaniu pliku dodatkowych zasobów do projektu ClassWizard nie rozpoznaje zasobów w dodany plik.  
  
 Ta uwaga mają strukturę odpowiedzi na te pytania w następujący sposób:  
  
- **Omówienie sposobu Visual C++ zarządza plików zasobów i pliki nagłówkowe** zawiera omówienie sposobu zasób ustawić zawiera polecenie w programie Visual C++ pozwala używać wielu plików zasobów i pliki nagłówkowe, w tym samym projekcie.  
  
- **Analiza utworzone z kreatorami AppWizard. RC i. Pliki H** analizuje wielu plików zasobów i nagłówek, które są używane przez aplikacje utworzone z kreatorami AppWizard. Te pliki służą jako dobry model dodatkowe pliki zasobów i pliki nagłówkowe, które można dodać do projektu.  
  
- **Dodatkowe pliki nagłówka w tym** opisano, gdzie mogą zostać uwzględnione pliki nagłówka i zawiera szczegółowe informacje, jak to zrobić.  
  
- **Udostępnianie pliku nagłówka między dwiema. Pliki RC** pokazuje, jak można współużytkować jeden plik nagłówka między wieloma. RC — pliki w różnych projektów lub w tym samym projekcie.  
  
- **Korzystanie z wielu plików zasobów, w tym samym projekcie** w tym artykule opisano, gdzie można podzielić projektu do wielu. RC pliki i zawiera szczegółowe informacje, jak to zrobić.  
  
- **Wymuszanie nieedytowalne pliki Visual C++** w tym artykule opisano, jak można upewnić się, Visual C++ nie Edytuj i przypadkowo ponownie sformatować zasobów niestandardowych.  
  
- **Zarządzanie symbole współużytkowane przez wiele Visual C++, edytować. Pliki RC** zawiera opis sposobu udostępniania tego samego symbole w kilku. RC — pliki i jak należy unikać przypisywania zduplikowane identyfikatory numeryczne.  
  
- **Zarządzanie zależności między. RC. CPP, i. Pliki H** w tym artykule opisano, jak Visual C++ pozwala uniknąć niepotrzebnego ponownej kompilacji. CPP pliki, które są zależne od zasobów plików symboli.  
  
- **Jak Visual C++ służy do zarządzania obejmuje informacji o zbiorze** szczegółowe informacje techniczne na temat sposobu Visual C++ przechowuje informacje o wielu (zagnieżdżona). RC — pliki i wiele plików nagłówka #include'd przez. Plik RC.  
  
 **Omówienie sposobu Visual c++ zarządza plików zasobów i pliki nagłówkowe**  
  
 Visual C++ zarządza jeden. Plik zasobów RC i odpowiadające mu. Plik nagłówka H jako silnie sprzężonego parę plików. Gdy Edytuj i zapisuj zasobów w. RC plik należy pośrednio Edytuj i zapisuj symboli w odpowiednich. Plik godz. Mimo że można otwierać i edytować wielu. RC — pliki w czasie (przy użyciu interfejsu użytkownika programu Visual C++ MDI) dla żadnej podanej. Plik RC pośrednio Edytuj dokładnie jeden plik nagłówka.  
  
 **Plik nagłówka symbolu**  
  
 Domyślnie program Visual C++ zawsze nazwy odpowiedni plik nagłówka ZASOBU. H, niezależnie od tego, nazwa pliku zasobu (np. MOJA_APLIKACJA. RC). Przy użyciu **zasobów zawiera** polecenie **widoku** menu w programie Visual C++, można zmienić nazwę tego pliku nagłówka, aktualizując plik nagłówka symbolu w **ustawić obejmuje**okno dialogowe.  
  
 **Dyrektywy symboli tylko do odczytu**  
  
 Mimo że Visual C++ edytuje tylko jeden plik nagłówka dla żadnej podanej. Plik RC, Visual C++ obsługuje odwołań do symboli zdefiniowanych w plikach dodatkowe nagłówka tylko do odczytu. Przy użyciu **zasobów zawiera** polecenie **widoku** menu w programie Visual C++, można określić dowolną liczbę dodatkowych nagłówka tylko do odczytu plików jako tylko do odczytu dyrektywy symboli. Ograniczenie "tylko do odczytu" oznacza, że podczas dodawania nowego zasobu w. RC plik, można użyć symbol zdefiniowany w pliku nagłówka tylko do odczytu. Jednak jeśli usuniesz zasób symbol nadal zdefiniowanych w pliku tylko do odczytu nagłówka. Nie można zmienić wartość liczbową przypisane do symbolu tylko do odczytu.  
  
 **Dyrektywy kompilacji**  
  
 Visual C++ obsługuje również zagnieżdżenia pliki zasobów, gdy jedna. RC plik jest #include'd w innym. Podczas edytowania danego. RC plik przy użyciu programu Visual C++, wszystkie zasoby w #include'd pliki nie są widoczne. Jednak podczas kompilacji. RC plik #include'd plików są również skompilowana. Przy użyciu **zasobów zawiera** polecenie **widoku** menu w programie Visual C++, można określić dowolną liczbę #include'd. RC — pliki jako dyrektywy kompilacji.  
  
 Należy pamiętać, co się stanie, jeśli odczytu w programie Visual C++. Plik RC #include innego obiektu. RC plik, który jest *nie* określony jako dyrektywy kompilacji. Tej sytuacji mogą wystąpić po przywróceniu języka Visual c++. RC plik, który można było zostały wcześniej utrzymania ręcznie za pomocą edytora tekstu. Gdy odczytuje Visual C++ #include'd. RC plik scala #include'd zasobów do obiektu nadrzędnego. Plik RC. Po zapisaniu obiektu nadrzędnego. RC plik #include instrukcji, w efekcie, zostaną zastąpione #include'd zasobów. Jeśli nie chcesz, aby scalania to mieć miejsce, należy usunąć #include instrukcji z obiektu nadrzędnego. Plik RC *wcześniejsze* do czytania go do języka Visual C++; przy użyciu programu Visual C++, dodać z powrotem takie same # instrukcji jako kompilacji dyrektywy include.  
  
 Zapisuje Visual C++. Trzy rodzaje powyżej plików RC ustawić zawiera informacje (plik nagłówka symbolu, dyrektywy symboli tylko do odczytu i dyrektywy kompilacji) w # dyrektywy include *i* TEXTINCLUDE zasobów. Zasoby TEXTINCLUDE, szczegółów implementacji, które zwykle zbędna, nie można rozwiązać, opisano szczegółowo w [jak Visual C++ zarządza ustawić zawiera informacje o](#_mfcnotes_tn035_set_includes).  
  
 **Analiza utworzone z kreatorami AppWizard. RC i. Pliki H**  
  
 Badanie kodu aplikacji utworzonej przez kreatorami AppWizard zapewnia wgląd w zarządzaniu Visual C++ na wielu plików zasobów i plików nagłówków. Fragmenty kodu zbadane poniżej są z aplikacji MOJA_APLIKACJA utworzonego przez kreatorami AppWizard przy użyciu opcji domyślnych.  
  
 Aplikacja utworzone z kreatorami AppWizard używa wielu plików zasobów i wiele plików nagłówka, zgodnie z opisem na poniższym diagramie:  
  
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
  
 Można je wyświetlić, wielu plików za pomocą polecenia programu Visual C++ pliku/zestaw zawiera.  
  
 MOJA_APLIKACJA. RC  
 Plik zasobów aplikacji można edytować przy użyciu programu Visual C++.  
  
 ZASÓB. H jest plik nagłówka specyficzne dla aplikacji. Jest zawsze o nazwie zasobów. H przez kreatorami AppWizard zgodne z domyślnego języka Visual C++ nazewnictwa pliku nagłówka. #Include dla tego pliku nagłówka jest pierwszą instrukcją w pliku zasobów (MOJA_APLIKACJA. RC):  
  
```  
//Microsoft Visual C++ generated resource script  
//  
#include "resource.h"  
```  
  
 RES\MYAPP. RC2  
 Zawiera zasoby, które nie będą edytowane przez Visual C++, ale zostaną uwzględnione w ostatecznym skompilowany. Plik EXE. Kreatorami AppWizard tworzy żadnych takich zasobów domyślnie, ponieważ Visual C++ można edytować wszystkie standardowe zasoby, w tym wersja zasobów (Nowa funkcja w tej wersji). Pusty plik jest generowany przez kreatorami AppWizard w przypadku, gdy chcesz dodać własne niestandardowe zasoby sformatowany do tego pliku.  
  
 Jeśli używasz niestandardowych zasobów sformatowane, można dodać je do RES\MYAPP. RC2 i edytować za pomocą edytora tekstu Visual C++.  
  
 AFXRES. RC i AFXPRINT. RC zawiera standardowe zasoby wymagane przez niektóre funkcje platformy. Podobnie jak RES\MYAPP. Są następujące dwa pliki zasobów udostępnionych przez firmę framework RC2, #include'd na końcu MOJA_APLIKACJA. RC i są określone w dyrektywy kompilacji okno dialogowe Ustawianie obejmuje. W związku z tym nie bezpośrednio wyświetlić ani edytować te zasoby, podczas edytowania MOJA_APLIKACJA. RC w programie Visual C++, ale są one kompilowane do pliku binarnego aplikacji. Plików RES i final. Plik EXE. Aby uzyskać więcej informacji na standardowych ramy zasoby, w tym procedur modyfikowania ich, zobacz [23 Uwaga techniczna](../mfc/tn023-standard-mfc-resources.md).  
  
 AFXRES. H definiuje symbole standardowe, takie jak `ID_FILE_NEW`, używane przez platformę i używane wyłącznie w AFXRES. RC. AFXRES. H również #include w WINRES. H, zawierającą podzbiór systemu WINDOWS. H, które są wymagane przez wygenerowany Visual C++. RC — pliki, jak również AFXRES. RC. Symbole zdefiniowane w AFXRES. H są dostępne podczas edytowania pliku zasobu aplikacji (MOJA_APLIKACJA. RC). Na przykład `ID_FILE_NEW` jest używany nowy plik elementu menu w MOJA_APLIKACJA. RC dla zasobów menu. Nie można zmienić ani usunąć te symbole zdefiniowane w ramach.  
  
## <a name="_mfcnotes_tn035_including"></a>W tym pliki nagłówkowe dodatkowe  
  
 Aplikacja utworzone z kreatorami AppWizard zawiera tylko dwa pliki nagłówkowe: zasobów. H i AFXRES. H. Tylko zasób. H jest specyficzne dla aplikacji. Konieczne może zawierać pliki dodatkowych nagłówków tylko do odczytu w następujących przypadkach:  
  
 Plik nagłówka pochodzi od źródła zewnętrznego lub chcesz udostępnić plik nagłówka wśród wielu projektów lub wielu części tego samego projektu.  
  
 Plik nagłówka ma formatowanie i komentarze, że nie ma Visual C++, aby zmienić lub odfiltrować podczas zapisywania pliku. Na przykład może być chcesz zachować #define firmy używające symboliczne arytmetyczne takich jak:  
  
```  
#define RED 0  
#define BLUE 1  
#define GREEN 2  
#define ID_COLOR_BUTTON 1001  
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)  
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)  
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)  
```  
  
 Można podać dodatkowy nagłówek tylko do odczytu plików za pomocą **zasobów zawiera** polecenie, aby określić #include instrukcji jako drugi dyrektywy symboli tylko do odczytu jako:  
  
```  
#include "afxres.h"  
#include "second.h"  
```  
  
 Plik diagramu relacji teraz wygląda następująco:  
  
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
  
 **Udostępnianie pliku nagłówka między dwiema. RC — pliki**  
  
 Warto udostępnić plik nagłówka między dwiema. RC — pliki znajdujących się w różnych projektów lub tego samego projektu. Aby to zrobić, wystarczy zastosować opisano powyżej, aby obie techniki dyrektywy tylko do odczytu. RC — pliki. W przypadku, gdy dwa. RC — pliki są dla różnych aplikacji (różnych projektów), wynik przedstawiono na poniższym diagramie:  
  
```  
    RESOURCE.H AFXRES.H   RESOURCE.H    
 (for MYAPP1) SECOND.H   (for MYAPP2)               
 \       /     \       /             
 \     /       \     /               
    MYAPP1.RC MYAPP2.RC */    \        /     \ */      \      /       \              
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2                
    AFXPRINT.RC 
```  
  
 Sytuacja, w którym drugi plik nagłówka jest udostępniony przez dwa. RC — pliki w tej samej aplikacji (projekt) została szczegółowo opisana poniżej.  
  
 **Korzystanie z wielu plików zasobów, w tym samym projekcie**  
  
 Visual C++ i kompilator zasobów obsługi wielu. RC — pliki w tym samym projekcie za pośrednictwem #include w jeden. RC plik w innym. Dozwolone jest wiele zagnieżdżenia. Istnieją różne przyczyny podziału zasoby projektu do wielu. RC — pliki:  
  
-   To ułatwia zarządzanie dużą liczbę zasobów w wielu członków zespołu projektu, jeśli można podzielić na wiele zasobów. RC — pliki. Jeśli używasz pakietu zarządzania kontroli źródła dla wyewidencjonowanie plików i ewidencjonowanie zmiany, dzielenie zasobów na wielu. RC — pliki zapewniają bardziej precyzyjną kontrolę nad Zarządzanie zmianami do zasobów.  
  
-   Jeśli chcesz użyć dyrektywy preprocesora, takich jak #ifdef, #endif, a #define, dla części zasobów, muszą izolowaniu ich w trybie tylko do odczytu zasobów, które będą zbierane przez kompilator zasobów.  
  
-   Składnik. RC — pliki będą obciążenia i Zapisz szybciej w programie Visual C++, niż jeden złożone. Plik RC.  
  
-   Jeśli chcesz zachować zasobu za pomocą edytora tekstu w postaci zrozumiałą dla użytkownika, należy go przechowywać. Umożliwia edycję plików RC niezależnie od jednego języka Visual C++.  
  
-   Jeśli trzeba utrzymywać zasób zdefiniowane przez użytkownika w postaci pliku binarnego lub tekst jest interpretable przez inny Edytor danych specjalne, następnie należy go przechowywać w oddzielnej. Plik RC, Visual C++ nie zmienia format danych szesnastkową. . Zasoby plików WAV (dźwięk) w próbce pojęcia zaawansowane MFC [SPEAKN](../visual-cpp-samples.md) są dobrym przykładem.  
  
 Możesz #include sekundy. RC w dyrektywach kompilacji w oknie dialogowym Ustaw obejmuje:  
  
```  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
#include "second.rc"  // THE SECOND .RC FILE  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
```  
  
 Na poniższym diagramie przedstawiono wyniki:  
  
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
  
 Przy użyciu dyrektyw kompilacji, możesz organizować zasobami Visual C++ edycji i nie można edytować w wielu. RC — pliki, których MYAPP "master". Nie robi nic, RC, ale #include inne. RC — pliki. Jeśli używasz projektu Visual C++. Plik klucza MAK, a następnie użytkownik powinien zawierać "master". RC plik w projekcie tak że wszystkie #include'd zasoby są kompilowane przy użyciu aplikacji.  
  
 **Wymuszanie plików edytowana Visual C++**  
  
 Utworzony z kreatorami AppWizard RES\MYAPP. Plik RC2 jest przykładowy plik zawierający zasoby, które można wykonać *nie* przypadkowo odczytu w programie Visual C++, a następnie zapisz je Wycofaj z utratę formatowania informacji. Aby zabezpieczyć się przed tym, należy umieścić następujące wiersze na początku RES\MYAPP. Plik RC2:  
  
```  
#ifdef APSTUDIO_INVOKED  
 #error this file is not editable by Visual C++  
#endif //APSTUDIO_INVOKED  
```  
  
 Gdy kompiluje Visual C++. Definiuje RC plik **APSTUDIO_INVOKED** oraz **RC_INVOKED**. Visual C++ odczytuje wiersz #error powyżej struktury plików utworzony z kreatorami AppWizard jest uszkodzony, zgłasza błąd krytyczny i Przerwij Odczyt. Plik RC.  
  
 **Zarządzanie symbole współużytkowane przez wiele Visual C++, edytować. RC — pliki**  
  
 Problemy z dwóch wystąpić, gdy podzielić zasoby do wielu. RC — pliki, które chcesz edytować oddzielnie w programie Visual C++:  
  
-   Warto udostępnić tym samym symbole w wielu. RC — pliki.  
  
-   Należy zapewnić Visual C++, należy unikać przypisywania tej samej wartości liczbowych identyfikator do różnych zasobów (symboli).  
  
 Na poniższym diagramie przedstawiono organizacji. RC i. H pliki, których dotyczy problem pierwszy:  
  
```  
    MYAPP.RC */         \ */           \  
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H  
 \    /    /      \   \    \  
 \  /    /        \   \    \  
    MYSTRS.RC MYMENUS.RC  
```  
  
 W tym przykładzie zasobów ciągu jest przechowywana w pliku jeden zasób, MYSTRS. RC i menu są przechowywane w innym MYMENUS. RC. Niektóre symbole, takie jak polecenia, trzeba być udostępniane między dwoma plikami. Na przykład ID_TOOLS_SPELL może być identyfikator polecenia menu dla elementu pisowni w menu Narzędzia. i może to być również identyfikator ciągu wiersza polecenia, wyświetlane przez platformę, na pasku stanu głównego okna aplikacji.  
  
 ID_TOOLS_SPELL symbol jest przechowywana w pliku nagłówka udostępnionego, MYSHARED. H. Ręcznie Obsługa tego pliku nagłówka udostępnionych za pomocą edytora tekstu; Visual C++ nie bezpośrednio edytować go. W zasobie dwa pliki MYSTRS. RC i MYMENUS. Określ RC, #include MYSHARED. H w dyrektywach tylko do odczytu dla MOJA_APLIKACJA. RC, za pomocą **zasobów zawiera** poleceń, zgodnie z wcześniejszym opisem.  
  
 Dogodnym przewidywania symbol udostępni przed próbą użycia go do identyfikacji dowolnego zasobu. Dodać symbol do pliku nagłówka udostępnionego i, jeśli jeszcze tego nie zrobiono #include'd plik nagłówka udostępnionych w dyrektywy tylko do odczytu. RC plik, należy go przy użyciu symbolu. Jeśli nie jest przewidywane udostępnianie symbol w ten sposób, a następnie trzeba będzie ręcznie (przy użyciu edytora tekstów) Przenieś #define instrukcji dla symbolu z MYMENUS powiedzieć. H do MYSHARED. H przed jego użyciem w MYSTRS. RC.  
  
 Jeśli zarządzasz symbole w wielu. RC — pliki, można również musi pomóc Visual C++, należy unikać przypisywania tej samej wartości liczbowych identyfikator do różnych zasobów (symboli). Dla żadnego danych. Plik RC, Visual C++ przyrostowo przypisuje identyfikatory w każdej z czterech domenach identyfikator. Między sesjach edycji, Visual C++ przechowuje informacje o identyfikator ostatniego ona zarejestrowana w każdej domenie w plik nagłówka symbolu. Plik RC. Oto, co wartości APS_NEXT jest pusta (nowy). Plik RC:  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  101  
#define _APS_NEXT_COMMAND_VALUE   40001  
#define _APS_NEXT_CONTROL_VALUE   1000  
#define _APS_NEXT_SYMED_VALUE     101  
```  
  
 **_APS_NEXT_RESOURCE_VALUE** jest następnej wartości symbol, który będzie służyć do zasobu okna dialogowego, zasobów menu i tak dalej. Prawidłowy zakres dla wartości symbol zasobu jest 0x6FFF do 1.  
  
 **_APS_NEXT_COMMAND_VALUE** jest następnej wartości symbolu, który będzie używany do identyfikacji polecenia. Prawidłowy zakres dla wartości symbolu polecenia jest 0x8000 do 0xDFFF.  
  
 **_APS_NEXT_CONTROL_VALUE** jest następnej wartości symbolu, który będzie używany dla formantu okna dialogowego. Prawidłowy zakres dla wartości symbolu formantu okna dialogowego jest 8 do 0xDFFF.  
  
 **_APS_NEXT_SYMED_VALUE** jest wartość symbolu następnego podczas ręcznie przypisać wartość symbolu, używając nowego polecenia w przeglądarce symbolu.  
  
 Visual C++ rozpoczyna się od znaku nieco większe wartości prawna najniższą wartość, przy tworzeniu nowego. Plik RC. Kreatorami AppWizard zainicjuje także te wartości na bardziej odpowiednią dla aplikacji MFC. Aby uzyskać więcej informacji o zakresach wartość Identyfikatora, wyświetlić [20 Uwaga techniczna](../mfc/tn020-id-naming-and-numbering-conventions.md).  
  
 Po każdym utworzeniu nowego pliku zasobu, nawet w tym samym projekcie Visual C++ definiuje takie same **_APS_NEXT\_**  wartości. Oznacza to, że jeśli dodasz, powiedzieć wielu okien dialogowych programu w dwóch różnych. RC — pliki, istnieje duże prawdopodobieństwo który takie same #define będzie można przypisać wartości do różnych okien dialogowych. Na przykład IDD_MY_DLG1 w pierwszym. Plik RC mogą przypisano tę samą liczbę, 101, jako IDD_MY_DLG2 na sekundę. Plik RC.  
  
 Aby tego uniknąć, należy zarezerwować oddzielne zakresu numerycznego dla każdego z czterech domenach identyfikatorów we właściwej. RC — pliki. W tym celu ręczne aktualizowanie **_APS_NEXT** wartości w każdym. RC — pliki `before` dodawania zasobów. Na przykład jeśli pierwszy. RC plik używa domyślnej **_APS_NEXT** wartości, a następnie można przypisać następujące **_APS_NEXT** wartości przez drugą. Plik RC:  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  2000  
#define _APS_NEXT_COMMAND_VALUE   42000  
#define _APS_NEXT_CONTROL_VALUE   2000  
#define _APS_NEXT_SYMED_VALUE     2000  
```  
  
 Oczywiście jest nadal możliwe, że Visual C++ przypisze tak wiele identyfikatorów w pierwszym. RC plik rozpoczęcia dla drugiego nakładania się wartości liczbowych. Plik RC. Wystarczająco duże zakresy należy zarezerwować tak, aby tak nie jest.  
  
 **Zarządzanie zależności między. RC. CPP, i. Pliki H**  
  
 Gdy zapisuje Visual C++. RC plik również zapisuje zmiany symbol do odpowiednich zasobów. Plik godz. Jedną z sieci. CPP pliki, które odwołują się do zasobów. Plik RC może # include. Plik H, zazwyczaj z poziomu projektu głównego nagłówka pliku. Prowadzi to do niepożądanych efekt uboczny z powodu Zarządzanie projektami wewnętrzny środowiska programowania, które skanuje pliki źródłowe dla nagłówka zależności. Za każdym razem Dodaj nowy symbol w programie Visual C++, wszystkie. Pliku CPP #include. H musi być ponownie kompilowane.  
  
 Visual C++ prowadzenia zależność od ZASOBU. H, umieszczając w niej Poniższy komentarz w pierwszym wierszu zasobu. Plik H:  
  
```  
//{{NO_DEPENDENCIES}}  
```  
  
 Środowisko projektowe interpretuje ten komentarz, ignorując zmiany do ZASOBU. H tak zależne. Plikach CPP nie trzeba ponownie skompilowana.  
  
 Visual C++ zawsze dodaje //{{NO_DEPENDENCIES}} komentarz wiersz. Plik RC podczas zapisywania pliku. W niektórych przypadkach obejścia zależności kompilacji dla ZASOBU. H może prowadzić do błędów czasu wykonywania wykryte w czasie łącza. Na przykład, jeśli używasz przeglądarki Symbol Aby zmienić wartość liczbową przypisane do symbolu dla zasobu, zasób zostanie nie poprawnie znaleziono i załadowany Jeśli czasu wykonywania aplikacji. Pliku CPP odwołujących się do zasobu nie jest ponownie kompilowana. W takich przypadkach należy jawnie skompiluj żadnego. Dotyczy plików CPP, które znasz zmiany symbol w ZASOBIE. H lub wybierz **rekompilacji wszystkiego**. Jeśli trzeba często Zmienianie symbolu wartości dla grupy zasobów, prawdopodobnie znajduje się on bardziej wygodne i bezpieczniejsze rozbicie tych symboli w pliku oddzielny nagłówek tylko do odczytu, zgodnie z opisem w powyższej sekcji [włącznie Pliki nagłówkowe dodatkowe](#_mfcnotes_tn035_including).  
  
## <a name="_mfcnotes_tn035_set_includes"></a>W jaki sposób zarządza Visual C++ zestaw zawiera informacje o **  
  
 Jak wspomniano powyżej, ustaw zawiera polecenia menu Plik pozwala określić trzy rodzaje informacji:  
  
-   Plik nagłówka symbolu  
  
-   Dyrektywy symboli tylko do odczytu  
  
-   Dyrektywy kompilacji  
  
 Poniżej opisano zachowywanie tych informacji w programie Visual C++. Plik RC. Nie trzeba te informacje do używania języka Visual C++, ale może pomóc lepiej zrozumieć, aby bardziej bezpieczne można ustawić obejmuje funkcję.  
  
 Każdego z trzech powyższych typów ustawić zawiera informacje są przechowywane w. Plik RC w dwóch formach: (1) jako #include lub dyrektyw interpretable przez kompilator zasobów i (2) jako interpretable specjalne zasoby TEXTINCLUDE tylko przez Visual C++.  
  
 Zasobu TEXTINCLUDE ma na celu bezpiecznie przechowywać informacji ustawić obejmują w formularz, który jest łatwo presentable w programie Visual C++ **ustawić obejmuje** okno dialogowe. Jest TEXTINCLUDE *typu zasobu* zdefiniowane przez Visual C++. Visual C++ rozpoznaje trzy określonych zasobów TEXTINCLUDE, które mają zasobów numery identyfikacyjne 1, 2 i 3:  
  
|Identyfikator zasobu TEXTINCLUDE|Typ ustawiony obejmuje informacji|  
|-----------------------------|--------------------------------------|  
|1|Plik nagłówka symbolu|  
|2|Dyrektywy symboli tylko do odczytu|  
|3|Dyrektywy kompilacji|  
  
 Domyślnie MOJA_APLIKACJA przedstawiono każdego z trzech typów ustawić zawiera informacje. RC i zasobów. H tworzonych przez kreatorami AppWizard, zgodnie z poniższym opisem. Dodatkowe \0 i "" tokeny od rozpoczęcia i zakończenia bloki są wymagane przez RC składni odpowiednio określić zero ciągi zakończone i znaku podwójnego cudzysłowu.  
  
## <a name="symbol-header-file"></a>Plik nagłówka symbolu  
 Formularz informacji plik nagłówka symbolu interpretowane przez kompilator zasobów jest po prostu #include instrukcji:  
  
```  
#include "resource.h"  
```  
  
 Odpowiadający jej zasób TEXTINCLUDE jest:  
  
```  
1 TEXTINCLUDE DISCARDABLE  
BEGIN  
 "resource.h\0"  
END  
```  
  
## <a name="read-only-symbol-directives"></a>Dyrektywy symboli tylko do odczytu  
 Dyrektywy symboli tylko do odczytu są uwzględniane w górnej części MOJA_APLIKACJA. RC w następującej postaci interpretable przez kompilator zasobów:  
  
```  
#include "afxres.h"  
```  
  
 Odpowiadający jej zasób TEXTINCLUDE jest:  
  
```  
2 TEXTINCLUDE DISCARDABLE  
BEGIN  
   "#include ""afxres.h""\r\n"  
   "\0"  
END  
```  
  
## <a name="compile-time-directives"></a>Dyrektywy kompilacji  
 Dyrektywy kompilacji znajdują się na końcu MOJA_APLIKACJA. RC w następującej postaci interpretable przez kompilator zasobów:  
  
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
  
 Dyrektywa #ifndef APSTUDIO_INVOKED nakazuje Visual C++, aby pominąć dyrektywy kompilacji.  
  
 Odpowiadający jej zasób TEXTINCLUDE jest:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

