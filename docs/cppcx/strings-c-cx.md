---
title: Ciągi (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 350c6133b9f910a067f760681832b81bac24f4e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556458"
---
# <a name="strings-ccx"></a>Ciągi (C + +/ CX)

Tekst w środowisku uruchomieniowym Windows jest reprezentowana w języku C + +/ CX przez [Platform::String, klasa](../cppcx/platform-string-class.md). Użyj `Platform::String Class` Jeśli ciągi i z powrotem do metody klasy środowiska wykonawczego Windows, lub gdy użytkownik korzysta z innych składników środowiska wykonawczego Windows granicę interfejsem binarnym (ABI) aplikacji. `Platform::String Class` Udostępnia metody dla kilku typowych operacji na ciągach, ale nie mają być klasą ciągów w pełni funkcjonalne. W module języka C++, użyj standardowych typów ciągu C++ takich jak [wstring](../standard-library/basic-string-class.md) przetwarzanie znaczące tekstu i następnie przekonwertować ostatni wynik do [Platform::String ^](../cppcx/platform-string-class.md) następnie przekazać go do lub z publiczną interfejs. Jest łatwy i wydajny, aby wykonać konwersję między `wstring` lub `wchar_t*` i `Platform::String`.

**Szybkie — dostęp próbny**

W niektórych przypadkach kompilator można sprawdzić, można bezpiecznie skonstruować `Platform::String` lub przekazać `String` funkcji bez kopiowania danych ciągu. Operacje takie są określane jako *szybko przekazywany* i występujących w sposób niewidoczny dla użytkownika.

## <a name="string-construction"></a>Konstrukcja ciągu

Wartość `String` obiektu to niezmienne (tylko do odczytu) Sekwencja `char16` (16-bitowych Unicode) znaków. Ponieważ `String` obiekt jest niemodyfikowalny przypisania nowy ciąg literału `String` zmiennej faktycznie zastępuje oryginalny `String` obiektu z nową `String` obiektu. Operacje łączenia obejmują zniszczenie oryginalny `String` obiektu i utworzenia nowego obiektu.

**Literały**

A *dosłownego znaku* jest znakiem, który jest ujęty w znaki pojedynczego cudzysłowu i *ciągiem literału* jest sekwencją znaków, który jest ujęty w znaki podwójnego cudzysłowu. Jeśli używasz literału do zainicjowania ciągu ^ zmiennej, kompilator zakłada, że literału składa się z `char16` znaków. Oznacza to, nie należy poprzedzać literał za pomocą modyfikatora "L" w ciągu, lub ujmij literału w **_T()** lub **TEXT()** makra. Aby uzyskać więcej informacji na temat języka C++ obsługę standardu Unicode, zobacz [podsumowanie programowania Unicode](../text/unicode-programming-summary.md).

Poniższy przykład pokazuje różne sposoby, aby skonstruować `String` obiektów.

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Parametry obsługi operacji

`String` Klasa udostępnia metody i operatorów do łączenia, porównywanie ciągów i inne podstawowe operacje na ciągach. Aby przeprowadzić bardziej rozległe działań na ciągach, użyć `String::Data()` funkcję elementu członkowskiego, aby pobrać wartość `String^` obiektu jako `const wchar_t*`. Następnie użyć tej wartości, aby zainicjować `std::wstring`, który udostępnia ciąg zaawansowane funkcje obsługi.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Ciąg konwersje

A `Platform::String` może zawierać tylko `char16` znaków, lub `NULL` znaków. Jeśli aplikacja ma do pracy z 8-bitowych znaków, użyj [String::Data](../cppcx/platform-string-class.md#data) umożliwia wyodrębnianie tekstu jako `const wchar_t*`. Następnie można użyć odpowiednich funkcji Windows lub funkcje biblioteki standardowej do obsługi danych i przekonwertować go z powrotem do `wchar_t*` lub [wstring](../standard-library/basic-string-class.md), którego można użyć do utworzenia nowego `Platform::String`.

Poniższy fragment kodu przedstawia sposób konwertowania `String^` zmiennej, do i z `wstring` zmiennej. Aby uzyskać więcej informacji na temat manipulowanie ciągami, który jest używany w tym przykładzie, zobacz [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Długość ciągu i osadzone wartości NULL

[String::Length](../cppcx/platform-string-class.md#length) zwraca liczbę znaków w ciągu, nie liczbę bajtów. Nie jest liczony kończącego znaku NULL, chyba że jawnie określisz jego użycia semantyka stosu do skonstruowania ciągu.

Element `Platform::String` może zawierać osadzone wartości NULL, ale tylko wtedy, gdy wartość NULL jest wynikiem operacji łączenia. Osadzone wartości nie są obsługiwane w literałach ciągu; w związku z tym, nie można użyć osadzonego na wartości null w ten sposób można zainicjować `Platform::String`. Osadzone wartości NULL w `Platform::String` są ignorowane, gdy ten ciąg jest wyświetlany, na przykład, gdy jest przypisany do `TextBlock::Text` właściwości. Osadzone wartości są usuwane, gdy wartość ciągu jest zwracany przez `Data` właściwości.

## <a name="stringreference"></a>StringReference

W niektórych przypadkach kod () odbiera std::wstring, lub ciąg wchar_t lub L"" ciąg literału i po prostu przekazuje je do innej metody, która przyjmuje ciąg ^ jako parametr wejściowy. Tak długo, jak oryginalny sam bufor ciągu pozostaje ważny i nie mutuje przed zwraca funkcję, możesz przekonwertować `wchar_t*` ciągu lub literału ciągu [Platform::StringReference](../cppcx/platform-stringreference-class.md)i przekazać, zamiast `Platform::String^`. Jest to dozwolone, ponieważ `StringReference` ma zdefiniowane przez użytkownika konwersji do `Platform::String^`. Za pomocą `StringReference` należy unikać wprowadzania dodatkową kopię danych ciągu. W pętlach, gdy przekazujesz dużą ciągów, w przeciwnym razie podczas przekazywania bardzo dużych ciągów, istotnie poprawiającą wydajność może potencjalnie osiągnąć za pomocą `StringReference`. Ale ponieważ `StringReference` zasadniczo pożycza oryginalnego buforu ciągu, aby uniknąć uszkodzenia pamięci, należy użyć rozwagą. Nie mają być przekazywane `StringReference` metody asynchronicznej Jeśli oryginalny ciąg może być w zakresie, po powrocie z tej metody. Ciąg ^ który jest inicjowany z StringReference wymusi alokacji i kopiowania danych ciągu, jeśli wystąpi drugą operację przypisania. W takim przypadku zostaną utracone korzyści w zakresie wydajności dla `StringReference`.

Należy pamiętać, że `StringReference` jest standardowego typu klasy C++, a nie klasy referencyjnej, nie można używać go w interfejsie publicznym klasy ref, które można zdefiniować.

Poniższy przykład pokazuje, jak używać StringReference:

```
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

