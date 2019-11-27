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
ms.openlocfilehash: ca111fcb8b0fc511fda3bbb3a4769ebc9fdd28bc
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189008"
---
# <a name="hint-files"></a>Pliki wskazówki

*Plik podpowiedzi* zawiera makra, które w przeciwnym razie mogłyby spowodować pominięcie regionów kodu przez analizatora bazy C++ danych przeglądania. Po otwarciu projektu programu Visual Studio C++ parser analizuje kod w każdym pliku źródłowym w projekcie i kompiluje bazę danych o informacje o każdym identyfikatorze. IDE używa tych informacji do obsługi funkcji przeglądania kodu, takich jak przeglądarka **Widok klasy** i **pasek nawigacyjny**.

C++ Analizator przeszukiwania bazy danych jest analizatorem rozmytym, który może analizować duże ilości kodu w krótkim czasie. Jednym z powodów, że jest to możliwe, ponieważ pomija zawartość bloków. Na przykład tylko rejestruje lokalizację i parametry funkcji i ignoruje jej zawartość. Niektóre makra mogą powodować problemy z algorytmami heurystycznymi używanymi do określenia początku i końca bloku. Te problemy powodują, że regiony kodu mają być nieprawidłowo zarejestrowane.

Te pominięte regiony można zamanifestować na wiele sposobów:

- Brak typów i funkcji na **Widok klasy**, **Przejdź do** i **pasek nawigacyjny**

- Niepoprawne zakresy na **pasku nawigacyjnym**

- Sugestie dotyczące **tworzenia deklaracji/definicji** dla funkcji, które są już zdefiniowane

Plik wskazówki zawiera wskazówki dostosowywane przez użytkownika, które mają taką samą składnię jak definicjeC++ C/makra. Wizualizacja C++ zawiera wbudowany plik wskazówek, który jest wystarczający dla większości projektów. Można jednak utworzyć własne pliki wskazówek, aby poprawić parser przeznaczony dla projektu.

> [!IMPORTANT]
> W przypadku zmodyfikowania lub dodania pliku wskazówki należy wykonać dodatkowe czynności, aby zmiany zaczęły obowiązywać:
> - W wersjach wcześniejszych niż program Visual Studio 2017 w wersji 15,6: Usuń plik. sdf i/lub plik VC. DB w rozwiązaniu, aby uzyskać wszystkie zmiany.
> - W programie Visual Studio 2017 w wersji 15,6 lub nowszej: Zamknij i ponownie otwórz rozwiązanie po dodaniu nowych plików podpowiedzi.

## <a name="scenario"></a>Scenariusz

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez pliku podpowiedzi `Function` nie jest wyświetlana w **Widok klasy**, **Przejdź do** lub na **pasku nawigacyjnym**. Po dodaniu pliku wskazówki z tą definicją makra analizator składni teraz rozpoznaje i zastępuje makro `NOEXCEPT`, co umożliwia jego prawidłowe przeanalizowanie funkcji:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Makra zakłócające

Istnieją dwie kategorie makr, które zakłócają analizator składni:

- Makra, które hermetyzują słowa kluczowe, które umieszczają funkcję

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   W przypadku tych typów makr w pliku wskazówki jest wymagana tylko nazwa makra:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra zawierające nawiasy niezrównoważone

   ```cpp
   #define BEGIN {
   ```

   W przypadku tych typów makr nazwa makra i jego zawartość są wymagane w pliku wskazówki:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Obsługa edytora

Począwszy od programu Visual Studio 2017 w wersji 15,8, istnieje kilka funkcji umożliwiających zidentyfikowanie makr zakłócających:

- Makra, które znajdują się wewnątrz regionów pominiętych przez parser, są wyróżnione.

- Istnieje szybka akcja umożliwiająca utworzenie pliku podpowiedzi zawierającego wyróżnione makro lub istniejący plik podpowiedzi, aby dodać makro do pliku wskazówki.

![Wyróżnione makro.](media/hint-squiggle-and-actions.png "Podpowiedź i szybkie akcje")

Po wykonaniu jednej z szybkich akcji Analizator analizuje pliki, na które ma wpływ plik wskazówki.

Domyślnie makro problemu jest wyróżnione jako sugestia. Wyróżnienie można zmienić na coś bardziej zauważalnego, na przykład czerwonego lub zielonego. Użyj **makr w obszarze pominięte regiony przeglądania** w sekcji **kod** zygzaks w obszarze **Narzędzia** > **Opcje** > **edytorze tekstów** > **C/C++**  > **widoku**.

![Makra w pominiętych opcjach regionów przeglądania.](media/skipped-regions-squiggle-option.png "Opcja zygzakowata regionów pominiętych.")

## <a name="display-browsing-database-errors"></a>Wyświetl błędy przeglądania bazy danych

