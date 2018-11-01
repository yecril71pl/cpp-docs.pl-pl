---
title: Pliki wskazówki
ms.date: 11/04/2016
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: 0b3ca7c6b09d85cddb519242e63af0b8097e3fec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558785"
---
# <a name="hint-files"></a>Pliki wskazówki

A *pliku podpowiedzi* programu Visual Studio pomaga zintegrowanego środowiska programistycznego (IDE) interpretacji identyfikatorów języka Visual C++, takich jak nazwy funkcji i makra. Po otwarciu projektu Visual C++, IDE firmy *analizowania system* analizuje kod w każdym pliku źródłowego w projekcie i zbiera informacje na temat każdego identyfikatora. Następnie IDE używa tych informacji do obsługi funkcji, takich jak **Widok klas** przeglądarki i **pasek nawigacyjny**.

Podczas analizowania system, który został wprowadzony w programie Visual C++ 2010, zrozumienie składni języka C/C++, ale mogą błędnie interpretuje instrukcję, która zawiera makra. Wykonywanie instrukcji może być błędnie zinterpretowana, jeśli makro powoduje, że kod źródłowy składniowo nieprawidłowy podczas zapisywania. Wykonywanie instrukcji może stać się poprawnych składniowo podczas kompilowania kodu źródłowego i zastępuje preprocesora [identyfikator — makro](../preprocessor/hash-define-directive-c-cpp.md) z jego definicji. Podczas analizowania system działa bez konieczności tworzenia projektu, ponieważ używa ona pliki wskazówki do interpretacji makra. W związku z tym, przeglądania funkcji takich jak **Widok klas** jest natychmiast dostępna.

Można dostosować użytkownika zawiera pliku podpowiedzi *wskazówek dotyczących serwerów*, które mają tej samej składni jako definicje makr C/C++. Visual C++ zawiera plik wskazówka wbudowane są wystarczające dla większości projektów, ale można utworzyć we własnych plikach wskazówki, aby poprawić sposób, w programie Visual Studio obsługuje identyfikatorów.

> [!IMPORTANT]
> Modyfikowanie lub Dodawanie pliku podpowiedzi, należy usunąć plik sdf i/lub VC.db plików w rozwiązaniu, aby zmiany zaczęły obowiązywać.

## <a name="scenario"></a>Scenariusz

Przyjęto założenie, że następujący kod znajduje się w pliku źródłowego, który można sprawdzić za pomocą **Widok klas** przeglądarki. `STDMETHOD` Makro deklaruje metodę o nazwie `myMethod` przyjmuje jeden parametr i zwraca wskaźnik do **HRESULT**.

```cpp
// Source code file.
STDMETHOD(myMethod)(int parameter1);
```

Następujące definicje makr znajdują się w pliku nagłówka oddzielne.

```cpp
// Header file.
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)
#define STDMETHODCALLTYPE __stdcall
#define HRESULT void*
```

Podczas analizowania systemu nie można zinterpretować kodu źródłowego, ponieważ funkcja o nazwie `STDMETHOD` wydaje się być zadeklarowany, i deklaracja jest nieprawidłowy, ponieważ zawiera ona dwie listy parametrów. Podczas analizowania system nie otworzyć pliku nagłówka, aby odkryć definicje `STDMETHOD`, `STDMETHODCALLTYPE`, i `HRESULT` makra. Ponieważ nie można zinterpretować systemu podczas analizowania `STDMETHOD` makra ignoruje całą instrukcję, a następnie kontynuuje analizowanie.

System analizy nie używa plików nagłówkowych, ponieważ projekt może zależeć od jednego lub więcej plików nagłówkowych ważne. Jeśli zmieni się dowolny plik nagłówka, analizowania system może być konieczne reexamine wszystkie pliki nagłówkowe w swoim projekcie i spowalnia wydajność środowiska IDE. Zamiast tego podczas analizowania system używa wskazówek dotyczących serwerów, które określają sposób obsługi `STDMETHOD`, `STDMETHODCALLTYPE`, i `HRESULT` makra.

