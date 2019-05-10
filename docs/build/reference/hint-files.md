---
title: Pliki wskazówki
ms.date: 02/26/2019
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
ms.openlocfilehash: 919cbedd0c0d7c610273d597328979d1fb449f8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446308"
---
# <a name="hint-files"></a>Pliki wskazówki

A *pliku podpowiedzi* zawiera makra, które mogłyby spowodować regiony kodu do pominięcia przez Parser bazy danych przeglądania C++. Po otwarciu programu Visual Studio C++ projektu analizator analizuje kod w każdym pliku źródłowego w projekcie i tworzy bazę danych przy użyciu informacji na temat każdego identyfikatora. IDE używa, aby uzyskać informacje dotyczące obsługi przeglądania kodu funkcje, takie jak **Widok klas** przeglądarki i **pasek nawigacyjny**.

Analiza bazy danych przeglądania C++ jest rozmyte analizatora, które można analizować duże ilości kodu w krótkim czasie. Jedną z przyczyn jest szybkie jest, ponieważ pomija zawartość bloków. Na przykład on tylko rekordy lokalizacji i parametrów funkcji i ignoruje jego zawartość. Pewne makra może spowodować problemy z algorytmów heurystycznych używany w celu określenia początku i na końcu bloku. Te problemy powodują regiony kodu ma zostać nieprawidłowo zarejestrowany.

Te regiony pominięto manifestu można na wiele sposobów:

- Brak typów i funkcje w **Widok klas**, **przejdź do** i **pasek nawigacyjny**

- Niepoprawne zakresów w **pasek nawigacyjny**

- Sugestie **Utwórz deklarację/definicję** dla funkcji, które są już zdefiniowane

Pliku podpowiedzi zawiera użytkownika można dostosować wskazówek dotyczących serwerów, które mają tej samej składni jako definicje makr C/C++. Visual C++ zawiera plik wskazówka wbudowane są wystarczające dla większości projektów. Można jednak utworzyć we własnych plikach wskazówki, aby poprawić analizatora specjalnie dla Twojego projektu.

> [!IMPORTANT]
> Modyfikowanie lub Dodawanie pliku podpowiedzi, musisz wykonać dodatkowe kroki, aby zmiany zaczęły obowiązywać:
> - W wersjach starszych niż program Visual Studio 2017 w wersji 15.6: Usuń plik sdf i/lub plik VC.db w rozwiązaniu dla wszystkich zmian.
> - W wersjach programu Visual Studio 2017 15.6 za pośrednictwem 15.9: Zamknij i otwórz ponownie rozwiązanie po dodaniu nowych plików wskazówki.

## <a name="scenario"></a>Scenariusz

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez pliku podpowiedzi `Function` nie pojawiają się w **Widok klas**, **przejdź do** lub **pasek nawigacyjny**. Po dodaniu pliku podpowiedzi, z tą definicją makra, analizator teraz rozumie i zastępuje `NOEXCEPT` makro, co pozwala na poprawnie przeanalizować funkcji:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Szkodliwe makra

Istnieją dwie kategorie makr, które zakłócają analizator składni:

- Makra, które hermetyzują słów kluczowych, które ozdobić funkcji

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Dla tych typów makra tylko nazwa makra jest wymagany w pliku wskazówek:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra, które zawierają niezrównoważone nawiasy kwadratowe

   ```cpp
   #define BEGIN {
   ```

   Dla tych typów makr w pliku podpowiedzi są wymagane nazwy makra wraz z zawartością:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Pomoc techniczna do edytora

Począwszy od programu Visual Studio 2017 w wersji 15.8 kilka funkcji do identyfikowania szkodliwe makra:

- Makra, które znajdują się w regionach pominięte przez parser są wyróżnione.

- Jest szybka akcja do utworzenia pliku wskazówkę, który zawiera wyróżnione makro lub w przypadku istniejącego pliku podpowiedzi do dodawania makra do pliku podpowiedzi.

![Wyróżnione makra. ](media/hint-squiggle-and-actions.png "Podpowiedzi wężyk i szybkie akcje")

Po wykonaniu, albo szybkie akcje, analizator reparses plików dotyczy pliku podpowiedzi.

Domyślnie makro problem jest podświetlona jako sugestię. Wyróżnienie można ją zmienić na coś bardziej zauważalne, takich jak wężyk czerwonego lub zielonego. Użyj **makra w regionach pominięte przeglądania** opcji **faliste linie kodu** sekcji **narzędzia** > **opcje**  >  **Edytora tekstów** > **C/C++** > **widoku**.

![Makra w pominięto opcję przeglądania w regionach. ](media/skipped-regions-squiggle-option.png "Pominięto opcję wężyk regionów.")

## <a name="display-browsing-database-errors"></a>Wyświetl błędy bazy danych przeglądania

