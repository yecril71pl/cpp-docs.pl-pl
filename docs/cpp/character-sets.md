---
title: Tokeny i zestawy znaków
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 1f6dbe2faa6348d61ec00b411cc35e8ef5ceb57a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301616"
---
# <a name="tokens-and-character-sets"></a>Tokeny i zestawy znaków

Tekst C++ programu składa się z tokenów i *białych znaków*. Token jest najmniejszym elementem C++ programu, który jest zrozumiały dla kompilatora. C++ Analizator rozpoznaje te rodzaje tokenów:

- [Słowa kluczowe](../cpp/keywords-cpp.md)
- [Identyfikatory](../cpp/identifiers-cpp.md)
- [Literały numeryczne, wartości logicznych i wskaźników](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [Literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md)
- [Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md)
- [Operatory](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [Znaki interpunkcyjne](../cpp/punctuators-cpp.md)

Tokeny są zwykle oddzielane *znakami odstępu*, co może być jedną lub większą liczbą:

- Wartości puste
- Karty poziome lub pionowe
- Nowe wiersze
- Źródła formularzy
- Komentarze

## <a name="basic-source-character-set"></a>Podstawowy zestaw znaków źródła

C++ Standard określa *podstawowy zestaw znaków źródła* , który może być używany w plikach źródłowych. Aby reprezentować znaki poza tym zestawem, można określić dodatkowe znaki przy użyciu *uniwersalnej nazwy znaków*. Implementacja MSVC zezwala na dodatkowe znaki. *Podstawowy zestaw znaków źródła* składa się z 96 znaków, które mogą być używane w plikach źródłowych. Ten zestaw zawiera znak odstępu, tabulator poziomy, tabulator pionowy, znaki kontrolne formularza i wiersz sterowania i ten zestaw znaków graficznych:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft Specific**

MSVC zawiera znak `$` jako element członkowski podstawowego zestawu znaków źródła. MSVC umożliwia również dodatkowy zestaw znaków, który ma być używany w plikach źródłowych, na podstawie kodowania plików. Domyślnie program Visual Studio przechowuje pliki źródłowe przy użyciu domyślnej strony kodowej. Gdy pliki źródłowe są zapisywane przy użyciu strony kodowej specyficznej dla ustawień regionalnych lub strony kodowej Unicode, MSVC umożliwia używanie dowolnych znaków tej strony kodowej w kodzie źródłowym, z wyjątkiem kodów kontroli niejawnie dozwolonych w podstawowym zestawie znaków źródła. Na przykład można umieścić znaki japońskie w komentarzach, identyfikatorach lub literałach ciągów, jeśli plik zostanie zapisany przy użyciu japońskiej strony kodowej. MSVC nie zezwala na sekwencje znaków, których nie można przetłumaczyć na prawidłowe znaki wielobajtowe lub punkty kodu Unicode. W zależności od opcji kompilatora nie wszystkie dozwolone znaki mogą pojawić się w identyfikatorach. Aby uzyskać więcej informacji, zobacz temat [Identyfikatory](../cpp/identifiers-cpp.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

### <a name="universal-character-names"></a>Uniwersalne nazwy znaków

Ponieważ C++ programy mogą używać dużo więcej znaków niż określone w podstawowym zestawie znaków źródłowych, można określić te znaki w przenośnej postaci przy użyciu *uniwersalnych nazw znaków*. Uniwersalna nazwa znaku składa się z sekwencji znaków, która reprezentuje punkt kodu Unicode.  Mają one dwie formy. Użyj `\UNNNNNNNN`, aby reprezentować punkt kodu Unicode w postaci U + NNNNNNNN, gdzie NNNNNNNN jest cyfrowym numerem punktu szesnastkowego. Użyj czterech cyfr `\uNNNN`, aby reprezentować punkt kodu Unicode w postaci U + 0000NNNN.

Uniwersalne nazwy znaków mogą być używane w identyfikatorach oraz w literałach ciągów i znakach. Nie można użyć uniwersalnej nazwy znaku do reprezentowania punktu kodu zastępczego w zakresie 0xD800-0xDFFF. Zamiast tego należy użyć żądanego punktu kodu; Kompilator automatycznie generuje wszystkie wymagane surogaty. Dodatkowe ograniczenia dotyczą uniwersalnych nazw znaków, które mogą być używane w identyfikatorach. Aby uzyskać więcej informacji, zobacz [identyfikatory](../cpp/identifiers-cpp.md) i [literały znaków i znaki](../cpp/string-and-character-literals-cpp.md).

**Microsoft Specific**

Kompilator firmy C++ Microsoft traktuje znak w formie uniwersalnej nazwy znaków i literału w formie zamiennej. Na przykład można zadeklarować identyfikator przy użyciu formularza uniwersalnej nazwy znaku i użyć go w postaci literału:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Format znaków rozszerzonych w Schowku systemu Windows jest specyficzny dla ustawień regionalnych aplikacji. Wycinanie i wklejanie tych znaków do kodu z innej aplikacji może spowodować nieoczekiwane kodowanie znaków. Może to spowodować analizowanie błędów bez widocznej przyczyny w kodzie. Zalecamy ustawienie kodowania pliku źródłowego na stronę kodową Unicode przed wklejeniem znaków rozszerzonych. Zalecamy również użycie edytora IME lub aplikacji mapy znaków do generowania znaków rozszerzonych.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

### <a name="execution-character-sets"></a>Zestawy znaków wykonywania

*Zestawy znaków wykonywania* reprezentują znaki i ciągi, które mogą być wyświetlane w skompilowanym programie. Te zestawy znaków składają się ze wszystkich znaków, które są dozwolone w pliku źródłowym, a także znaki kontrolne, które reprezentują alert, spację, znaki powrotu karetki i znak null. Zestaw znaków wykonywania ma reprezentację specyficzną dla ustawień regionalnych.