Skąd wiadomo, należy wskazówkę? I jeśli potrzebujesz wskazówkę, jakiego rodzaju powinien utworzysz? Jeden logowanie omówioną wskazówką jest Jeśli widok identyfikatora w **Widok klas** jest niespójny z widoku w **edytora**. Na przykład **Widok klas** mogą nie zostanie wyświetlona składowej klasy, której wiadomo, że istnieje, lub nazwę elementu członkowskiego jest nieprawidłowy. Aby uzyskać więcej informacji o typach wskazówek, które rozwiązywania typowych problemów Zobacz co makra wymagają wskazówka? w dalszej części tego tematu.

## <a name="architecture"></a>Architektura

Pliki wskazówki odnoszą się do katalogów fizycznych, przedstawiona katalogi logiczne **Eksploratora rozwiązań**. Nie trzeba dodać pliku podpowiedzi do projektu do pliku podpowiedzi, które mają wpływ. Podczas analizowania system używa pliki wskazówki, tylko wtedy, gdy jej analizuje pliki źródłowe.

Nosi nazwę każdego pliku podpowiedzi **cpp.hint**. W związku z tym plik wskazówki może się znajdować wiele katalogów, ale tylko jedna wskazówka pliku może wystąpić w określonym katalogu.

Projekt mogą mieć wpływ na zero lub więcej pliki wskazówki. Jeśli nie ma żadnych plików wskazówkę, analizy system używa technik odzyskiwania błąd ignorowanie kodu źródłowego w ciągu. W przeciwnym razie podczas analizowania system używa następujących strategii do znalezienia i zebrać wskazówek.

### <a name="search-order"></a>Kolejność wyszukiwania

Podczas analizowania system przeszukuje katalogi plików wskazówki, w następującej kolejności.

- Katalog, który zawiera pakiet instalacyjny dla języka Visual C++ (**vcpackages**). Ten katalog zawiera plik wbudowanych wskazówki opisujące symboli w systemie często używanych plików, takich jak **windows.h**. W związku z tym projekt automatycznie dziedziczy większość z tych wskazówek, których potrzebuje.

- Ścieżka z katalogu głównego pliku źródłowego do katalogu zawierającego plik źródłowy, sam. W typowym projekcie Visual C++ katalog główny zawiera plik rozwiązania lub projektu.

   Wyjątkiem od tej reguły jest Jeśli *pliku stop* znajduje się w ścieżce do pliku źródłowego. Plik zatrzymania zapewnia dodatkową kontrolę nad kolejność wyszukiwania i jest każdy plik, który nosi nazwę **cpp.stop**. Zamiast począwszy od katalogu głównego, analizowania system przeszukuje z katalogu, który zawiera plik zatrzymania do katalogu, który zawiera plik źródłowy. W typowym projekcie nie potrzebujesz pliku zatrzymania.

### <a name="hint-gathering"></a>Wskazówka zbieranie

Plik wskazówki zawiera zero lub więcej *wskazówek*. Wskazówką jest zdefiniowany lub usunięta tak samo jak makra języka C/C++. Oznacza to, że `#define` dyrektywy preprocesora tworzy lub ponownie wskazówkę i `#undef` dyrektywy usuwa wskazówką.

Podczas analizowania system otwiera każdego pliku podpowiedzi w kolejności wyszukiwania opisanej wcześniej, gromadzi wskazówek każdy plik na zestaw *skuteczne wskazówek*, a następnie używa skuteczne wskazówki do interpretacji identyfikatorów w kodzie.

Podczas analizowania system używa następujących reguł do wskazówek dotyczących serwerów.

- Jeśli nowe wskazówki Określa nazwę, która nie jest już zdefiniowany, nową wskazówkę dotyczącą dodaje nazwę do skutecznego wskazówek.

- Jeśli nowy Wskazówka określa nazwę, która jest już zdefiniowany, nową wskazówkę dotyczącą redefiniuje istniejących wskazówki.

