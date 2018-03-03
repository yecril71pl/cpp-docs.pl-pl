---
title: "Pliki wskazówki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 432b5fa5041a7997c9df0593dc511c29854387ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hint-files"></a>Pliki wskazówki
A *plik wskazówki* pomaga w Visual Studio identyfikatory Visual C++, takie jak nazwy funkcjami i makrami zinterpretować zintegrowane środowisko programistyczne (IDE). Po otwarciu projektu Visual C++, IDE w *analizy systemu* analizę kodu w każdym pliku źródłowego w projekcie i zbiera informacje na temat każdy identyfikator. Następnie IDE używa tych informacji do obsługi funkcji, takich jak **widoku klasy** przeglądarki i **pasek nawigacyjny**.  
  
 Podczas analizowania system, który wprowadzono w programie Visual C++ 2010 rozumie składni języka C/C++, ale może błędnie interpretuje instrukcję, która zawiera makr. Jeśli makra powoduje, że kod źródłowy jest niepoprawna składnia podczas zapisywania zostać błędnie zinterpretowane instrukcji. Instrukcja może stać się poprawna składniowo podczas kompilowania kodu źródłowego i zastępuje preprocesora [identyfikator makro](../preprocessor/hash-define-directive-c-cpp.md) z jego definicji. Podczas analizowania system działa bez konieczności budowania projektu, ponieważ używa on pliki wskazówki interpretować makra. W związku z tym Przeglądanie funkcji, takich jak **widoku klasy** jest natychmiast dostępna.  
  
 Plik wskazówki zawiera dostosowania użytkownika *wskazówek*, który mieć takiej samej składni jak definicje makr C/C++. Visual C++ zawiera plik wskazówka wbudowanych są wystarczające dla większości projektów, ale można utworzyć własne pliki wskazówki w celu zwiększenia możliwości programu Visual Studio obsługuje identyfikatory.  
  
> [!IMPORTANT]
>  Modyfikowanie lub Dodawanie pliku wskazówek, należy usunąć pliku .sdf i/lub pliku VC.db w rozwiązaniu aby zmiany zaczęły obowiązywać.  
  
## <a name="scenario"></a>Scenariusz  
 Założono, że następujący kod jest w pliku źródłowym, który należy zbadać z **widoku klasy** przeglądarki. `STDMETHOD` Makro deklaruje metodę o nazwie `myMethod` przyjmuje jeden parametr i zwraca wskaźnik do **HRESULT**.  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 Poniższe definicje makr znajdują się w pliku oddzielny nagłówek.  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 Podczas analizowania systemu nie może zinterpretować kodu źródłowego, ponieważ funkcja o nazwie stdmethod — wydaje się być zadeklarowany jako, a deklaracja jest nieprawidłowy, ponieważ zawiera dwie listy parametrów. Podczas analizowania system nie otworzyć plik nagłówka, aby odnaleźć definicje `STDMETHOD`, `STDMETHODCALLTYPE`, i `HRESULT` makra. Ponieważ system analizy nie może zinterpretować `STDMETHOD` makra ignoruje całą instrukcję, a następnie jest kontynuowana analizy.  
  
 Podczas analizowania system nie używa pliki nagłówkowe, ponieważ projekt może być zależna od co najmniej jeden plik nagłówka ważne. W przypadku zmiany dowolnego pliku nagłówka, systemu przetwarzania może być konieczne reexamine wszystkie pliki nagłówka w projekcie spowalnia działanie środowiska IDE. Zamiast tego podczas analizowania system używa wskazówki, które określają sposób obsługi `STDMETHOD`, `STDMETHODCALLTYPE`, i `HRESULT` makra.  
  
 Skąd wiadomo, że należy wskazówkę? I jeśli potrzebujesz wskazówkę, jakiego rodzaju powinien utworzysz? Jeden znak, że niezbędna jest wskazówkę jest Jeśli identyfikatora w widoku **widoku klasy** jest niespójny z widoku w **edytor**. Na przykład **widoku klasy** może nie wyświetlania istnieje element członkowski klasy, który znasz lub nazwa elementu członkowskiego jest nieprawidłowa. Aby uzyskać więcej informacji o typach wskazówki, które rozwiązywania typowych problemów Zobacz co makra wymagają A wskazówka? dalszej części tego tematu.  
  