**Projektu** > **błędów bazy danych przeglądania wyświetlania** menu polecenie wyświetla wszystkie regiony, które nie można przeanalizować w **lista błędów**. Polecenie jest przeznaczone do usprawnić kompilowanie pliku podpowiedzi początkowej. Jednak Analizator nie wiadomo, jeśli przyczyną błędu były powodującego zakłócenia — makro, dlatego należy ocenić poszczególne błędy. Uruchom **błędów bazy danych przeglądania wyświetlania** polecenia i przejdź do każdego błędu, aby załadować wspomniany plik w edytorze. Po załadowaniu pliku, jeśli wszystkie makra znajdują się w regionie, jest wyróżniona. Można wywoływać szybkie akcje, aby dodać je do pliku podpowiedzi. Po zaktualizowaniu pliku wskazówkę lista błędów jest aktualizowane automatycznie. Alternatywnie, w przypadku ręcznie modyfikacji pliku podpowiedzi można użyć **Skanuj ponownie rozwiązanie** polecenie, aby uruchomić aktualizację.

## <a name="architecture"></a>Architektura

Pliki wskazówki odnoszą się do katalogów fizycznych nie logiczne katalogi pokazane **Eksploratora rozwiązań**. Nie trzeba dodać pliku podpowiedzi do projektu do pliku podpowiedzi, które mają wpływ. Podczas analizowania system używa pliki wskazówki, tylko wtedy, gdy jej analizuje pliki źródłowe.

Nosi nazwę każdego pliku podpowiedzi **cpp.hint**. Plik wskazówki może się znajdować wiele katalogów, ale tylko jedna wskazówka pliku może wystąpić w określonym katalogu.

Projekt mogą mieć wpływ na zero lub więcej pliki wskazówki. Jeśli nie ma żadnych plików wskazówkę, analizy system używa technik odzyskiwania błąd ignorowanie kodu źródłowego w ciągu. W przeciwnym razie podczas analizowania system używa następujących strategii do znalezienia i zebrać wskazówek.

### <a name="search-order"></a>Kolejność wyszukiwania

Podczas analizowania system przeszukuje katalogi plików wskazówki, w następującej kolejności.

- Katalog, który zawiera pakiet instalacyjny dla języka Visual C++ (**vcpackages**). Ten katalog zawiera plik wbudowanych wskazówki opisujące symboli w systemie często używanych plików, takich jak **windows.h**. W związku z tym projekt automatycznie dziedziczy większość z tych wskazówek, których potrzebuje.

- Ścieżka z katalogu głównego pliku źródłowego do katalogu zawierającego plik źródłowy, sam. W typowym środowisku Visual Studio C++ projekt, katalog główny zawiera plik rozwiązania lub projektu.

   Wyjątkiem od tej reguły jest Jeśli *pliku stop* znajduje się w ścieżce do pliku źródłowego. Plik zatrzymania jest dowolny plik, który nosi nazwę **cpp.stop**. Plik zatrzymania zapewnia dodatkową kontrolę nad kolejność wyszukiwania. Zamiast począwszy od katalogu głównego, analizowania system przeszukuje z katalogu, który zawiera plik zatrzymania do katalogu, który zawiera plik źródłowy. W typowym projekcie nie jest potrzebny plik zatrzymania.

### <a name="hint-gathering"></a>Wskazówka zbieranie

Plik wskazówki zawiera zero lub więcej *wskazówek*. Wskazówką jest zdefiniowany lub usunięta tak samo jak makra języka C/C++. Oznacza to, że `#define` dyrektywy preprocesora tworzy lub ponownie wskazówkę i `#undef` dyrektywy usuwa wskazówką.

Podczas analizowania system otwiera każdego pliku podpowiedzi w kolejności wyszukiwania opisanej wcześniej. Jego gromadzi wskazówek każdy plik na zestaw *skuteczne wskazówek*, a następnie używa skuteczne wskazówki do interpretacji identyfikatorów w kodzie.

Podczas analizowania system używa tych reguł do wskazówek dotyczących serwerów:

- Jeśli nowy Wskazówka określa nazwę, która nie jest już zdefiniowany, nową wskazówkę dotyczącą dodaje nazwę do skutecznego wskazówek.

- Jeśli nowy Wskazówka określa nazwę, która jest już zdefiniowany, nową wskazówkę dotyczącą redefiniuje istniejących wskazówki.

- Jeśli jest nową wskazówkę dotyczącą `#undef` dyrektywy, który określa skutecznych podpowiedzi, nową wskazówkę dotyczącą usuwa istniejące wskazówki.

Pierwszą regułę oznacza skuteczne wskazówek zostały odziedziczone wskazówka wcześniej otwartych plików. Ostatnie dwie reguły oznacza, że wskazówki w dalszej kolejności wyszukiwania można zastąpić wcześniej wskazówek dotyczących serwerów. Na przykład można zastąpić poprzedniego wskazówek dotyczących po utworzeniu pliku podpowiedzi w katalogu, który zawiera plik źródłowy.