- Jeśli jest nową wskazówkę dotyczącą `#undef` dyrektywy, który określa skutecznych podpowiedzi, nową wskazówkę dotyczącą usuwa istniejące wskazówki.

Pierwszą regułę oznacza skuteczne wskazówek zostały odziedziczone wskazówka wcześniej otwartych plików. Ostatnie dwie reguły oznacza, że wskazówki, które występują w dalszej kolejności wyszukiwania można zastąpić wskazówek, które wystąpiły wcześniej. Na przykład można zastąpić poprzedniego wskazówek dotyczących po utworzeniu pliku podpowiedzi w katalogu, który zawiera plik źródłowy.

Aby uzyskać sceny jak zbierane są wskazówki, zobacz `Example` w dalszej części tego tematu.

### <a name="syntax"></a>Składnia

Wskazówki dotyczące tworzenia i usunąć z tej samej składni jako dyrektywy preprocesora, które umożliwiają tworzenie i usuwanie makra. W rzeczywistości analizy system używa preprocesora C/C++, można obliczyć wskazówek. Aby uzyskać więcej informacji na temat dyrektywy preprocesora, zobacz [#define — dyrektywa (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) i [#undef — dyrektywa (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md).

Elementy składni tylko nietypowe są `@<`, `@=`, i `@>` ciągów zastępczych. Są to ciągi określone zastąpienia pliku podpowiedzi, które są używane tylko z *mapy* makra. Mapa jest zestaw makra, które dotyczą danych, funkcji lub zdarzeń innych danych, funkcji lub procedury obsługi zdarzeń. Na przykład `MFC` utworzyć przy użyciu map [komunikatu mapy](../mfc/reference/message-maps-mfc.md), i `ATL` utworzyć przy użyciu map [obiektu mapy](../atl/reference/object-map-macros.md). Parametry określone zastąpienia pliku podpowiedzi wskazują początkowy, pośrednie i końcowy elementy mapy. Istotne jest tylko nazwa makra mapy. W związku z tym każdy ciąg zastępujący celowo powoduje ukrycie opcji wdrożenia makra.

Wskazówki należy użyć następującej składni.

|Składnia|Znaczenie|
|------------|-------------|
|`#define` *Wskazówka dotycząca nazwy* *ciąg zastępujący*<br /><br /> `#define` *Wskazówka dotycząca nazwy* `(` *parametru*,... `)` *ciąg zastępujący*|Dyrektywy preprocesora, definiuje wskazówkę dotyczącą nowych lub ponownie wskazówką istniejących. Po dyrektywie preprocesora zamienia każde wystąpienie *nazw wskazówka* w kodzie źródłowym za pomocą *ciąg zastępujący*.<br /><br /> Druga forma składni definiuje funkcyjne wskazówkę. W przypadku wskazówką funkcyjne w kodzie źródłowym, preprocesor najpierw zamienia każde wystąpienie *parametru* w *ciąg zastępujący* za pomocą odnośnego argumentu w kodzie źródłowym, a następnie zastępuje *nazw wskazówka* z *ciąg zastępujący*.|
|`@<`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza początek zbiór elementów mapy.|
|`@=`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza element pośredni mapy. Mapy może mieć wielu elementów mapy.|
|`@>`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza koniec zbiór elementów mapy.|
|`#undef` *Wskazówka dotycząca nazwy*|Dyrektywy preprocesora, który służy do usuwania istniejących wskazówki. Nazwa wskazówka odbywa się przy *nazw wskazówka* identyfikatora.|
|`//` *Komentarz*|Pojedynczy wiersz komentarza.|
|`/*` *Komentarz* `*/`|Komentarz wielowierszowy.|

## <a name="what-macros-require-a-hint"></a>Co to makra wymagają wskazówkę?

Niektóre rodzaje makra mogą zakłócać systemu podczas analizowania. W tej sekcji opisano typy makr, które może powodować problem i typ wskazówka, że możesz tworzyć, aby rozwiązać ten problem.

### <a name="disruptive-macros"></a>Szkodliwe makra

Niektóre makra systemu podczas analizowania do błędnie interpretuje kodu źródłowego, ale można je zignorować bez zakłócania przeglądania sieci. Na przykład język adnotacji kodu źródłowego ([SAL](../c-runtime-library/sal-annotations.md)) makra rozpoznać atrybutów języka C++, które pomagają znaleźć błędy programowania. Chcesz zignorować adnotacji SAL podczas przeglądania kodu, można utworzyć pliku podpowiedzi, która ukrywa adnotacji.

W poniższym kodzie źródłowym, wpisz parametr `FormatWindowClassName()` funkcja `PXSTR`, a nazwa parametru jest `szBuffer`. Jednak podczas analizowania błędów systemowych `_Pre_notnull_` i `_Post_z_` adnotacji SAL typ parametru lub nazwę parametru.

**Kod źródłowy:**

```cpp
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)
```

**Strategia:** Null definicji

Strategia w tej sytuacji jest przetwarzanie adnotacji SAL tak, jakby nie istniał. Aby to zrobić, należy określić wskazówki, w której ciąg zastępujący ma wartość null. W związku z tym, podczas analizowania system ignoruje adnotacje i **Widok klas** przeglądarki te nie są wyświetlane. (Visual C++ w tym pliku podpowiedzi wbudowanych, która ukrywa adnotacji SAL.)

**Plik wskazówki:**

```cpp.hint
#define _Pre_notnull_
```

### <a name="concealed-cc-language-elements"></a>Elementy języka C/C++ ukryte

Typową przyczyną, że systemu podczas analizowania misinterprets kod źródłowy jest, jeśli makro ukrywa C/C++ [znak interpunkcyjny](../cpp/punctuators-cpp.md) lub [— słowo kluczowe](../cpp/keywords-cpp.md) tokenu. Oznacza to, makro może zawierać połowę parę przerywniki języka, takie jak `<>`, `[]`, `{}`, i `()`.

W poniższym kodzie źródłowym `START_NAMESPACE` — makro ukrywa niesparowane nawias klamrowy otwierający (`{`).

**Kod źródłowy:**

```cpp
#define START_NAMESPACE namespace MyProject {
```

**Strategia:** bezpośrednie kopiowania

Jeżeli semantyka makra są krytyczne dla działania przeglądarki, należy utworzyć wskazówkę, która jest taka sama jak makra. Podczas analizowania systemu jest rozpoznawany jako makra definicję w pliku podpowiedzi.

Należy pamiętać o tym, jeśli makro w pliku źródłowym zawiera innych makr, te makra interpretację tylko wtedy, gdy są one już zestaw skuteczne wskazówek dotyczących serwerów.

**Plik wskazówki:**

```cpp.hint
#define START_NAMESPACE namespace MyProject {
```

### <a name="maps"></a>Mapy

Mapa zawiera makra, które wyznaczają element początkowy, końcowy element i zero lub więcej elementów pośrednich. Podczas analizowania systemu misinterprets maps, ponieważ każde makro mapy ukrywa elementy języka C/C++ i składni pełną instrukcję języka C/C++ jest rozłożona na wiele oddzielnych makra.

Poniższy kod źródłowy definiuje `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY`, i `END_CATEGORY_MAP` makra.

**Kod źródłowy:**

```cpp
#define BEGIN_CATEGORY_MAP(x)\
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },
#define END_CATEGORY_MAP()\
   { _ATL_CATMAP_ENTRY_END, NULL } };\
   return( pMap ); }
```

**Strategia:** identyfikowanie elementów mapy

Określanie wskazówki dotyczące rozpoczęcia, drugie (jeśli istnieje) i zakończenia elementy mapy. Użyć ciągów zastępczych specjalne mapy, `@<`, `@=`, i `@>`. Aby uzyskać więcej informacji, zobacz `Syntax` w tym temacie.

**Plik wskazówki:**

```cpp.hint
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

Makra złożonego zawierać jeden lub więcej typów makra, które należy mylić systemu podczas analizowania.

Poniższy kod źródłowy zawiera `START_NAMESPACE` makra, która określa początek zakresu przestrzeni nazw, a `BEGIN_CATEGORY_MAP` makra, która określa początek mapy.

**Kod źródłowy:**

```cpp
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

**Strategia:** bezpośrednie kopiowania

Wskazówki dotyczące tworzenia `START_NAMESPACE` i `BEGIN_CATEGORY_MAP` makra, a następnie Utwórz podpowiedź dotyczącą `NSandMAP` makra, która jest taka sama, jak pokazano wcześniej kodu źródłowego. Alternatywnie Jeśli złożone — makro składa się tylko z makra uciążliwe i biały znak, można zdefiniować wskazówkę, którego ciąg zastępujący jest definicją o wartości null.

W tym przykładzie przyjęto założenie, `START_NAMESPACE` już wskazówkę, zgodnie z opisem w tym temacie w `Concealed C/C++ Language Elements` podtytułu. I bierze na siebie `BEGIN_CATEGORY_MAP` ma wskazówkę, jak opisano wcześniej w `Maps`.

**Plik wskazówki:**

```cpp.hint
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

### <a name="inconvenient-macros"></a>Nie można użyć makra

Niektóre makra mogą być interpretowane przez system analizy, ale kod źródłowy jest trudne do odczytania, ponieważ makra jest długie lub zbyt złożone. Dla czytelności może podać wskazówkę, upraszczającego wyświetlanie makra.

**Kod źródłowy:**

```cpp
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)
```

**Strategia:** uproszczenia

Utworzyć wskazówkę wyświetlającą prostsze definicji makra.

**Plik wskazówki:**

```cpp.hint
#define STDMETHOD(methodName) void* methodName
```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wskazówki są zbierane z pliki wskazówki. Zatrzymaj pliki nie są używane w tym przykładzie.

Poniższa ilustracja przedstawia niektóre katalogi fizyczne w projekcie Visual C++. Pliki wskazówki znajdują się w `vcpackages`, `Debug`, `A1`, i `A2` katalogów.

### <a name="hint-file-directories"></a>Wskazówka katalogi plików

![Typowe i projekt&#45;wskazówki określone katalogi plików. ](../ide/media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Katalogi i zawartość pliku wskazówka

Na poniższej liście przedstawiono katalogi, w tym projekcie, zawierających pliki wskazówki i zawartość tych plików wskazówki. Tylko niektóre z wielu wskazówki w `vcpackages` pliku podpowiedzi katalogu są wyświetlane.

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Debugowanie

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Skuteczne wskazówki

W poniższej tabeli wymieniono skuteczne wskazówek dotyczących plików źródłowych, w tym projekcie.

- Plik źródłowy: A1_A2_B.cpp

- Skuteczne wskazówek:

    ```cpp.hint
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

Poniższe uwagi dotyczą powyższej liście.

- Skuteczne wskazówki są z `vcpackages`, `Debug`, `A1`, i `A2` katalogów.

- **#Undef** dyrektywy w `Debug` pliku podpowiedzi usunięte `#define _In_` podpowiedzi w `vcpackages` pliku podpowiedzi katalogu.

- Pliku podpowiedzi w `A1` redefiniuje katalogu `START_NAMESPACE`.

- `#undef` Podpowiedzi w `A2` wskazówek dotyczących usunąć katalogu `OBRACE` i `CBRACE` w `Debug` pliku podpowiedzi katalogu.

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[#define, dyrektywa (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef, dyrektywa (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Adnotacje SAL](../c-runtime-library/sal-annotations.md)<br>
[Mapy komunikatów](../mfc/reference/message-maps-mfc.md)<br>
[Makra mapy komunikatów](../atl/reference/message-map-macros-atl.md)<br>
[Makra mapy obiektów](../atl/reference/object-map-macros.md)