# <a name="metadata-and-markdown-template"></a>Metadane i szablonu języka znaczników Markdown

Ten szablon dokumentacji core zawiera przykłady składni języka znaczników Markdown, a także wskazówki dotyczące konfiguracji metadanych. Aby uzyskać najwięcej z nich, możesz wyświetlić obie [pierwotne języka znaczników Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) i [renderowany widok](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (na przykład pierwotne języka znaczników Markdown przedstawiono bloku metadanych, a nie w widoku renderowanym).

Podczas tworzenia pliku Markdown należy skopiować ten szablon do nowego pliku, wypełnij metadanych jako opisany poniżej, ustawić nagłówek H1 powyżej jako tytuł artykułu i usunąć zawartość.

## <a name="metadata"></a>Metadane

Pełen blok metadanych jest powyżej (w [pierwotne języka znaczników Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), są one podzielone na pola wymagane i opcjonalne pola. Ważne uwagi:

- Możesz **musi** miejsca między dwukropek (:) i wartość dla elementu metadanych.
- Jeśli opcjonalny element metadanych nie ma wartości, komentarzy, poprzedzając symbolem # lub usuń go (nie należy pozostawiać pustego elementu ani używać "d"); Jeśli dodajesz wartość do elementu, który zostało oznaczone jako komentarz, należy usunąć #.
- Dwukropki w wartości (na przykład tytuł) przerwanie analizatora składni metadanych. W takim przypadku należy ująć tytuł przy użyciu podwójnych cudzysłowów (na przykład `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- **Tytuł**: ten tytuł pojawi się w wynikach wyszukiwarki. Możesz również dodać potoku (|), a następnie według nazwy produktu (na przykład `title: Developing Libraries with Cross Platform Tools | .NET Core`). Tytuł nie musi być taka sama jak tytuł w nagłówku H1 i powinien on zawierać 65 znaków lub mniej (łącznie z | NAZWA PRODUKTU).
- **Autor**, **Menedżera**, **ms.reviewer**: powinna zawierać pola Autor **nazwę użytkownika usługi GitHub** autora, a nie jego alias.  Pola "manager" i "ms.reviewer", z drugiej strony, powinny zawierać aliasy firmy Microsoft. Wartość MS.Reviewer Określa nazwę PM dev skojarzone z artykułu lub funkcji.
- **MS.devlang** definiuje technologii. Niektóre obsługiwane wartości to: `dotnet`, `cpp`, `csharp`, `fsharp`, `vb` i `xml`.
- **MS.AssetID**: jest to identyfikator GUID artykułu, który jest używany do wewnętrznego śledzenia celów takich jak analizy biznesowej (BI). Podczas tworzenia nowego pliku Markdown, można uzyskać identyfikatora GUID z [Online GUID Generator](https://www.guidgenerator.com/).

## <a name="basic-markdown-gfm-and-special-characters"></a>Podstawowe języka znaczników Markdown, GFM i znaki specjalne

Wszystkie podstawowe i GitHub Flavored Markdown (GFM) jest obsługiwana. Aby uzyskać więcej informacji na ten temat zobacz:

- [Podstawowa składnia języka Markdown](https://daringfireball.net/projects/markdown/syntax)
- [Dokumentacja GFM](https://guides.github.com/features/mastering-markdown)

Markdown używa znaków specjalnych, takich jak \*, \`, i \# formatowania. Jeśli chcesz uwzględnić jedną z następujących znaków we własnych Treściach, wykonaj jedną z następujących czynności:

- Umieść ukośnik odwrotny przed znak specjalny "przed nimi znak ucieczki" (na przykład `\*` dla \*)
- Użyj [kodu jednostki HTML](https://www.ascii.cl/htmlcodes.htm) znak (na przykład `&#42;` dla &#42;).

## <a name="markdown-editing-tools"></a>Narzędzia do edycji języka markdown

Możesz użyć [programu Visual Studio Code](https://code.visualstudio.com/) do edycji dokumentów języka znaczników Markdown. Program VS Code zawiera wiele przydatne rozszerzenia języka Markdown, takie jak:

- [docs markdown](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-markdown) przez firmę Microsoft
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)

## <a name="file-name"></a>Nazwa pliku

Nazwy plików używają następujących reguł:

- Zawierać tylko małe litery, cyfry i łączniki.
- Bez spacji i znaków interpunkcyjnych. Używać łączników do oddzielania wyrazy i liczby w nazwie pliku.
- Użyj akcji konkretnych czasowników oznaczających, takie jak tworzenie, kupić, kompilacji, rozwiązywanie problemów. Bez wyrazów - ing.
- Nie dołączaj bez krótkich wyrazów — oraz, in, "or" itp.
- Musi być w języku znaczników Markdown i rozszerzenie pliku MD.
- Zachowaj względnie krótkich nazw plików. Są one częścią adresu URL dla artykułów.  

## <a name="headings"></a>Nagłówki

Stosowanie stylu zdania liter. Zawsze wielką literą:

- Pierwszy wyraz nagłówka.
- Word, zgodnie z dwukropkiem w nagłówku lub tytuł (na przykład "porady: Sortowanie tablicy").

Nagłówki, które ma być przeprowadzane przy użyciu stylu atx, oznacza to, znaki 1 – 6 wyznaczania wartości skrótu (#) na początku wiersza do wskazania nagłówek, odpowiadający poziomów nagłówków HTML H1 do H6. Przykłady nagłówków pierwszego i drugiego poziomu są używane powyżej.

Brak **musi** można tylko jeden nagłówek pierwszego stopnia (H1) w temacie, która będzie wyświetlana jako tytuł na stronie.

Jeśli nagłówek kończy `#` znaków, należy dodać dodatkowy `#` znaków w celu w kolejności tytułu zapewnić prawidłowe renderowanie. Na przykład `# Async Programming in F# #`.

Zawsze powinien istnieć jeden pusty wiersz przed i po nagłówku (z wyjątkiem pierwszego poziomu nagłówków).

Drugiego stopnia spowodują wygenerowanie na stronie spisu treści, która pojawia się w sekcji "w tym artykule" pod tytułem strony.

```markdown
### Third-level heading

#### Fourth-level heading

##### Fifth level heading

###### Sixth-level heading
```

## <a name="text-styling"></a>Style tekstu

*Kursywa*  
Na użytek generowane przez użytkownika nazwy plików, folderów i ścieżki (w przypadku długich elementów, podzielić na własnej linii); nowe warunki; nazwy parametrów; wartości wprowadzone przez użytkownika. adresy URL i (Jeśli nie są renderowane jako linki, co jest ustawieniem domyślnym).

**Bold**  
Użyj do elementów interfejsu użytkownika i słowa kluczowe języka.

## <a name="links"></a>Łącza

### <a name="internal-links"></a>Łączy wewnętrznych

Aby utworzyć link do nagłówka w tym samym pliku Markdown (znany także jako linki kotwiczące), należy sprawdzić identyfikator nagłówka, w którym próbujesz się połączyć. Aby upewnić się, identyfikator, Wyświetl źródło renderowanych artykułu, wyszukaj identyfikator nagłówka (na przykład `id="blockquote"`) i Połącz przy użyciu # + identyfikator (na przykład `#blockquote`).
Identyfikator jest generowane automatycznie na podstawie tekstu nagłówka. Tak, na przykład, biorąc pod uwagę unikatowy sekcję o nazwie `## Step 2`, identyfikator wyglądałoby następująco `id="step-2"`.

- Przykład: [rozdział 1](#chapter-1)

Aby utworzyć link do pliku Markdown, w tym samym repozytorium, użyj [linków względnych](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), łącznie z "MD" na końcu nazwy pliku.

- Przykład: [pliku Readme](../readme.md)
- Przykład: [.NET — Zapraszamy](../docs/welcome.md)

Aby utworzyć link do nagłówka w pliku Markdown w tym samym repozytorium, użyj względny + łączenie hasztagiem.

- Przykład: [społeczności platformy .NET](../docs/welcome.md#community)

### <a name="docs-links"></a>Dokumentacja łącza

Aby utworzyć link do pliku w repozytorium innego Docs, należy użyć względny adres URL witryny docs.microsoft.com jako łącza. Nie dołączaj sufiks MD.

- Przykład: [dokumentacji Universal Windows Platform](/windows/uwp)

### <a name="external-links"></a>Linki zewnętrzne

Aby utworzyć link do zewnętrznego pliku, należy użyć pełnego adresu URL jako łącza. Użyj adresu URL protokołu HTTPS, jeśli ma to zastosowanie.

- Przykład: [GitHub](https://www.github.com)

Jeśli w pliku Markdown występuje adres URL, zostanie on przekształcony w łączem.

- Przykład: https://www.github.com

### <a name="links-to-apis"></a>Linki do interfejsów API

System kompilacji ma niektórych rozszerzeń, które pozwalają połączyć interfejsów API platformy .NET Core, bez konieczności skorzystania z linków zewnętrznych.  
Podczas łączenia z interfejsu API, używając jego identyfikatora unikatowego (UID), który został wygenerowany automatycznie z kodu źródłowego.

Można użyć jednej z następującej składni:

1. Link języka markdown: `[link_text](xref:UID)`
2. Link automatyczny: `<xref:UID>`
3. Skrócone formy: `@UID`

- Przykład: `@System.String`
- Przykład: `[String class](xref:System.String)`

Aby uzyskać więcej informacji na temat tej notacji, zobacz [przy użyciu odsyłacz](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).

> W tej chwili, jest łatwy sposób znajdowania identyfikatorów UID. Najlepszym sposobem znalezienia identyfikatora UID dla interfejsu API jest do wyszukania w tym repozytorium: [docascode/coreapi](https://github.com/docascode/coreapi). Pracujemy nad o lepszym systemem w przyszłości.

Po identyfikatorze UID zawiera znaki specjalne \` lub \#, wartość UID musi być zakodowany jako % 60 i % 23 odpowiednio tak jak w poniższych przykładach kodu HTML:
- Przykład: @System.Threading.Tasks.Task \`1 staje się `@System.Threading.Tasks.Task%601`
- Przykład: @System.Exception.\# ctor staje się `@System.Exception.%23ctor`

## <a name="lists"></a>Listy

Listy powinna być otoczona pustych wierszy.

### <a name="ordered-lists"></a>Listy uporządkowane

1. Ten
1. jest
1. Usługi
1. Uporządkowane
1. Lista

#### <a name="ordered-list-with-an-embedded-list"></a>Lista uporządkowana z osadzoną listą

1. Tutaj
1. jest dostępna
1. Usługi
1. Osadzony
    1. Julia
    1. Romeo
1. uporządkowany
1. list

### <a name="unordered-lists"></a>Listy nieuporządkowane

- Ten
- is
- a
- punktowana
- list

#### <a name="unordered-list-with-an-embedded-list"></a>Lista nieuporządkowana z osadzoną listą

- Ten
- punktowana
- list
    - Rozalina
    - Merkucjo
- zawiera  
- Inne
    1. Tybalt
    1. Marta
- listy

## <a name="horizontal-rule"></a>Linia pozioma

___

## <a name="tables"></a>Tabele

| Tabele        | Czy           | chłodna  |
| ------------- |:-------------:| -----:|
| Kolumna 3 jest      | wyrównany do prawej | $1600 |
| Kolumna 2 jest      | wyśrodkowany      |   $12 |
| Kolumna 1 jest domyślnie | wyrównane do lewej     |    $1 |

Możesz użyć [narzędzia generator tabel Markdown](https://www.tablesgenerator.com/markdown_tables) ułatwiające, co ułatwi ich tworzenia. Zobacz też [narzędzia do edycji języka Markdown](#markdown-editing-tools).

## <a name="code"></a>Kod

Najlepszym sposobem, aby uwzględnić kod jest dołączaj fragmenty kodu z próbki pracy. Utwórz swój przykład, postępując zgodnie z instrukcjami w [mającym swój wkład przewodnik](../CONTRIBUTING.md#contributing-to-samples).

Może zawierać kod przy użyciu obejmują składni:

```markdown
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

Przykład powyżej przedstawiono C# składni, ale inne języki są obsługiwane.
Użyj `code-fsharp` dla F# przykłady; użyj `code-vbnet` dla przykładów kodu języka Visual Basic.
Inne języki, które są obsługiwane są:

- C++: `code-cpp`
- HTML: `code-html`
- JavaScript: `code-javascript`
- Program PowerShell: `code-ps`
- SQL: `code-sql`
- KOD XML: `code-xml`

Tekst, umieść dla `<title>` jest wyświetlany jako przerzucania na tekst. `<pathToFile>` Jest ścieżka do pliku źródłowego. `<RegionName>` Powinny być region, w kodzie źródłowym, które mają zostać uwzględnione. Użyj `#region` i `#endregion` preprocesora składnię, aby określić region kodu do uwzględnienia.

W przypadkach, w których regionach nie działają można określić początek i koniec okresu fragment kodu przy użyciu nazwa elementu XML w pojedynczym wierszu komentarza. Na przykład można napisać to C#:

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

W innych językach należy użyć składni komentarzy dla tego języka.

Na koniec można użyć numery wierszy: `#L1-L10` obejmuje wiersze od 1 do 10. Będziemy zniechęcać numery wierszy, ponieważ są one bardzo kruchy.

Dołączenie fragmentów z pełną programy gwarantuje, że cały kod jest uruchamiany w naszym systemie ciągłej integracji (CI). Jednak jeśli zachodzi potrzeba Pokaż coś, że przyczyny kompilacji błędy czasu lub środowiska uruchomieniowego, można użyć bloków kodu w tekście.

### <a name="inline-code-blocks-with-language-identifier"></a>Wbudowane bloki kodu przy użyciu identyfikatora języka

Użyj trzy znaki grawisu (\`\`\`) + Identyfikatora języka, aby zastosować kolor specyficzny dla języka programowania do bloku kodu. Oto Pełna lista [identyfikatory języków GFM](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

#### <a name="c"></a>C\#

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Blok kodu ogólnego

Użyj trzy znaki grawisu (&#96;&#96;&#96;) kodowania blok kodu ogólnego.

> Zalecanym podejściem jest używać bloków kodu z identyfikatorów języka, zgodnie z opisem w poprzedniej sekcji do upewnij się, poprawna składnia wyróżniania w witrynie dokumentacji. Użyj kodu ogólnego bloki tylko wtedy, gdy jest to konieczne.

```javascript
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>Wbudowany kod

Użyj grawisu (&#96;) dla `inline code`. Na użytek kodu wbudowanego polecenia wiersza polecenia, nazwy tabel i kolumn baz danych i wyrażeń języka i nazwy funkcji.

## <a name="blockquotes"></a>Cytaty

> Susza trwała już dziesięć milionów lat. i reign z panowanie olbrzymich jaszczurów dawno dobiegło. W tym miejscu na geograficznej mierzonej w kontynencie, który będzie jeden dzień będzie znany jako Afryka, gruntownie istnienie doszła do nowego coraz bardziej zaciekła walka o kontynencie, a kiedyś nie zostało jeszcze toczyła się. W tej jałowej szybkim i dzikim ziemi tylko mały lub swift ostrą można tacy mogli liczyć lub nawet nadzieję, że umożliwiającą przetrwanie.

## <a name="images"></a>Obrazy

### <a name="static-image-or-animated-gif"></a>Obraz statyczny lub animowany plik gif

![to jest tekst alternatywny](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Obraz połączony

[![tekst alternatywny połączonego obrazu](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>Wideo

### <a name="channel-9"></a>Witryna Channel 9

[![Ostermana Larry'ego — jego jeden interakcji z Billa Gatesa (przez stos sieciowy systemu DOS)](https://sec.ch9.ms/ch9/caf5/f8657a22-5b83-47a3-9748-4c1be9fecaf5/Larry-Osterman-His-one-interaction-with-Bill-Gate_960.jpg)
](https://channel9.msdn.com/Blogs/TheChannel9Team/Larry-Osterman-His-one-interaction-with-Bill-Gates-over-DOS-networking-stack)

### <a name="youtube"></a>YouTube

[![Na platformie .NET 2/4/2016 - Scottem Hunterem](https://img.youtube.com/vi/g2a4W6Q7aRw/0.jpg)
](https://www.youtube.com/watch?v=g2a4W6Q7aRw)

## <a name="docsmicrosoft-extensions"></a>rozszerzenia docs.Microsoft

docs.Microsoft oferuje kilka dodatkowych rozszerzeń GitHub Flavored Markdown. 

### <a name="alerts"></a>Alerty

Należy użyć następujących stylów alertu, dzięki czemu są one renderowane przy użyciu właściwego stylu w witrynie dokumentacji. Jednakże aparat renderowania w serwisie GitHub nie odróżnić je.

#### <a name="note"></a>Uwaga

> [!NOTE]
> To jest Uwaga

#### <a name="warning"></a>Ostrzeżenie

> [!WARNING]
> To jest ostrzeżenie

#### <a name="tip"></a>Porada

> [!TIP]
> To jest porada

#### <a name="important"></a>Ważne

> [!IMPORTANT]
> Jest to ważne

Będzie renderowany przez ich następująco: ![Alert style](../images/alerts.png)

### <a name="buttons"></a>Przyciski

> [!div class="button"]
[linki przycisków](../docs/core/index.md)

Możesz zobaczyć przykład przycisków w akcji w [dokumentacja usługi Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-enroll-devices). 

### <a name="selectors"></a>Selektory

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

Możesz zobaczyć przykład selektorów w akcji w [dokumentacja usługi Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps).

### <a name="step-by-steps"></a>Krok przez kroki

>[!div class="step-by-step"]
[Wstępnie](../docs/csharp/expression-trees-interpreting.md)
[dalej](../docs/csharp/expression-trees-translating.md)

Możesz zobaczyć przykład krok przez kroki w akcji w [dokumentacja usługi Advanced Threat Analytics](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step2).