Aby uzyskać sceny jak zbierane są wskazówki, zobacz [przykład](#example) sekcji.

### <a name="syntax"></a>Składnia

Tworzenie i usuwanie wskazówek dotyczących serwerów przy użyciu tej samej składni jako dyrektywy preprocesora do tworzenia i usuwania makra. W rzeczywistości analizy system używa preprocesora C/C++, można obliczyć wskazówek. Aby uzyskać więcej informacji na temat dyrektywy preprocesora, zobacz [#define — dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) i [#undef — dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Elementy składni tylko nietypowe są `@<`, `@=`, i `@>` ciągów zastępczych. Te ciągi określone zastąpienia pliku podpowiedzi są używane tylko w *mapy* makra. Mapa jest zestaw makra, które dotyczą danych, funkcji lub zdarzeń innych danych, funkcji lub procedury obsługi zdarzeń. Na przykład `MFC` utworzyć przy użyciu map [komunikatu mapy](../../mfc/reference/message-maps-mfc.md), i `ATL` utworzyć przy użyciu map [obiektu mapy](../../atl/reference/object-map-macros.md). Parametry określone zastąpienia pliku podpowiedzi oznaczyć początkowy, pośrednie i końcowy elementy mapy. Istotne jest tylko nazwa makra mapy. W związku z tym każdy ciąg zastępujący celowo powoduje ukrycie opcji wdrożenia makra.

Wskazówki należy użyć następującej składni:

|Składnia|Znaczenie|
|------------|-------------|
|`#define` *Wskazówka dotycząca nazwy* *ciąg zastępujący*<br /><br /> `#define` *Wskazówka dotycząca nazwy* `(` *parametru*,... `)` *ciąg zastępujący*|Dyrektywy preprocesora definiuje wskazówkę dotyczącą nowych lub ponownie wskazówką istniejących. Po dyrektywie preprocesora zamienia każde wystąpienie *nazw wskazówka* w kodzie źródłowym za pomocą *ciąg zastępujący*.<br /><br /> Druga forma składni definiuje funkcyjne wskazówkę. W przypadku wskazówką funkcyjne w kodzie źródłowym, preprocesor najpierw zamienia każde wystąpienie *parametru* w *ciąg zastępujący* za pomocą odnośnego argumentu w kodzie źródłowym, a następnie zastępuje *nazw wskazówka* z *ciąg zastępujący*.|
|`@<`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza początek zbiór elementów mapy.|
|`@=`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza element pośredni mapy. Mapy może mieć wielu elementów mapy.|
|`@>`|Określonego pliku podpowiedzi *ciąg zastępujący* oznacza koniec zbiór elementów mapy.|
|`#undef` *Wskazówka dotycząca nazwy*|Dyrektywy preprocesora, który służy do usuwania istniejących wskazówki. Nazwa wskazówka odbywa się przy *nazw wskazówka* identyfikatora.|
|`//` *Komentarz*|Jednowierszowego komentarza.|
|`/*` *Komentarz* `*/`|Komentarz wielowierszowy.|

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak wskazówki są zbierane z pliki wskazówki. Zatrzymaj pliki nie są używane w tym przykładzie.

Na ilustracji pokazano niektóre z katalogów fizycznych w programie Visual Studio C++ projektu. Istnieją pliki wskazówki w `vcpackages`, `Debug`, `A1`, i `A2` katalogów.

### <a name="hint-file-directories"></a>Wskazówka katalogi plików

![Typowe i projekt&#45;wskazówki określone katalogi plików. ](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Katalogi i zawartość pliku wskazówka

Ta lista zawiera katalogi, w tym projekcie, zawierających pliki wskazówki i zawartość tych plików wskazówki. Tylko niektóre z wielu wskazówki w `vcpackages` katalogu pliku podpowiedzi należą:

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

Poniższa tabela zawiera listę skuteczne wskazówek dotyczących plików źródłowych, w tym projekcie:

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

Te informacje dotyczą powyższej liście:

- Skuteczne wskazówki są z `vcpackages`, `Debug`, `A1`, i `A2` katalogów.

- **#Undef** dyrektywy w `Debug` pliku podpowiedzi usunięte `#define _In_` podpowiedzi w `vcpackages` pliku podpowiedzi katalogu.

- Pliku podpowiedzi w `A1` redefiniuje katalogu `START_NAMESPACE`.

- `#undef` Podpowiedzi w `A2` wskazówek dotyczących usunąć katalogu `OBRACE` i `CBRACE` w `Debug` pliku podpowiedzi katalogu.

## <a name="see-also"></a>Zobacz także

[Plik typy utworzone dla wizualizacji C++ projektów](file-types-created-for-visual-cpp-projects.md)<br>
[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef, dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)<br>

