---
title: char, wchar_t, char16_t, char32_t | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9855dc406c56f82eb3ed87248316103397e44007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112658"
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t

Typy **char**, **wchar_t**, **char16_t** i **char32_t** są wbudowanych typów, które reprezentują znaki alfanumeryczne oraz Symbole inne niż alfanumeryczne i znaki niedrukowalne.

## <a name="syntax"></a>Składnia

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Uwagi

**Char** typ to oryginalny typ znaku, w językach C i C++. Typ **unsigned char** jest często używana do reprezentowania *bajtów*, która nie jest typem wbudowanym w języku C++. **Char** typu mogą być używane do przechowywania znaków z zestawu znaków ASCII lub żadnego z zestawów znaków ISO-8859 i pojedynczych bajtów znaków wielobajtowych, takiego jak Shift-JIS lub kodowania UTF-8 zestawu znaków Unicode. Ciągi **char** typu są określane jako *zawęzić* ciągów, nawet wtedy, gdy jest używany do kodowania znaków wielobajtowych. W kompilatorze Microsoft **char** jest typem 8-bitowych.

**Wchar_t** typ jest typem znaków dwubajtowych zdefiniowanych w implementacji. W kompilatorze Microsoft znakiem dwubajtowym 16-bitowych, używany do przechowywania Unicode zakodowanymi w formacie UTF-16LE, reprezentuje typ znaków natywnych w systemach operacyjnych Windows. Znak dwubajtowy wersje korzystanie z funkcji biblioteki Universal C Runtime (UCRT) **wchar_t** i jego wskaźnika i tablicy typów jako parametrów i zwracanych wartości, jak znak dwubajtowy wersje natywnych interfejsów API Windows.

**Char16_t** i **char32_t** typy reprezentują 16-bitowe i 32-bitowych znaków dwubajtowych, odpowiednio. Unicode zakodowanych jak UTF-16, mogą być przechowywane w **char16_t** typu i Unicode zakodowanych jak UTF-32 mogą być przechowywane w **char32_t** typu. Ciągi z tych typów i **wchar_t** są wszystkie są nazywane *szeroki* ciągów, chociaż ten termin często odnosi się to do ciągów **wchar_t** typu.

W bibliotece standardowej C++ `basic_string` typu jest przeznaczone dla szerokości i wąskie ciągów. Użyj `std::string` po znaki są typu **char**, `std::u16string` po znaki są typu **char16_t**, `std::u32string` po znaki są typu **char32_t** , i `std::wstring` po znaki są typu **wchar_t**. Inne typy, które reprezentują tekstu, w tym `std::stringstream` i `std::cout` mają specjalizacje wąskie i dwubajtowe ciągów.