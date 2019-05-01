---
title: komentarz (C/C++)
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: fb9bfef2ae751529b8424143cde020e78f17ec72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403480"
---
# <a name="comment-cc"></a>komentarz (C/C++)

Umieszcza rekord komentarza do obiektu pliku lub pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
#pragma comment( comment-type [,"commentstring"] )
```

## <a name="remarks"></a>Uwagi

*Typ komentarza* jest jednym z wstępnie zdefiniowane identyfikatory, opisane poniżej, który określa typ rekordu komentarz. Opcjonalny *commentstring* jest ciągiem literału, który zawiera dodatkowe informacje dla niektórych typów komentarz. Ponieważ *commentstring* jest ciągiem literału, jego przestrzegają wszystkie reguły dla literałów ciągów w odniesieniu do znaki ucieczki i osadzone znaki cudzysłowu (`"`) i łączenia.

### <a name="compiler"></a> — kompilator

Umieszcza nazwę oraz numer wersji kompilatora w pliku obiektu. Ten rekord komentarza jest ignorowane przez konsolidator. Jeśli podasz *commentstring* parametr dla tego typu rekordu, kompilator generuje ostrzeżenie.

### <a name="exestr"></a>exestr

Umieszcza *commentstring* w pliku obiektu. W czasie połączenia ten ciąg jest umieszczany w pliku wykonywalnym. Ciąg nie jest ładowany do pamięci podczas ładowania pliku wykonywalnego; jednak można je znaleźć przy użyciu programu, który umożliwia znalezienie drukowalnych ciągów w plikach. Jednym z zastosowań dla tego typu rekordu komentarza jest osadzanie numer wersji lub podobne informacje w pliku wykonywalnym.

`exestr` jest przestarzały i zostanie usunięta w przyszłej wersji; konsolidator nie przetwarza rekordów komentarz.

### <a name="lib"></a>lib

Umieszcza rekord wyszukiwania biblioteki w pliku obiektu. Ten typ komentarza musi towarzyszyć *commentstring* parametr zawierający nazwę (i prawdopodobnie ścieżka) biblioteki, który chcesz, aby konsolidator, aby wyszukać. Wyszukiwania biblioteki domyślne rekordy w pliku obiektu; następuje nazwa biblioteki konsolidator szuka tę bibliotekę tak, jakby było nazwał ją w wierszu polecenia pod warunkiem, że biblioteka nie zostanie określony z [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md). Wiele rekordów wyszukiwania biblioteki można umieścić w tym samym pliku źródłowym; Każdy rekord pojawi się w pliku obiektu w tej samej kolejności, napotkała w pliku źródłowym.

Jeśli ważna jest kolejność domyślna biblioteka oraz dodano bibliotekę, kompilowania za pomocą [/Zl](../build/reference/zl-omit-default-library-name.md) przełącznika uniemożliwi umieszczonych w module obiektu domyślną nazwę biblioteki. Drugi dyrektywy komentarza następnie może służyć do wstawiania nazwę domyślnej biblioteki po dodano biblioteki. Biblioteki, na liście za pomocą tych pragmy pojawi się w module obiektów w tej samej kolejności, które zostały znalezione w kodzie źródłowym.

### <a name="linker"></a>konsolidator

Umieszcza [— opcja konsolidatora](../build/reference/linker-options.md) w pliku obiektu. Typ komentarza umożliwia określanie opcji konsolidatora zamiast przekazywania go do wiersza polecenia lub określając jej w środowisku programistycznym. Na przykład można określić / include opcję, aby wymusić włączenia symbol:

```
#pragma comment(linker, "/include:__mySymbol")
```

Jedynie następujące elementy (*typ komentarza*) są dostępne do przekazania do identyfikatora konsolidatora opcje konsolidatora:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/ MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/ SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>użytkownik

Umieszcza ogólny komentarz w pliku obiektu. *Commentstring* parametr zawiera tekst komentarza. Ten rekord komentarza jest ignorowane przez konsolidator.

Następujące pragmy powoduje, że konsolidator, aby wyszukać EMAPI. Biblioteki LIB podczas łączenia. Konsolidator szuka najpierw w bieżącym katalogu roboczym, a następnie w ścieżce określonej w zmiennej środowiskowej LIB.

```
#pragma comment( lib, "emapi" )
```

Następujące pragmy powoduje, że kompilator umieszcza nazwę oraz numer wersji kompilatora w pliku obiektu:

```
#pragma comment( compiler )
```

> [!NOTE]
> Dla komentarzy o *commentstring* parametru, można użyć makra w dowolnym miejscu, gdzie należy użyć literału ciągu, pod warunkiem, że makro rozszerza się do literału ciągu. Można również łączyć ze sobą dowolną kombinację literały ciągów i makra, pozwalające na rozszerzenie do literałów ciągu. Na przykład następująca instrukcja jest dopuszczalne:

```
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)