## <a name="architecture"></a>Architektura  
 Pliki wskazówki odnoszą się do katalogów fizycznych, katalogi logicznej opisany w **Eksploratora rozwiązań**. Nie trzeba dodać plik wskazówki do projektu dla pliku wskazówek, które mają wpływ. Podczas analizowania system używa pliki wskazówki tylko wtedy, gdy analizuje pliki źródłowe.  
  
 Każdy plik wskazówka nosi nazwę **cpp.hint**. W związku z tym plik wskazówka może się znajdować wiele katalogów, ale wskazówka tylko jeden plik może wystąpić z określonego katalogu.  
  
 Pliki wskazówki zero lub więcej mogą mieć wpływ projektu. Jeśli nie ma żadnych plików wskazówki, analizy system używa technik odzyskiwania błąd zignorować kodu źródłowego nierozpoznawalne. W przeciwnym razie analizy systemu używa następujących strategii do znalezienia i zebrać wskazówek.  
  
### <a name="search-order"></a>Kolejność wyszukiwania  
 Podczas analizowania system wyszukuje katalogów pliki wskazówki w następującej kolejności.  
  
-   Katalog, który zawiera pakiet instalacyjny dla programu Visual C++ (**vcpackages**). Ten katalog zawiera plik wbudowanych wskazówka opisujący symbole w systemie często używanych plików, takich jak **windows.h**. W rezultacie projektu automatycznie dziedziczy większość wskazówki, które wymaga.  
  
-   Ścieżka z katalogu głównego pliku źródłowego do katalogu zawierającego plik źródłowy, sama. W typowym projekcie Visual C++ katalog główny zawiera plik rozwiązania lub projektu.  
  
     Wyjątkiem od tej reguły jest Jeśli *plik zatrzymania* znajduje się w ścieżce do pliku źródłowego. Plik zatrzymania zapewnia dodatkową kontrolę nad kolejność wyszukiwania i jest dowolny plik o nazwie **cpp.stop**. Zamiast od katalogu głównego, wyszukiwania podczas analizowania system z katalogu, który zawiera plik zatrzymania do katalogu, który zawiera plik źródłowy. W typowym projekcie nie trzeba plik zatrzymania.  
  
### <a name="hint-gathering"></a>Zbieranie wskazówki  
 Plik wskazówki zawiera zero lub więcej *wskazówek*. Wskazówkę jest zdefiniowana lub usunięty, podobnie jak makr C/C++. Oznacza to `#define` dyrektywy preprocesora tworzy lub ponownie definiuje wskazówkę i `#undef` dyrektywy usuwa wskazówkę.  
  
 Podczas analizowania system otwiera każdego pliku wskazówek w kolejności wyszukiwania opisanych wcześniej, akumuluje wskazówek każdego pliku na zestaw *skuteczne wskazówek*, a następnie używa skuteczne wskazówek interpretować identyfikatorów w kodzie.  
  
 Podczas analizowania system używa następujących reguł do gromadzone wskazówek.  
  
-   Jeśli nowy Wskazówka określa nazwę, która nie jest już zdefiniowany nową wskazówkę dotyczącą dodaje nazwę do wprowadzenia wskazówek.  
  
-   Jeśli nowy Wskazówka określa nazwę, która jest już zdefiniowana, wskazówka nowego ponownie definiuje istniejących wskazówki.  
  
-   Jeśli nowy wskazówka jest `#undef` w dyrektywie, który określa skutecznych podpowiedzi, wskazówka nowego usuwa istniejące wskazówki.  
  
 Pierwsza reguła oznacza skuteczne wskazówki zostały odziedziczone wskazówka wcześniej otwartych plików. Ostatnich dwóch reguł oznacza, że wskazówki występujące później w kolejności wyszukiwania można zastąpić wskazówki, które wystąpiły wcześniej. Na przykład można zastąpić poprzednie wskazówki, jeśli Tworzenie pliku wskazówkę w katalogu, który zawiera plik źródłowy.  
  
 Aby sceny jak zbierane są wskazówki, zobacz `Example` później w tym temacie.  
  
