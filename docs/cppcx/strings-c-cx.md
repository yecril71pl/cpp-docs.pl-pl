---
title: "Ciągi (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e70f5fc5478d0950a7287da690822046621e517b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strings-ccx"></a>Ciągi (C + +/ CX)
Tekst w środowisku wykonawczym systemu Windows jest reprezentowana w języku C + +/ CX przez [Platform::String klasy](../cppcx/platform-string-class.md). Użyj `Platform::String Class` Jeśli ciągi i z powrotem do metod w klasach środowiska wykonawczego systemu Windows lub gdy użytkownik korzysta z innymi składnikami środowiska wykonawczego systemu Windows granicy binarny interfejsu (ABI) aplikacji. `Platform::String Class` Udostępnia metody dla kilku typowe operacje na ciągach, ale nie są zaprojektowane jako klasa kompletne ciągu. W module języka C++ Użyj standardowych typów ciąg C++ takiego jak [wstring](../standard-library/basic-string-class.md) przetwarzania znaczący tekst i następnie Konwertuj ostatecznych spowodować [Platform::String ^](../cppcx/platform-string-class.md) przed przekazać do lub z publiczną interfejs. Jest łatwe i skuteczne konwersję między `wstring` lub `wchar_t*` i `Platform::String`.  
  
 **Szybko przekazywany**  
  
 W niektórych przypadkach kompilator można sprawdzić, można bezpiecznie konstruować `Platform::String` lub Przekaż `String` funkcji bez kopiowania danych ciągu. Takie operacje są określane jako *szybko przekazywany* i występują w sposób niewidoczny dla użytkownika.  
  
## <a name="string-construction"></a>Ciąg konstrukcji  
 Wartość `String` obiekt jest niezmienialny sekwencji (tylko do odczytu) z `char16` (16-bitowych Unicode) znaków. Ponieważ `String` obiektu nie można modyfikować, przypisanie nowych literału ciągu na `String` zmiennej faktycznie zastępuje oryginalną `String` obiektu o nowej `String` obiektu. Operacje łączenia obejmują zniszczenie oryginalnej `String` obiekt i utworzenia nowego obiektu.  
  
 **Literały**  
  
 A *znak* jest znak jest ujęty w pojedynczym cudzysłowie, a *literałem* jest sekwencja znaków jest ujęta w znaki podwójnego cudzysłowu. Jeśli używasz literału ciągu inicjowania ^ zmiennej, kompilator przyjęto założenie, że literał składa się z `char16` znaków. Oznacza to, nie należy poprzedzać literał ciągu modyfikatorem "L" lub ujmij literał w **_T()** lub **TEXT()** makra. Aby uzyskać więcej informacji na temat języka C++, obsługa formatu Unicode, zobacz [podsumowanie programowania Unicode](../text/unicode-programming-summary.md).  
  
 W poniższym przykładzie przedstawiono różne sposoby tworzenia `String` obiektów.  
  
 [!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]  
  
## <a name="string-handling-operations"></a>Obsługi operacji ciągów  
 `String` Klasa udostępnia metody i operatory do łączenia, porównywanie ciągów i innych podstawowe operacje na ciągach. Aby przeprowadzić bardziej rozległych na ciągach, użyj `String::Data()` funkcji członkowskiej można pobrać wartości `String^` obiekt jako `const wchar_t*`. Następnie użyj tej wartości można zainicjować `std::wstring`, zapewniające ciąg rozbudowane funkcje obsługi.  
  
 [!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]  
  
## <a name="string-conversions"></a>Konwersja ciągu  
 A `Platform::String` może zawierać tylko `char16` znaków, lub `NULL` znaków. Jeśli aplikacja jest praca z 8-bitową znaków, użyj [String::Data](../cppcx/platform-string-class.md#data) można wyodrębnić tekst jako `const wchar_t*`. Następnie można użyć odpowiednie funkcje systemu Windows lub funkcje biblioteki standardowej do obsługi danych i przekonwertować go z powrotem do `wchar_t*` lub [wstring](../standard-library/basic-string-class.md), którego można użyć do utworzenia nowego `Platform::String`.  
  
 Poniższy fragment kodu pokazuje sposób konwertowania `String^` zmiennej do i z `wstring` zmiennej. Aby uzyskać więcej informacji na temat manipulowanie ciągami, który jest używany w tym przykładzie, zobacz [basic_string::replace](../standard-library/basic-string-class.md#replace).  
  
 [!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]  
  
## <a name="string-length-and-embedded-null-values"></a>Długość ciągu i osadzone wartości NULL  
 [String::Length](../cppcx/platform-string-class.md#length) zwraca liczbę znaków w ciągu nie liczba bajtów. Znak końcowy NULL jest pomijany, chyba że zostaną jawnie określone jej używania semantyka stosu do skonstruowania ciągu.  
  
 A `Platform::String` może zawierać osadzone wartości NULL, ale tylko wtedy, gdy wartość NULL jest wyniku operacji łączenia. Osadzone wartości nie są obsługiwane w literałach ciągu; w związku z tym nie można użyć osadzonego wartości null w ten sposób można zainicjować `Platform::String`. Osadzone wartości NULL w `Platform::String` są ignorowane, jeśli ciąg jest wyświetlany, na przykład, gdy jest przypisany do `TextBlock::Text` właściwości. Osadzone wartości są usuwane, gdy wartość ciągu jest zwracany przez `Data` właściwości.  
  
## <a name="stringreference"></a>StringReference  
 W niektórych przypadkach kodu () otrzymuje std::wstring, lub ciąg wchar_t lub L"" ciąg literału i po prostu przekazuje je do innej metody pobierającej ciąg ^ jako parametr wejściowy. Tak długo, jak oryginalny buforu ciągu, sam pozostaje ważny i nie zmodyfikować przed funkcji, można przekonwertować `wchar_t*` ciągu lub literału ciągu na [Platform::StringReference](../cppcx/platform-stringreference-class.md)i podaj który zamiast `Platform::String^`. Jest to dozwolone, ponieważ `StringReference` ma zdefiniowane przez użytkownika konwersja na `Platform::String^`. Za pomocą `StringReference` można uniknąć dodatkowych kopii danych ciągu. W pętli, gdzie są przekazywanie dużą liczbą parametrów lub podczas przekazywania ciągów bardzo duży, poprawa wydajności znaczących może potencjalnie osiągnąć za pomocą `StringReference`. Jednak ponieważ `StringReference` zasadniczo pożycza oryginalnego buforu ciągu, należy użyć szczególną uwagę na to, aby uniknąć uszkodzenia pamięci. Nie należy przekazać `StringReference` do metody asynchronicznej, chyba że oryginalnego ciągu gwarantuje to w zakresie po powrocie z tej metody. Ciąg ^ inicjowany ze StringReference wymusi alokacji i kopiowania danych ciągu w przypadku druga operacja przypisania. W takim przypadku zostaną utracone korzyści wydajności `StringReference`.  
  
 Należy pamiętać, że `StringReference` jest standardowego typu klasy C++, nie klasy referencyjnej, nie możesz go użyć w interfejsie publicznej klasy ref, zdefiniowane przez użytkownika.  
  
 Poniższy przykład przedstawia użycie StringReference:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Typy wbudowane](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)