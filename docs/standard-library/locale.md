---
title: '&lt;ustawienie&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: ae008ef45e8a6bb57505432f2c931a768d4c8ea4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224802"
---
# <a name="ltlocalegt"></a>&lt;ustawienie&gt;

Definiuje szablony klas i funkcje, które mogą być używane przez programy C++ do hermetyzacji i manipulowania różnymi konwencjami kulturowymi dotyczącymi reprezentacji i formatowania danych liczbowych, pieniężnych i kalendarzowych, w tym do obsługi funkcji wielojęzycznych klasyfikacji znaków i sortowania ciągów.

## <a name="syntax"></a>Składnia

```cpp
#include <locale>
```

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Sprawdza, czy określony zestaw reguł jest przechowywany w określonych ustawieniach regionalnych.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym czy liczbowym.|
|[isalpha](../standard-library/locale-functions.md#isalpha)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem kontrolnym.|
|[IsDigit](../standard-library/locale-functions.md#isdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem liczbowym.|
|[isgraf](../standard-library/locale-functions.md#isgraph)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.|
|[IsLower](../standard-library/locale-functions.md#islower)|Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.|
|[isprint](../standard-library/locale-functions.md#isprint)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.|
|[isspace](../standard-library/locale-functions.md#isspace)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.|
|[IsUpper](../standard-library/locale-functions.md#isupper)|Sprawdza, czy element w ustawieniach regionalnych jest pisany wielkimi literami.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Konwertuje znak do małej litery.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Konwertuje znak do wielkiej litery.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Szablon klasy, który zawiera zestaw reguł służący do konwersji między wewnętrznymi i zewnętrznymi kodowaniem znaków.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Klasa bazowa dla klasy codecvt, która jest używana do definiowania typu wyliczenia, który jest określany jako `result` , używany jako zwracany typ dla funkcji składowych aspektu, aby wskazać wynik konwersji.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczące konwersji.|
|[sortowan](../standard-library/collate-class.md)|Szablon klasy sortowania, który zawiera zestaw reguł, który obsługuje konwencje sortowania ciągów.|
|[collate_byname](../standard-library/collate-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł sortowania dla danego ustawienia regionalnego, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących Konwencji sortowania ciągów.|
|[CType](../standard-library/ctype-class.md)|Szablon klasy, który udostępnia zestaw reguł, który jest używany do klasyfikowania znaków, konwersji z wielkich i małych liter oraz między natywnym zestawem znaków i zestawem używanym przez ustawienia regionalne.|
|[CType\<char>](../standard-library/ctype-char-class.md)|Klasa, która jest jawną specjalizacją szablonu klasy `ctype<CharType>` do wpisywania **`char`** opisującą obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu scharakteryzowania różnych właściwości znaku typu **`char`** .|
|[ctype_base](../standard-library/ctype-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł CType dla danego ustawienia regionalnego, co umożliwia klasyfikację znaków i konwersję znaków między zestawami znaków w przypadku i natywnym i lokalnym.|
|[ustawienie](../standard-library/locale-class.md)|Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.|
|[komunikaty](../standard-library/messages-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu pobrania zlokalizowanych komunikatów z katalogu międzynarodowych komunikatów dla danego ustawienia regionalnego.|
|[messages_base](../standard-library/messages-base-class.md)|Klasa bazowa opisująca **`int`** Typ wykazu komunikatów.|
|[messages_byname](../standard-library/messages-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw aspektów komunikatów dla danego ustawienia regionalnego, umożliwiając pobieranie zlokalizowanych komunikatów.|
|[money_base](../standard-library/money-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[money_get](../standard-library/money-get-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości pieniężne.|
|[money_put](../standard-library/money-put-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości pieniężnych na sekwencje typu **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Szablon klasy, który opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych do opisania sekwencji typu **CharType** używanego do reprezentowania pola wejściowego lub pieniężnego pola danych wyjściowych.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł moneypunct dla danego ustawienia regionalnego, co umożliwia formatowanie pól danych wejściowych lub wyjściowych.|
|[num_get](../standard-library/num-get-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości liczbowe.|
|[num_put](../standard-library/num-put-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości numerycznych na sekwencje typu **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Szablon klasy, który opisuje obiekt, który może służyć jako zestaw reguł lokalnych do opisywania sekwencji typu **CharType** używanego do reprezentowania informacji o formatowaniu i interpunkcji wyrażeń liczbowych i logicznych.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł moneypunct dla danego ustawienia regionalnego, co umożliwia formatowanie i interpunkcję wyrażeń liczbowych i logicznych.|
|[time_base](../standard-library/time-base-class.md)|Klasa, która służy jako klasa bazowa dla aspektów szablonu klasy time_get, definiująca tylko typ wyliczeniowy dateorder i kilka stałych tego typu.|
|[time_get](../standard-library/time-get-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości czasu.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł ustawień regionalnych typu time_get \<**CharType**, **InputIterator**> .|
|[time_put](../standard-library/time-put-class.md)|Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości czasu na sekwencje typu **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł ustawień regionalnych typu `time_put` \<**CharType**, **OutputIterator**> .|
|[Klasa wbuffer_convert](../standard-library/wbuffer-convert-class.md)|Opisuje bufor strumienia, który kontroluje przekazywanie elementów do i z bufora strumienia bajtów.|
|[Klasa wstring_convert](../standard-library/wstring-convert-class.md)|Szablon klasy, który wykonuje konwersje między ciągiem szerokim i ciągiem bajtowym.|

## <a name="see-also"></a>Zobacz także

[Strony kodowe](../c-runtime-library/code-pages.md)\
[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