Polecenie menu **Wyświetl błędy bazy danych** **programu Project** > wyświetla wszystkie regiony, które nie zostały przeanalizowane w **Lista błędów**. Polecenie jest przeznaczone do usprawnienia tworzenia pliku wskazówki początkowej. Analizator nie może jednak stwierdzić, czy przyczyną błędu było makro zakłócające, dlatego należy ocenić każdy błąd. Uruchom polecenie **Wyświetl błędy bazy danych** i przejdź do każdego błędu, aby załadować odnośny plik w edytorze. Po załadowaniu pliku, jeśli którykolwiek z makr znajduje się w regionie, są one wyróżnione. Można wywołać szybkie akcje, aby dodać je do pliku wskazówki. Po aktualizacji pliku podpowiedzi Lista błędów zostanie automatycznie zaktualizowana. Alternatywnie, jeśli modyfikujesz plik wskazówki ręcznie, możesz użyć polecenia Skanuj ponownie **rozwiązanie** , aby wyzwolić aktualizację.

## <a name="architecture"></a>Architektura

Pliki wskazówek odnoszą się do katalogów fizycznych, a nie katalogów logicznych przedstawionych w **Eksplorator rozwiązań**. Nie trzeba dodawać pliku wskazówki do projektu, aby plik wskazówki miał efekt. System analizowania używa plików podpowiedzi tylko wtedy, gdy analizuje pliki źródłowe.

Każdy plik wskazówki ma nazwę **cpp. Wskazówka**. Wiele katalogów może zawierać plik wskazówki, ale tylko jeden plik podpowiedzi może wystąpić w określonym katalogu.

Na Twój projekt może mieć wpływ zero lub więcej plików podpowiedzi. W przypadku braku plików podpowiedzi system analizowania używa technik odzyskiwania błędów, aby zignorować nierozpoznawalny kod źródłowy. W przeciwnym razie system analizowania używa następującej strategii do znajdowania i zbierania wskazówek.

### <a name="search-order"></a>Kolejność wyszukiwania

System analizowania Przeszukuje katalogi pod kątem plików podpowiedzi w następującej kolejności.

- Katalog zawierający pakiet instalacyjny dla programu Visual C++ (**vcpackages**). Ten katalog zawiera wbudowaną wskazówkę opisującą symbole w często używanych plikach systemowych, takich jak **Windows. h**. W związku z tym projekt automatycznie dziedziczy większość wskazówek, których potrzebuje.

- Ścieżka z katalogu głównego pliku źródłowego do katalogu, który zawiera sam plik źródłowy. W typowym projekcie programu C++ Visual Studio katalog główny zawiera rozwiązanie lub plik projektu.

   Wyjątkiem od tej reguły jest, czy *plik zatrzymania* znajduje się w ścieżce do pliku źródłowego. Plik Stop to każdy plik o nazwie **cpp. Stop**. Plik Stop zapewnia dodatkową kontrolę nad kolejnością wyszukiwania. Zamiast rozpoczynać się od katalogu głównego, system analizowania wyszukuje z katalogu zawierającego plik zatrzymania do katalogu, który zawiera plik źródłowy. W typowym projekcie nie jest potrzebny plik Stop.

### <a name="hint-gathering"></a>Zbieranie wskazówek

Plik podpowiedzi zawiera zero lub więcej *wskazówek*. Wskazówka jest definiowana lub usuwana podobnie jak makro C/C++ . Oznacza to, że dyrektywa preprocesora `#define` tworzy lub ponownie definiuje wskazówkę, a dyrektywa `#undef` usuwa wskazówkę.

System analizowania otwiera każdy plik podpowiedzi w kolejności wyszukiwania opisanej wcześniej. Gromadzi wskazówki poszczególnych plików do zestawu *skutecznych wskazówek*, a następnie używa obowiązujących wskazówek do interpretowania identyfikatorów w kodzie.

System analizowania używa tych reguł do gromadzenia wskazówek:

- Jeśli nowa Wskazówka określa nazwę, która nie jest jeszcze zdefiniowana, Nowa Wskazówka dodaje nazwę do obowiązujących wskazówek.

- Jeśli nowa Wskazówka określa nazwę, która jest już zdefiniowana, Nowa Wskazówka ponownie definiuje istniejącą wskazówkę.

- Jeśli nową wskazówką jest dyrektywa `#undef`, która określa istniejącą skuteczną wskazówkę, Nowa Wskazówka Usuwa istniejącą wskazówkę.

Pierwsza reguła oznacza, że skuteczne wskazówki są dziedziczone z wcześniej otwartych plików wskazówek. Ostatnie dwie reguły oznaczają, że wskazówki w dalszej kolejności wyszukiwania mogą przesłonić wcześniejsze wskazówki. Na przykład można zastąpić wszystkie poprzednie wskazówki w przypadku utworzenia pliku podpowiedzi w katalogu, który zawiera plik źródłowy.

