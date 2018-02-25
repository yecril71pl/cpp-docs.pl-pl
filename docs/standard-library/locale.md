---
title: '&lt;Ustawienia regionalne&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
dev_langs:
- C++
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ac044246cf9dea3d5760d60453182b2ec5711d0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltlocalegt"></a>&lt;Ustawienia regionalne&gt;
Definiuje klasy szablonów i funkcje, których programy C++ mogą używać do hermetyzacji i manipulowania różnymi konwencjami kulturalnymi dotyczącymi reprezentacji i formatowania danych liczbowych, pieniężnych i kalendarzowych, w tym obsługi funkcji wielojęzycznych klasyfikacji znaków i sortowania ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <locale>  
  
```  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[has_facet](../standard-library/locale-functions.md#has_facet)|Sprawdza, czy określony zestaw reguł jest przechowywany w określonych ustawieniach regionalnych.|  
|[isalnum](../standard-library/locale-functions.md#isalnum)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym czy liczbowym.|  
|[isalpha](../standard-library/locale-functions.md#isalpha)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym.|  
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem kontrolnym.|  
|[isdigit](../standard-library/locale-functions.md#isdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem liczbowym.|  
|[isgraph —](../standard-library/locale-functions.md#isgraph)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.|  
|[islower](../standard-library/locale-functions.md#islower)|Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.|  
|[isprint —](../standard-library/locale-functions.md#isprint)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.|  
|[ispunct —](../standard-library/locale-functions.md#ispunct)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.|  
|[isspace](../standard-library/locale-functions.md#isspace)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.|  
|[isupper —](../standard-library/locale-functions.md#isupper)|Sprawdza, czy element w ustawieniach regionalnych jest pisany wielkimi literami.|  
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.|  
|[tolower](../standard-library/locale-functions.md#tolower)|Konwertuje znak do małej litery.|  
|[toupper](../standard-library/locale-functions.md#toupper)|Konwertuje znak do wielkiej litery.|  
|[use_facet](../standard-library/locale-functions.md#use_facet)|Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[codecvt](../standard-library/codecvt-class.md)|Klasa szablonu, która zawiera zestaw reguł używanych do konwersji między wewnętrznym i zewnętrznym kodowaniem znaków.|  
|[codecvt_base](../standard-library/codecvt-base-class.md)|Klasa podstawowa dla codecvt — klasa, która służy do definiowania typu wyliczeniowego, określany jako **wynik**, używana jako typ zwracany dla funkcji Członkowskich aspektu wyniku konwersji.|  
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwersji.|  
|[Sortowanie](../standard-library/collate-class.md)|Klasy szablonu sortowania, która zawiera zestaw reguł obsługujących konwencje sortowania ciągów.|  
|[collate_byname](../standard-library/collate-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.|  
|[ctype](../standard-library/ctype-class.md)|Klasa szablonu zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.|  
|[CType —\<char >](../standard-library/ctype-char-class.md)|Klasa, która jest jawnej specjalizacji szablonu klasy **ctype\<CharType**> na typ `char`, opisujący obiekt, który może służyć jako zestaw reguł ustawień regionalnych charakteryzujących różne właściwości znaku typu `char`.|  
|[ctype_base](../standard-library/ctype-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|  
|[ctype_byname](../standard-library/ctype-byname-class.md)|Klasa pochodna szablonu, opisująca obiekt, który może służyć jako zestaw reguł ctype danych ustawień regionalnych, umożliwiając klasyfikację znaków i konwersję znaków między wielkimi i małymi literami oraz zestawami znaków macierzystymi i określonymi przez ustawienia regionalne.|  
|[Ustawienia regionalne](../standard-library/locale-class.md)|Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.|  
|[Komunikaty](../standard-library/messages-class.md)|Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu pobrania zlokalizowanych komunikatów z katalogu międzynarodowych wiadomości dla danego ustawienia regionalnego.|  
|[messages_base](../standard-library/messages-base-class.md)|Klasa podstawowa, która opisuje `int` typ katalogu wiadomości.|  
|[messages_byname](../standard-library/messages-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł komunikatów danych ustawień regionalnych, umożliwiając pobieranie zlokalizowanych komunikatów.|  
|[money_base](../standard-library/money-base-class.md)|Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.|  
|[money_get](../standard-library/money-get-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu **CharType** do wartości monetarnych.|  
|[money_put](../standard-library/money-put-class.md)|Klasy szablonu, który opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersji wartości walutowej sekwencji typu **CharType**.|  
|[moneypunct](../standard-library/moneypunct-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do opisywania sekwencji typu **CharType** używany do reprezentowania pieniężnego pole wejściowe lub pole pieniężne danych wyjściowych.|  
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie pól pieniężnych danych wejściowych i wyjściowych.|  
|[num_get](../standard-library/num-get-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu **CharType** do wartości liczbowych.|  
|[num_put](../standard-library/num-put-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersji wartości liczbowych sekwencji typu **CharType**.|  
|[numpunct —](../standard-library/numpunct-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako lokalnego aspektu do opisywania sekwencji typu **CharType** używany do reprezentowania informacje dotyczące formatowania i znaków interpunkcyjnych wyrażeń liczbowych i logicznych.|  
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł moneypunct danych ustawień regionalnych, umożliwiając formatowanie i interpunkcję wyrażeń liczbowych i logicznych.|  
|[time_base](../standard-library/time-base-class.md)|Klasa, która służy jako klasa bazowa dla zestawów reguł klasy szablonu time_get, definiująca tylko typ wyliczenia dateorder oraz kilka stałych tego typu.|  
|[time_get](../standard-library/time-get-class.md)|Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu **CharType** do wartości typu time.|  
|[time_get_byname](../standard-library/time-get-byname-class.md)|Klasy pochodne szablonu, która opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych z time_get — typ\<**CharType**, **InputIterator**>.|  
|[time_put](../standard-library/time-put-class.md)|Klasy szablonu, który opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersji wartości czasu sekwencji typu **CharType**.|  
|[time_put_byname](../standard-library/time-put-byname-class.md)|Klasy pochodne szablonów opisujący obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu `time_put` \< **CharType**, **OutputIterator**>.|  
|[wbuffer_convert, klasa](../standard-library/wbuffer-convert-class.md)|W tym artykule opisano buforu strumienia, który kontroluje przesyłania elementów do i z buforu strumienia bajtów.|  
|[wstring_convert, klasa](../standard-library/wstring-convert-class.md)|Klasy szablonu, który wykonuje konwersje między ciąg typu wide i ciąg bajtów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Strony kodowe](../c-runtime-library/code-pages.md)   
 [Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



