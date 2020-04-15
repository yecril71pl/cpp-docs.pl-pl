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
ms.openlocfilehash: 8037cb8025cc85a8479528490e1512531cbcc035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322313"
---
# <a name="hint-files"></a>Pliki wskazówki

*Plik wskazówki* zawiera makra, które w przeciwnym razie spowodowałyby pominięcie regionów kodu przez analizator bazy danych przeglądania języka C++. Po otwarciu projektu Visual Studio C++ analizator analizuje kod w każdym pliku źródłowym w projekcie i tworzy bazę danych z informacjami o każdym identyfikatorze. IDE używa tych informacji do obsługi funkcji przeglądania kodu, takich jak **przeglądarka widok klasy** i **pasek nawigacyjny**.

Analizator bazy danych przeglądania języka C++ jest analizatorem rozmytym, który może analizować duże ilości kodu w krótkim czasie. Jednym z powodów, dla których jest szybki, jest to, że pomija zawartość bloków. Na przykład rejestruje tylko lokalizację i parametry funkcji i ignoruje jej zawartość. Niektóre makra mogą powodować problemy z heurystyką używaną do określenia początku i końca bloku. Te problemy powodują, że regiony kodu mają być rejestrowane nieprawidłowo.

Te pominięte regiony mogą objawiać się na wiele sposobów:

- Brakujące typy i funkcje w **widoku klasy,** przejdź do i **pasku** **nawigacyjnym**

- Nieprawidłowe zakresy na pasku **nawigacyjnym**

- Sugestie **tworzenia deklaracji/definicji** dla funkcji, które są już zdefiniowane

Plik wskazówki zawiera wskazówki, które można dostosowywać przez użytkownika, które mają taką samą składnię jak definicje makr C/C++. Visual C++ zawiera wbudowany plik wskazówek, który jest wystarczający dla większości projektów. Można jednak utworzyć własne pliki podpowiedzi, aby poprawić analizatora specjalnie dla projektu.

> [!IMPORTANT]
> Jeśli zmodyfikujesz lub dodasz plik podpowiedzi, musisz podjąć dodatkowe kroki, aby zmiany zostały wprowadzone:
>
> - W wersjach przed programem Visual Studio 2017 w wersji 15.6: Usuń plik sdf i/lub plik VC.db w rozwiązaniu dla wszystkich zmian.
> - W programie Visual Studio 2017 w wersji 15.6 i nowszych: Zamknij i ponownie otwórz rozwiązanie po dodaniu nowych plików wskazówek.

## <a name="scenario"></a>Scenariusz

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez pliku podpowiedzi `Function` nie jest widoczny w widoku **klasy**, Przejdź **do** lub pasku **nawigacyjnym**. Po dodaniu pliku podpowiedzi z tą definicją makra `NOEXCEPT` analizator teraz rozumie i zastępuje makro, co pozwala na poprawne analizowanie funkcji:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Destrukcyjne makra

Istnieją dwie kategorie makr, które zakłócają analizator:

- Makra hermetyzujące słowa kluczowe, które zdobią funkcję

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   W przypadku tych typów makr w pliku podpowiedzi wymagana jest tylko nazwa makra:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra zawierające niesymetryzowe nawiasy

   ```cpp
   #define BEGIN {
   ```

   W przypadku tych typów makr zarówno nazwa makra, jak i jego zawartość są wymagane w pliku podpowiedzi:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Obsługa edytora

Począwszy od programu Visual Studio 2017 w wersji 15.8 istnieje kilka funkcji umożliwiających identyfikację przełomowych makr:

- Wyróżniane są makra znajdujące się wewnątrz regionów pominiętych przez analizatora.

- Istnieje szybka akcja, aby utworzyć plik podpowiedzi, który zawiera podświetlone makro lub jeśli istnieje istniejący plik podpowiedzi, aby dodać makro do pliku podpowiedzi.

![Podświetlone makro.](media/hint-squiggle-and-actions.png "Podpowiedź squiggle i szybkie akcje")

Po wykonaniu jednej z szybkich akcji analizator ponownie analizuje pliki, których dotyczy plik podpowiedzi.

Domyślnie makro problemu jest wyróżnione jako sugestia. Podświetlenie można zmienić na coś bardziej zauważalnego, na przykład czerwoną lub zieloną faliskę. Użyj opcji **Makra w pominiętych regionach przeglądania** w sekcji **Squiggles kodu** w obszarze**Opcje** >  **narzędzi** > **Edytor** > tekstu**Widok C/C++.** > **View**

![Makra w opcji Pominięte regiony przeglądania.](media/skipped-regions-squiggle-option.png "Pominięte regiony squiggle opcji.")

## <a name="display-browsing-database-errors"></a>Wyświetlanie błędów przeglądania bazy danych

