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
ms.openlocfilehash: 708184a6a6a443456f0d70f57b6be17b281ac4f5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453921"
---
# <a name="ltlocalegt"></a>&lt;ustawienie&gt;

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
|[isgraf](../standard-library/locale-functions.md#isgraph)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.|
|[islower](../standard-library/locale-functions.md#islower)|Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.|
|[isprint](../standard-library/locale-functions.md#isprint)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.|
|[isspace](../standard-library/locale-functions.md#isspace)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.|
|[IsUpper](../standard-library/locale-functions.md#isupper)|Sprawdza, czy element w ustawieniach regionalnych jest pisany wielkimi literami.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Konwertuje znak do małej litery.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Konwertuje znak do wielkiej litery.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Klasa szablonu, która zawiera zestaw reguł używanych do konwersji między wewnętrznym i zewnętrznym kodowaniem znaków.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Klasa bazowa dla klasy codecvt, która jest używana do definiowania typu wyliczenia `result`, który jest określany jako, używany jako zwracany typ dla funkcji składowych aspektu, aby wskazać wynik konwersji.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwersji.|
|[sortowan](../standard-library/collate-class.md)|Klasy szablonu sortowania, która zawiera zestaw reguł obsługujących konwencje sortowania ciągów.|
|[collate_byname](../standard-library/collate-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.|
|[ctype](../standard-library/ctype-class.md)|Klasa szablonu zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.|
|[ctype\<char >](../standard-library/ctype-char-class.md)|Klasa, która jest jawną specjalizacją klasy `ctype<CharType>` szablonu do typu **char**, opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu scharakteryzowania różnych właściwości znaku typu **char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Klasa pochodna szablonu, opisująca obiekt, który może służyć jako zestaw reguł ctype danych ustawień regionalnych, umożliwiając klasyfikację znaków i konwersję znaków między wielkimi i małymi literami oraz zestawami znaków macierzystymi i określonymi przez ustawienia regionalne.|
|[ustawienie](../standard-library/locale-class.md)|Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.|
|[komunikaty](../standard-library/messages-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu pobrania zlokalizowanych komunikatów z katalogu międzynarodowych wiadomości dla danego ustawienia regionalnego.|
|[messages_base](../standard-library/messages-base-class.md)|Klasa bazowa opisująca typ **int** dla wykazu komunikatów.|
|[messages_byname](../standard-library/messages-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł komunikatów danych ustawień regionalnych, umożliwiając pobieranie zlokalizowanych komunikatów.|
|[money_base](../standard-library/money-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|
|[money_get](../standard-library/money-get-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu CharType  na wartości pieniężne.|
|[money_put](../standard-library/money-put-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości pieniężnych na sekwencje typu **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych do opisania sekwencji typu CharType  używanego do reprezentowania pola wejściowego lub pieniężnego.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie pól pieniężnych danych wejściowych i wyjściowych.|
|[num_get](../standard-library/num-get-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu CharType  na wartości liczbowe.|
|[num_put](../standard-library/num-put-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości numerycznych na sekwencje typu **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł lokalnych do opisywania sekwencji typu CharType  używanego do reprezentowania informacji o formatowaniu i interpunkcji wyrażeń liczbowych i logicznych.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie i interpunkcję wyrażeń liczbowych i logicznych.|
|[time_base](../standard-library/time-base-class.md)|Klasa, która służy jako klasa bazowa dla zestawów reguł klasy szablonu time_get, definiująca tylko typ wyliczenia dateorder oraz kilka stałych tego typu.|
|[time_get](../standard-library/time-get-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji sekwencji typu CharType  na wartości czasu.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może być używany jako zestaw reguł ustawień regionalnych typu\<time_get**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości czasu na sekwencje typu **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może być używany jako zestaw reguł ustawień regionalnych `time_put` \<typu **CharType**, **OutputIterator**>.|
|[wbuffer_convert, klasa](../standard-library/wbuffer-convert-class.md)|Opisuje bufor strumienia, który kontroluje przekazywanie elementów do i z bufora strumienia bajtów.|
|[wstring_convert, klasa](../standard-library/wstring-convert-class.md)|Klasa szablonu, która wykonuje konwersje między ciągiem szerokim i ciągiem bajtowym.|

## <a name="see-also"></a>Zobacz także

[Strony kodowe](../c-runtime-library/code-pages.md)\
[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