### <a name="syntax"></a>Składnia  
 Wskazówki dotyczące tworzenia i usunąć z tej samej składni jak dyrektywy preprocesora, które tworzenie i usuwanie makra. W rzeczywistości analizy system używa preprocesora języka C/C++ do oceny wskazówek. Aby uzyskać więcej informacji na temat dyrektywy preprocesora, zobacz [#define — dyrektywa (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) i [#undef — dyrektywa (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md).  
  
 Elementy składni tylko nietypowe są `@<`, `@=`, i `@>` ciągów zamiennych. Są to plik wskazówki konkretnego zamiennika ciągów, które są używane tylko z *mapy* makra. Mapa jest zestawem makr, które dotyczą danych, funkcji lub zdarzeń innych danych, funkcji lub procedury obsługi zdarzeń. Na przykład `MFC` używa mapy w celu utworzenia [mapy komunikatów](../mfc/reference/message-maps-mfc.md), i `ATL` używa mapy w celu utworzenia [obiekt mapy](../atl/reference/object-map-macros.md). Ciągi zamienne określonego pliku wskazówek wskazuje początkowy, pośrednie i końcowy elementów mapy. Istotne jest tylko nazwa makra mapy. W związku z tym każdy ciąg zastępczy celowo ukrywa implementacji makra.  
  
 Wskazówek dotyczących serwerów należy użyć następującej składni.  
  
|Składnia|Znaczenie|  
|------------|-------------|  
|`#define`*nazwa wskazówka* *ciąg zastępczy*<br /><br /> `#define`*nazwa wskazówka* `(` *parametru*,... `)` *ciąg zastępczy*|Dyrektywy preprocesora, który definiuje nową wskazówkę dotyczącą lub ponownie definiuje wskazówką istniejących. Po dyrektywie preprocesora zamienia każde wystąpienie *nazwa wskazówka* w kodzie źródłowym z *ciąg zastępczy*.<br /><br /> Drugi formularz składni definiuje wskazówkę podobnych funkcji. Sytuacji wskazówkę podobnych funkcji w kodzie źródłowym preprocesora najpierw zamienia każde wystąpienie *parametru* w *ciąg zastępczy* z argumentem odpowiedni kod źródłowy i zamienia *nazwa wskazówka* z *ciąg zastępczy*.|  
|`@<`|Określony plik wskazówki *ciąg zastępczy* wskazujące to początek zestawu elementów mapy.|  
|`@=`|Określony plik wskazówki *ciąg zastępczy* który wskazuje element pośredni mapy. Mapa może mieć wielu elementów mapy.|  
|`@>`|Określony plik wskazówki *ciąg zastępczy* oznacza koniec zbiór elementów mapy.|  
|`#undef`*nazwa wskazówki*|Dyrektywy preprocesora usuwa istniejące wskazówki. Nazwa wskazówka odbywa się przy *nazwa wskazówka* identyfikator.|  
|`//`*komentarza*|Jednowierszowego komentarza.|  
|`/*`*komentarz*`*/`|Komentarz wielowierszowy.|  
  
## <a name="what-macros-require-a-hint"></a>Co makra wymagają wskazówkę?  
 Niektóre typy makr może zakłócać analizy systemu. W tej sekcji opisano typy makra, które mogą spowodować problem, a typ wskazówkę można utworzyć w celu rozwiązania tego problemu.  
  
### <a name="disruptive-macros"></a>Zakłócenie makra  
 Niektóre makra spowodować analizy systemu błędnie interpretuje kodu źródłowego, ale może zostać zignorowany bez zakłócania przeglądania sieci. Na przykład język adnotacji kodu źródłowego ([SAL](../c-runtime-library/sal-annotations.md)) makra rozpoznać atrybuty C++, które ułatwiają znajdowanie usterki programowania. Jeśli chcesz zignorować adnotacji SAL podczas przeglądania kodu, można utworzyć pliku wskazówek, która ukrywa adnotacji.  
  
 W poniższym kodzie źródłowym parametr typu dla `FormatWindowClassName()` jest funkcja `PXSTR`, a nazwa parametru jest `szBuffer`. Jednak podczas analizowania błędów systemu `_Pre_notnull_` i `_Post_z_` adnotacji SAL dla parametru typu lub nazwę parametru.  
  
 **Kod źródłowy:**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **Strategia:** definicji o wartości Null  
  
 Strategii w tej sytuacji jest traktowana adnotacji SAL tak, jakby nie został znaleziony. Aby to zrobić, należy określić wskazówki, których ciąg zastępczy ma wartość null. W rezultacie analizy systemu ignoruje adnotacje i **widoku klasy** przeglądarki te nie są wyświetlane. (Visual C++ zawiera plik wbudowanych wskazówka ukrywa adnotacji SAL.)  
  
 **Plik wskazówki:**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>Elementy języka C/C++ ukryte  
 Typowe przyczyny, że analizy systemu misinterprets kod źródłowy jest Jeśli makra ukrywa C/C++ [znak interpunkcyjny](../cpp/punctuators-cpp.md) lub [— słowo kluczowe](../cpp/keywords-cpp.md) tokenu. Oznacza to makro może zawierać połowę pary znaki interpunkcyjne, takie jak `<>`, `[]`, `{}`, i `()`.  
  
 W poniższym kodzie źródłowym `START_NAMESPACE` makro ukrywa nieparzysty lewego nawiasu klamrowego (`{`).  
  
 **Kod źródłowy:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **Strategia:** bezpośrednie kopiowania  
  
 Jeśli semantykę makra są krytyczne dla działania przeglądarki, należy utworzyć wskazówkę, która jest taka sama jak makra. Podczas analizowania systemu usuwa makro do definicji w pliku wskazówek.  
  
 Należy zwrócić uwagę, jeśli makra w pliku źródłowym zawiera inne makra, te makra interpretację tylko wtedy, gdy są one już zestaw wskazówek skuteczne.  
  
 **Plik wskazówki:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>Mapy  
 Mapa składa się z makra, które określają element początkowy, końcowy element i elementy pośrednie zero lub więcej. Podczas analizowania systemu misinterprets mapy, ponieważ każde makro mapy ukrywa elementy języka C/C++ i składnia pełną instrukcję C/C++ jest rozmieszczona na wielu oddzielnych makra.  
  
 Poniższy kod źródłowy definiuje `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY`, i `END_CATEGORY_MAP` makra.  
  
 **Kod źródłowy:**  
  
```  
#define BEGIN_CATEGORY_MAP(x)\  
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\  
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {  
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },  
#define END_CATEGORY_MAP()\  
   { _ATL_CATMAP_ENTRY_END, NULL } };\  
   return( pMap ); }  
```  
  
 **Strategia:** Identyfikuj elementów mapy  
  
 Określ wskazówek dotyczących początku, środka (jeśli istnieje) i na końcu elementów mapy. Użyj ciągów zamiennych specjalne mapy, `@<`, `@=`, i `@>`. Aby uzyskać więcej informacji, zobacz `Syntax` w tym temacie.  
  
 **Plik wskazówki:**  
  
```  
// Start of the map.  
#define BEGIN_CATEGORY_MAP(x) @<  
// Intermediate map element.  
#define IMPLEMENTED_CATEGORY( catid ) @=  
// Intermediate map element.  
#define REQUIRED_CATEGORY( catid ) @=  
// End of the map.  
#define END_CATEGORY_MAP() @>  
```  
  
### <a name="composite-macros"></a>Złożone makra  
 Złożone makra zawierają jedną lub więcej typów makra, które należy mylić analizy systemu.  
  
 Poniższy kod źródłowy zawiera `START_NAMESPACE` makra, która określa początek zakresu przestrzeni nazw, i `BEGIN_CATEGORY_MAP` makra, która określa początek mapy.  
  
 **Kod źródłowy:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **Strategia:** bezpośrednie kopiowania  
  
 Wskazówek dotyczących tworzenia `START_NAMESPACE` i `BEGIN_CATEGORY_MAP` makra, a następnie Utwórz podpowiedź dla `NSandMAP` makra, który jest taki sam, jak pokazano wcześniej kodu źródłowego. Alternatywnie złożone — makro składa się tylko z makra zakłócenie i biały znak, można określić wskazówki, których ciąg zastępczy jest definicją wartości null.  
  
 W tym przykładzie założono `START_NAMESPACE` ma już wskazówkę zgodnie z opisem w tym temacie w `Concealed C/C++ Language Elements` podtytułu. I przejęcia `BEGIN_CATEGORY_MAP` ma wskazówkę, jak opisano wcześniej w `Maps`.  
  
 **Plik wskazówki:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>Niewygodne makra  
 Niektóre makra może zostać zinterpretowany przez system podczas analizowania, ale kod źródłowy jest trudne do odczytu, ponieważ makro jest długa lub złożonych. Dla czytelności może podać wskazówkę upraszczającym wyświetlania makra.  
  
 **Kod źródłowy:**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **Strategia:** uproszczenia  
  
 Utwórz podpowiedź, która wyświetla prostsze definicji makra.  
  
 **Plik wskazówki:**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak wskazówki jest sumą pliki wskazówki. Zatrzymaj pliki nie są używane w tym przykładzie.  
  
 Poniższa ilustracja przedstawia niektóre z katalogów fizycznych w projekcie Visual C++. Pliki wskazówki znajdują się w `vcpackages`, `Debug`, `A1`, i `A2` katalogów.  
  
### <a name="hint-file-directories"></a>Wskazówka katalogi plików  
 ![Typowe projektu &#45; i katalogi plików określonych wskazówki. ] (../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>Katalogi i zawartość pliku wskazówki  
 Poniższa lista zawiera katalogi w tego projektu, który zawiera pliki wskazówki i zawartość plików te wskazówki. Tylko niektóre z tych wskazówek wiele w `vcpackages` pliku wskazówka katalogu są wyświetlane.  
  
-   vcpackages  
  
    ```  
    // vcpackages (partial list)  
    #define _In_  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    ```  
  
-   Debugowanie  
  
    ```  
    // Debug  
    #undef _In_  
    #define OBRACE {  
    #define CBRACE }  
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {  
    #define END_NAMESPACE }  
    ```  
  
-   A1  
  
    ```  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {  
    ```  
  
-   A2  
  
    ```  
    // A2  
    #undef OBRACE  
    #undef CBRACE  
    ```  
  
### <a name="effective-hints"></a>Skuteczne wskazówki  
 W poniższej tabeli wymieniono skuteczne wskazówki dla plików źródłowych, w tym projekcie.  
  
-   Plik źródłowy: A1_A2_B.cpp  
  
-   Skuteczne wskazówek:  
  
    ```  
    // vcpackages (partial list)  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    // Debug...  
    #define RAISE_EXCEPTION(x) throw (x)  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {   
    // ...Debug  
    #define END_NAMESPACE }  
    ```  
  
 Poniższe uwagi dotyczą powyższej listy.  
  
-   Skuteczne wskazówki są z `vcpackages`, `Debug`, `A1`, i `A2` katalogów.  
  
-   **#Undef** dyrektywę `Debug` usunięto plik wskazówka `#define _In_` wskazówki w `vcpackages` pliku wskazówka katalogu.  
  
-   Plik wskazówki w `A1` ponownie definiuje katalogu `START_NAMESPACE`.  
  
-   `#undef` Wskazówki w `A2` wskazówek dotyczących usunąć katalogu `OBRACE` i `CBRACE` w `Debug` pliku wskazówka katalogu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)    
 [#define — dyrektywa (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef — dyrektywa (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)   
 [Adnotacje SAL](../c-runtime-library/sal-annotations.md)   
 [Mapy komunikatów](../mfc/reference/message-maps-mfc.md)   
 [Makra mapy wiadomości](../atl/reference/message-map-macros-atl.md)   
 [Makra mapy obiektów](../atl/reference/object-map-macros.md)