Polecenie Menu Błędy przeglądania bazy danych **w programie Project** > **Display** wyświetla wszystkie regiony, w których nie można przeanalizować na **liście błędów**. Polecenie ma usprawnić tworzenie początkowego pliku podpowiedzi. Jednak analizator nie może stwierdzić, czy przyczyną błędu było destrukcyjne makro, więc należy ocenić każdy błąd. Uruchom polecenie **Wyświetl błędy bazy danych przeglądania** i przejdź do każdego błędu, aby załadować plik, którego dotyczy problem w edytorze. Po załadowaniu pliku, jeśli makra znajdują się wewnątrz regionu, są one wyróżnione. Można wywołać szybkie akcje, aby dodać je do pliku podpowiedzi. Po aktualizacji pliku podpowiedzi lista błędów jest aktualizowana automatycznie. Alternatywnie, jeśli modyfikujesz plik podpowiedzi ręcznie, możesz użyć polecenia **Rescan Solution,** aby wyzwolić aktualizację.

## <a name="architecture"></a>Architektura

Pliki wskazówek odnoszą się do katalogów fizycznych, a nie katalogów logicznych wyświetlanych w **Eksploratorze rozwiązań**. Nie trzeba dodawać pliku podpowiedzi do projektu, aby plik podpowiedzi miał wpływ. System analizowania używa plików wskazówek tylko wtedy, gdy analizuje pliki źródłowe.

Każdy plik podpowiedzi nosi nazwę **cpp.hint**. Wiele katalogów może zawierać plik podpowiedzi, ale w określonym katalogu może wystąpić tylko jeden plik podpowiedzi.

Na projekt może mieć wpływ zero lub więcej plików podpowiedzi. Jeśli nie ma żadnych plików wskazówek, system analizowania używa technik odzyskiwania błędów, aby zignorować nieczytelny kod źródłowy. W przeciwnym razie system analizowania używa następującej strategii, aby znaleźć i zebrać wskazówki.

### <a name="search-order"></a>Kolejność wyszukiwania

System analizowania przeszukuje katalogi w poszukiwaniu plików podpowiedzi w następującej kolejności.

- Katalog zawierający pakiet instalacyjny dla programu Visual C++ (**vcpackages**). Ten katalog zawiera wbudowany plik podpowiedzi opisujący symbole w często używanych plikach systemowych, takich jak **windows.h**. W związku z tym projekt automatycznie dziedziczy większość wskazówek, które potrzebuje.

- Ścieżka z katalogu głównego pliku źródłowego do katalogu zawierającego sam plik źródłowy. W typowym projekcie Programu Visual Studio C++ katalog główny zawiera plik rozwiązania lub projektu.

   Wyjątkiem od tej reguły jest, jeśli *plik zatrzymania* znajduje się w ścieżce do pliku źródłowego. Plik zatrzymania to dowolny plik o nazwie **cpp.stop**. Plik zatrzymania zapewnia dodatkową kontrolę nad kolejnością wyszukiwania. Zamiast zaczynać od katalogu głównego, system analizowania przeszukuje katalog zawierający plik zatrzymania do katalogu zawierającego plik źródłowy. W typowym projekcie nie potrzebujesz pliku zatrzymania.

### <a name="hint-gathering"></a>Zbieranie podpowiedzi

Plik wskazówki zawiera zero lub więcej *wskazówek*. Wskazówka jest definiowana lub usuwana podobnie jak makro C/C++. Oznacza to, `#define` że dyrektywa preprocesora tworzy lub na `#undef` nowo definiuje wskazówkę, a dyrektywa usuwa wskazówkę.

System analizowania otwiera każdy plik podpowiedzi w opisanej wcześniej kolejności wyszukiwania. Gromadzi wskazówki każdego pliku w zestaw *skutecznych wskazówek,* a następnie używa skutecznych wskazówek do interpretacji identyfikatorów w kodzie.

System analizowania używa tych reguł do gromadzenia wskazówek:

- Jeśli nowa wskazówka określa nazwę, która nie jest jeszcze zdefiniowana, nowa wskazówka dodaje nazwę do skutecznych wskazówek.

- Jeśli nowa wskazówka określa nazwę, która jest już zdefiniowana, nowa wskazówka na nowo definiuje istniejącą wskazówkę.

- Jeśli nowa wskazówka `#undef` jest dyrektywa, która określa istniejącą wskazówkę skuteczne, nowa wskazówka usuwa istniejącą wskazówkę.

Pierwsza reguła oznacza, że skuteczne wskazówki są dziedziczone z wcześniej otwartych plików podpowiedzi. Dwie ostatnie reguły oznaczają, że wskazówki w dalszej kolejności wyszukiwania mogą zastąpić wcześniejsze wskazówki. Na przykład można zastąpić wszystkie poprzednie wskazówki, jeśli utworzysz plik wskazówki w katalogu zawierającym plik źródłowy.

