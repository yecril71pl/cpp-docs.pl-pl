---
title: Ciągi (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: a67b9a4552dc83791c05029cca76f60fd83df0f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745344"
---
# <a name="strings-ccx"></a>Ciągi (C++/CX)

Tekst w środowisku wykonawczego systemu Windows jest reprezentowany w języku C++/CX przez [platformę::String Class](../cppcx/platform-string-class.md). `Platform::String Class` Podczas przekazywania ciągów tam iz powrotem do metod w klasach środowiska wykonawczego systemu Windows lub podczas interakcji z innymi składnikami środowiska wykonawczego systemu Windows w granicach interfejsu binarnego aplikacji (ABI). Zapewnia `Platform::String Class` metody dla kilku typowych operacji ciągu, ale nie jest przeznaczony do w pełni funkcjonalny ciąg klasy. W module C++ należy użyć standardowych typów ciągów języka C++, takich jak [wstring](../standard-library/basic-string-class.md) dla dowolnego znaczącego przetwarzania tekstu, a następnie przekonwertować wynik końcowy na [Platform::String^](../cppcx/platform-string-class.md) przed przekazaniem go do lub z interfejsu publicznego. Konwersja między `wstring` lub i `wchar_t*` . `Platform::String`

**Szybkie przejście**

W niektórych przypadkach kompilator może sprawdzić, `Platform::String` czy `String` można bezpiecznie skonstruować lub przekazać do funkcji bez kopiowania podstawowych danych ciągu. Takie operacje są znane jako *szybkie przejście* i występują w sposób przezroczysty.

## <a name="string-construction"></a>Konstrukcja strun

Wartość `String` obiektu jest niezmienną (tylko do odczytu) `char16` sekwencją (16-bitowych znaków Unicode). Ponieważ `String` obiekt jest niezmienny, przypisanie nowego literału ciągu do `String` `String` zmiennej faktycznie `String` zastępuje oryginalny obiekt nowym obiektem. Operacje łączenia obejmują zniszczenie oryginalnego `String` obiektu i utworzenie nowego obiektu.

**Literały**

*Znak dosłowny* jest znakiem, który jest ujęty w pojedynczy cudzysłów, a *ciąg literał* jest sekwencją znaków, która jest ujęta w podwójne cudzysłowy. Jeśli używasz literału do zainicjowania string^ zmiennej, kompilator `char16` zakłada, że literał składa się ze znaków. Oznacza to, że nie trzeba poprzedzać literału modyfikatorem ciągu "L" ani ująć literału w makra **_T()** lub **TEXT().** Aby uzyskać więcej informacji na temat obsługi języka C++ dla unicode, zobacz [Podsumowanie programowania Unicode](../text/unicode-programming-summary.md).

W poniższym przykładzie `String` przedstawiono różne sposoby konstruowania obiektów.

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Operacje obsługi ciągów

Klasa `String` zawiera metody i operatory do łączenia, porównywania ciągów i innych podstawowych operacji ciągu. Aby wykonać bardziej obszerne manipulacje ciągami, użyj funkcji `String::Data()` elementu członkowskiego, aby pobrać wartość `String^` obiektu jako . `const wchar_t*` Następnie użyj tej wartości, `std::wstring`aby zainicjować , który zapewnia zaawansowane funkcje obsługi ciągów.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Konwersje ciągów

A `Platform::String` może `char16` zawierać tylko `NULL` znaki lub znak. Jeśli aplikacja musi pracować ze znakami 8-bitowym, `const wchar_t*`użyj [string::Data,](../cppcx/platform-string-class.md#data) aby wyodrębnić tekst jako plik . Następnie można użyć odpowiednich funkcji systemu Windows lub funkcji biblioteki standardowej `wchar_t*` do działania na danych i przekonwertować je z powrotem na lub [wstring](../standard-library/basic-string-class.md), który można użyć do skonstruowania nowego `Platform::String`.

Poniższy fragment kodu pokazuje, `String^` jak przekonwertować zmienną do i ze zmiennej. `wstring` Aby uzyskać więcej informacji na temat manipulacji ciągami używanymi w tym przykładzie, zobacz [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Długość ciągu i osadzone wartości NULL

[Ciąg::Długość](../cppcx/platform-string-class.md#length) zwraca liczbę znaków w ciągu, a nie liczbę bajtów. Kończący się znak NULL nie jest liczony, chyba że jawnie określisz go podczas używania semantyki stosu do konstruowania ciągu.

A `Platform::String` może zawierać osadzone wartości NULL, ale tylko wtedy, gdy null jest wynikiem operacji łączenia. Osadzone Nulls nie są obsługiwane w literałach ciągów; w związku z tym nie można użyć osadzonych NULLs w ten sposób, aby zainicjować `Platform::String`. Osadzone wartości NULL `Platform::String` w a są ignorowane, gdy ciąg jest wyświetlany, `TextBlock::Text` na przykład, gdy jest przypisany do właściwości. Osadzone NulLs są usuwane, gdy `Data` wartość ciągu jest zwracana przez właściwość.

## <a name="stringreference"></a>Odwzłówka ciągu

W niektórych przypadkach kod (a) odbiera std::wstring lub wchar_t string lub literał ciągu L"" i po prostu przekazuje go do innej metody, która przyjmuje String^ jako parametr wejściowy. Tak długo, jak oryginalny bufor ciągu sam pozostaje prawidłowy i nie mutuje przed zwraca funkcję, można przekonwertować `wchar_t*` ciąg lub ciąg literał do [Platform::StringReference](../cppcx/platform-stringreference-class.md), i przekazać w tym zamiast . `Platform::String^` Jest to dozwolone, ponieważ `StringReference` ma zdefiniowaną przez użytkownika konwersję do `Platform::String^`. Za `StringReference` pomocą można uniknąć tworzenia dodatkowej kopii danych ciągu. W pętlach, w których przekazujesz dużą liczbę ciągów lub podczas przekazywania bardzo dużych ciągów, można potencjalnie osiągnąć znaczną poprawę wydajności za pomocą `StringReference`programu . Ale `StringReference` ponieważ zasadniczo pożycza oryginalny bufor ciągów, należy użyć ekstremalnej staranności, aby uniknąć uszkodzenia pamięci. Nie należy przekazywać `StringReference` do metody asynchroniczne, chyba że oryginalny ciąg jest gwarantowane w zakresie, gdy ta metoda zwraca. A String^ który jest inicjowany z StringReference wymusi alokacji i kopii danych ciągu, jeśli wystąpi druga operacja przypisania. W takim przypadku stracisz korzyści `StringReference`z wydajności .

Należy `StringReference` zauważyć, że jest to standardowy typ klasy C++, a nie klasa ref, nie można jej używać w interfejsie publicznym klasy ref, które definiujesz.

W poniższym przykładzie pokazano, jak używać StringReference:

```cpp
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
