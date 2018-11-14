---
title: '&lt;Ustawienia regionalne&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 16248a93b557a92d89e35aac8eba912a8294af76
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524264"
---
# <a name="ltlocalegt"></a>&lt;Ustawienia regionalne&gt;

Definiuje klasy szablonów i funkcje, których programy C++ mogą używać do hermetyzacji i manipulowania różnymi konwencjami kulturalnymi dotyczącymi reprezentacji i formatowania danych liczbowych, pieniężnych i kalendarzowych, w tym obsługi funkcji wielojęzycznych klasyfikacji znaków i sortowania ciągów.

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
|[isdigit](../standard-library/locale-functions.md#isdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem liczbowym.|
|[isgraph](../standard-library/locale-functions.md#isgraph)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.|
|[islower](../standard-library/locale-functions.md#islower)|Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.|
|[isprint](../standard-library/locale-functions.md#isprint)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.|
|[isspace](../standard-library/locale-functions.md#isspace)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.|
|[isupper](../standard-library/locale-functions.md#isupper)|Sprawdza, czy element w ustawieniach regionalnych jest pisany wielkimi literami.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.|
|[tolower](../standard-library/locale-functions.md#tolower)|Konwertuje znak do małej litery.|
|[toupper](../standard-library/locale-functions.md#toupper)|Konwertuje znak do wielkiej litery.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Klasa szablonu, która zawiera zestaw reguł używanych do konwersji między wewnętrznym i zewnętrznym kodowaniem znaków.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Klasa bazowa dla klasy codecvt, która służy do definiowania typu wyliczenia, określane jako `result`, który jest używany jako typ zwracany dla funkcji składowych zestawu reguł, aby wskazać wynik konwersji.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwersji.|
|[COLLATE](../standard-library/collate-class.md)|Klasy szablonu sortowania, która zawiera zestaw reguł obsługujących konwencje sortowania ciągów.|
|[collate_byname](../standard-library/collate-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.|
|[ctype](../standard-library/ctype-class.md)|Klasa szablonu zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.|
|[CType\<char >](../standard-library/ctype-char-class.md)|Klasa, która jest jawną specjalizacją klasy szablonu `ctype<CharType>` na typ **char**, opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu scharakteryzowania różnych właściwości znaku typu **char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Klasa pochodna szablonu, opisująca obiekt, który może służyć jako zestaw reguł ctype danych ustawień regionalnych, umożliwiając klasyfikację znaków i konwersję znaków między wielkimi i małymi literami oraz zestawami znaków macierzystymi i określonymi przez ustawienia regionalne.|
|[Ustawienia regionalne](../standard-library/locale-class.md)|Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.|
|[Komunikaty](../standard-library/messages-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu pobrania zlokalizowanych komunikatów z katalogu międzynarodowych wiadomości dla danego ustawienia regionalnego.|
|[messages_base](../standard-library/messages-base-class.md)|Klasa bazowa, która opisuje **int** typu dla katalogu komunikatów.|
|[messages_byname](../standard-library/messages-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł komunikatów danych ustawień regionalnych, umożliwiając pobieranie zlokalizowanych komunikatów.|
|[money_base](../standard-library/money-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[money_get](../standard-library/money-get-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości pieniężne.|
|[money_put](../standard-library/money-put-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości pieniężnych na sekwencje typu **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych do opisania sekwencji typu **CharType** używana do reprezentowania pola pieniężnych danych wejściowych lub pola pieniężnych danych wyjściowych.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie pól pieniężnych danych wejściowych i wyjściowych.|
|[num_get](../standard-library/num-get-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości liczbowe.|
|[num_put](../standard-library/num-put-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości liczbowych na sekwencje typu **CharType**.|
|[numpunct —](../standard-library/numpunct-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako lokalny zestaw reguł do opisania sekwencji typu **CharType** używanych do przedstawiania informacji o formatowaniu i znakach interpunkcyjnych wyrażeń liczbowych i logicznych.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie i interpunkcję wyrażeń liczbowych i logicznych.|
|[time_base](../standard-library/time-base-class.md)|Klasa, która służy jako klasa bazowa dla zestawów reguł klasy szablonu time_get, definiująca tylko typ wyliczenia dateorder oraz kilka stałych tego typu.|
|[time_get](../standard-library/time-get-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu **CharType** na wartości czasu.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu time_get\<**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości czasu na sekwencje typu **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu `time_put` \< **CharType**, **OutputIterator**>.|
|[wbuffer_convert, klasa](../standard-library/wbuffer-convert-class.md)|W tym artykule opisano buforu strumieni, który kontroluje przekazywanie elementów do i z buforu strumienia bajtów.|
|[wstring_convert, klasa](../standard-library/wstring-convert-class.md)|Klasa szablonu, który wykonuje konwersje między ciąg znaków dwubajtowych i ciąg bajtów.|

## <a name="see-also"></a>Zobacz także

[Strony kodowe](../c-runtime-library/code-pages.md)<br/>
[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