Aby uzyskać przedstawienie sposobu zbierania wskazówek, zobacz [przykładową](#example) sekcję.

### <a name="syntax"></a>Składnia

Wskazówki można tworzyć i usuwać przy użyciu tej samej składni co dyrektywy preprocesora do tworzenia i usuwania makr. W rzeczywistości system analizowania używa preprocesora C/C++ do oceny wskazówek. Aby uzyskać więcej informacji na temat dyrektyw preprocesora, zobacz [#define dyrektywy (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) i [#undef directive (C/C++).](../../preprocessor/hash-undef-directive-c-cpp.md)

Jedynymi nietypowymi elementami `@<`składni są `@=`ciągi , i `@>` zastępcze. Te ciągi zastępcze specyficzne dla pliku wskazówki są używane tylko w makrach *map.* Mapa to zestaw makr, które odnoszą się do danych, funkcji lub zdarzeń do innych danych, funkcji lub programów obsługi zdarzeń. Na przykład `MFC` używa map do tworzenia `ATL` map [wiadomości](../../mfc/reference/message-maps-mfc.md)i używa map do tworzenia map [obiektów.](../../atl/reference/object-map-macros.md) Ciągi zastępowania specyficzne dla pliku wskazówki oznaczają początkowe, pośrednie i końcowe elementy mapy. Znaczenie makr mapy jest znacząca. W związku z tym każdy ciąg zastępczy celowo ukrywa implementację makra.

Wskazówki używają tej składni:

|Składnia|Znaczenie|
|------------|-------------|
|`#define`*ciąg zastępczy* *podpowiedzi*<br /><br /> `#define`*hint-name* `(` *parametr*, ... `)` *ciąg zastępczy*|Dyrektywa preprocesora, która definiuje nową wskazówkę lub na nowo definiuje istniejącą wskazówkę. Po dyrektywie preprocesor zastępuje każde wystąpienie *nazwy podpowiedzi* w kodzie źródłowym *ciągiem zastępczym.*<br /><br /> Drugi formularz składni definiuje wskazówkę podobną do funkcji. Jeśli wskazówka podobna do funkcji występuje w kodzie źródłowym, preprocesor najpierw zastępuje każde wystąpienie *parametru* w *replacement-string* odpowiednim argumentem w kodzie źródłowym, a następnie zastępuje *nazwę wskazówki* *ciągiem zastępczym*.|
|`@<`|Ciąg *zastępczy* specyficzny dla pliku wskazówki, który wskazuje początek zestawu elementów mapy.|
|`@=`|Ciąg *zastępczy* specyficzny dla pliku wskazówki, który wskazuje pośredni element mapy. Mapa może mieć wiele elementów mapy.|
|`@>`|Ciąg *zastępczy* specyficzny dla pliku wskazówki, który wskazuje koniec zestawu elementów mapy.|
|`#undef`*nazwa podpowiedzi*|Dyrektywa preprocesora, która usuwa istniejącą wskazówkę. Nazwa wskazówki jest dostarczana przez identyfikator *nazwy podpowiedzi.*|
|`//`*komentarz*|Komentarz jednowierszowy.|
|`/*`*komentarz*`*/`|Komentarz wielowierszowy.|

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak wskazówki są gromadzone z plików podpowiedzi. Zatrzymaj pliki nie są używane w tym przykładzie.

Ilustracja przedstawia niektóre katalogi fizyczne w projekcie Visual Studio C++. W katalogach znajdują `vcpackages` `Debug`się `A1`pliki `A2` podpowiedzi.

### <a name="hint-file-directories"></a>Katalogi plików podpowiedzi

![Typowe i&#45;określonych katalogów plików wskazówek.](media/hintfile.png "Plik hintfile")

### <a name="directories-and-hint-file-contents"></a>Katalogi i zawartość pliku wskazówki

Ta lista zawiera katalogi w tym projekcie, które zawierają pliki wskazówek, oraz zawartość tych plików wskazówek. Tylko niektóre z wielu wskazówek `vcpackages` w pliku podpowiedzi katalogu są wymienione:

- opakowania vc

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

W tej tabeli wymieniono skuteczne wskazówki dotyczące plików źródłowych w tym projekcie:

- Plik źródłowy: A1_A2_B.cpp

- Skuteczne wskazówki:

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

Uwagi te odnoszą się do powyższej listy:

- Skuteczne wskazówki są `vcpackages`z `Debug` `A1`, `A2` , i katalogów.

- Dyrektywa **#undef** w pliku `Debug` podpowiedzi `#define _In_` usunęła wskazówkę w pliku podpowiedzi `vcpackages` katalogu.

- Plik wskazówki `A1` w katalogu `START_NAMESPACE`na nowo definiuje plik .

- `#undef` Wskazówka w `A2` katalogu usunęła `OBRACE` wskazówki dotyczące i `CBRACE` w pliku podpowiedzi `Debug` katalogu.

## <a name="see-also"></a>Zobacz też

[Typy plików utworzone dla projektów programu Visual Studio C++](file-types-created-for-visual-cpp-projects.md)<br>
[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef — dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)<br>