Aby poznać sposób, w jaki są zbierane wskazówki, zapoznaj się z sekcją [przykładową](#example) .

### <a name="syntax"></a>Składnia

Wskazówki można tworzyć i usuwać za pomocą tej samej składni co dyrektywy preprocesora do tworzenia i usuwania makr. W rzeczywistości system analizy używa języka C/C++ preprocesora do szacowania wskazówek. Aby uzyskać więcej informacji na temat dyrektyw preprocesora, zobacz [#define dyrektywie (c/C++)](../../preprocessor/hash-define-directive-c-cpp.md) i [#undef (c/C++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Jedyne nietypowe elementy składni to `@<`, `@=`i `@>` ciągi zamienne. Te wskazówki — ciągi zamienne charakterystyczne dla pliku są używane tylko w makrach *mapy* . Mapa to zestaw makr, które wiążą dane, funkcje lub zdarzenia z innymi danymi, funkcjami lub obsługą zdarzeń. Na przykład `MFC` używa map do tworzenia [map komunikatów](../../mfc/reference/message-maps-mfc.md), a `ATL` używa map do tworzenia [map obiektów](../../atl/reference/object-map-macros.md). Wskazówka-specyficzne dla pliku ciągi zamienne oznaczają początkowe, pośrednie i końcowe elementy mapy. Tylko nazwa makra mapy jest znacząca. W związku z tym każdy ciąg zamienny celowo ukrywa implementację makra.

Wskazówki używają następującej składni:

|Składnia|Znaczenie|
|------------|-------------|
|*wskazówka `#define` —* *ciąg zastępczy* nazwy<br /><br /> `#define` *wskazówki-nazwa* `(` *parametru*,...`)`*zastąpienie ciągu*|Dyrektywa preprocesora, która definiuje nową wskazówkę lub ponownie definiuje istniejącą wskazówkę. Po dyrektywie preprocesor zastępuje każde wystąpienie *nazwy wskazówki* w kodzie źródłowym *ciągiem zastępczym*.<br /><br /> Druga forma składni definiuje wskazówkę podobną do funkcji. Jeśli w kodzie źródłowym występuje Wskazówka przypominająca funkcję, preprocesor zastępuje każde wystąpienie *parametru* w *ciągu wymiany* z odpowiednim argumentem w kodzie źródłowym, a następnie zamienia *nazwę wskazówki* na *ciąg zastępczy*.|
|`@<`|Wskazówka — *ciąg zastępczy* określony dla pliku, który wskazuje początek zestawu elementów mapy.|
|`@=`|Wskazówka — *ciąg zastępczy* określony dla pliku, który wskazuje pośredni element mapy. Mapa może mieć wiele elementów mapy.|
|`@>`|Wskazówka — *ciąg zastępczy* określony dla pliku, który wskazuje koniec zestawu elementów mapy.|
|*wskazówka `#undef`-Name*|Dyrektywa preprocesora, która usuwa istniejącą wskazówkę. Nazwa wskazówki jest zapewniana przez identyfikator *nazwy wskazówki* .|
|*komentarz* `//`|Komentarz jednowierszowy.|
|`/*` `*/` *komentarzy*|Komentarz wielowierszowy.|

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak są gromadzone wskazówki z plików wskazówek. Pliki Stop nie są używane w tym przykładzie.

Na ilustracji przedstawiono niektóre katalogi fizyczne w projekcie programu Visual Studio C++ . Istnieją pliki podpowiedzi w katalogach `vcpackages`, `Debug`, `A1`i `A2`.

### <a name="hint-file-directories"></a>Podpowiedź katalogów plików

![Wspólne i charakterystyczne dla projektu&#45;katalogi plików podpowiedzi.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Katalog i zawartość pliku wskazówki

Ta lista zawiera katalogi w tym projekcie, które zawierają pliki podpowiedzi oraz zawartość tych plików wskazówek. Na liście poniżej przedstawiono tylko niektóre wskazówki dotyczące `vcpackages`:

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

### <a name="effective-hints"></a>Efektywne wskazówki

W tej tabeli wymieniono efektywne wskazówki dotyczące plików źródłowych w tym projekcie:

- Plik źródłowy: A1_A2_B. cpp

- Efektywne wskazówki:

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

Te informacje dotyczą powyższej listy:

- Efektywne wskazówki pochodzą z katalogów `vcpackages`, `Debug`, `A1`i `A2`.

- Dyrektywa **#undef** w pliku podpowiedzi `Debug` usunął wskazówkę `#define _In_` w pliku wskazówki dotyczącej katalogu `vcpackages`.

- Plik wskazówki w katalogu `A1` ponownie definiuje `START_NAMESPACE`.

- Wskazówka `#undef` w katalogu `A2` usunął wskazówki dotyczące `OBRACE` i `CBRACE` w pliku wskazówek dotyczących katalogu `Debug`.

## <a name="see-also"></a>Zobacz także

[Typy plików utworzone dla projektów programu C++ Visual Studio](file-types-created-for-visual-cpp-projects.md)<br>
[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef, dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)<br>

