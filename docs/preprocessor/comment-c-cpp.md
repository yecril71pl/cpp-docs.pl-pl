---
title: comment — Wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219094"
---
# <a name="comment-pragma"></a>comment — Wartość dyrektywy pragma

Umieszcza rekord komentarza w pliku obiektu lub pliku wykonywalnego.

## <a name="syntax"></a>Składnia

> **komentarz #pragma (** *Typ komentarza* [ **,** "*komentarz-ciąg*"] **)**

## <a name="remarks"></a>Uwagi

*Typ komentarza* to jeden ze wstępnie zdefiniowanych identyfikatorów, opisany poniżej, który określa typ rekordu komentarza. Opcjonalny *ciąg komentarza* jest literałem ciągu, która zawiera dodatkowe informacje dla niektórych typów komentarzy. Ponieważ *komentarz-ciąg* jest literałem ciągu, przestrzega wszystkich reguł dla literałów ciągów odnoszących się do znaków ucieczki, osadzonych znaków cudzysłowu (`"`) i łączenia.

### <a name="compiler"></a>— kompilator

Umieszcza nazwę i numer wersji kompilatora w pliku obiektu. Ten rekord komentarza jest ignorowany przez konsolidator. Jeśli podasz parametr *ciągu komentarza* dla tego typu rekordu, kompilator generuje ostrzeżenie.

### <a name="lib"></a>lib

Umieszcza rekord wyszukiwania biblioteki w pliku obiektu. Do tego typu komentarza musi być dołączony parametr *Comment-String* zawierający nazwę (a także ścieżkę) biblioteki, która ma być wyszukiwana przez konsolidator. Nazwa biblioteki jest zgodna z domyślnymi rekordami wyszukiwania w pliku obiektu; Konsolidator wyszukuje tę bibliotekę tak, jakby była nazywana w wierszu polecenia, pod warunkiem, że biblioteka nie została określona za pomocą [/NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). Można umieścić wiele rekordów wyszukiwania biblioteki w tym samym pliku źródłowym; Każdy rekord pojawia się w pliku obiektu w takiej samej kolejności, w jakiej występuje w pliku źródłowym.

Jeśli kolejność biblioteki domyślnej i dodanej biblioteki jest ważna, kompilowanie za pomocą przełącznika [/zl](../build/reference/zl-omit-default-library-name.md) uniemożliwi umieszczenie domyślnej nazwy biblioteki w module obiektu. Druga dyrektywa pragma komentarza następnie może służyć do wstawienia nazwy biblioteki domyślnej po dodanej bibliotece. Biblioteki wymienione w tych pragmach będą wyświetlane w module obiektów w tej samej kolejności, w której znajdują się w kodzie źródłowym.

### <a name="linker"></a>konsolidator

Umieszcza w pliku obiektu [opcję konsolidatora](../build/reference/linker-options.md) . Można użyć tego typu komentarza, aby określić opcję konsolidatora zamiast przekazywać ją do wiersza polecenia lub określić ją w środowisku deweloperskim. Na przykład można określić opcję/include, aby wymusić włączenie symbolu:

```C
#pragma comment(linker, "/include:__mySymbol")
```

Tylko następujące opcje konsolidatora (*komentarz-typ*) są dostępne do przesłania do identyfikatora konsolidatora:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>użytkownik

Umieszcza ogólny komentarz w pliku obiektu. Parametr *Comment-String* zawiera tekst komentarza. Ten rekord komentarza jest ignorowany przez konsolidator.

## <a name="examples"></a>Przykłady

Poniższe dyrektywy pragma powodują, że konsolidator wyszuka EMAPI. Biblioteka LIB podczas konsolidacji. Konsolidator przeszukuje najpierw w bieżącym katalogu roboczym, a następnie w ścieżce określonej w zmiennej środowiskowej LIB.

```C
#pragma comment( lib, "emapi" )
```

Poniższe dyrektywy pragma powodują, że kompilator umieści nazwę i numer wersji kompilatora w pliku obiektu:

```C
#pragma comment( compiler )
```

W przypadku komentarzy, które pobierają parametr *komentarza-ciąg* , można użyć makra w dowolnym miejscu, w którym można użyć literału ciągu, pod warunkiem, że makro zostanie rozwinięte do literału ciągu. Można również połączyć dowolną kombinację literałów ciągów i makr, które rozszerzają się do literałów ciągów. Na przykład następująca instrukcja jest akceptowalna:

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
