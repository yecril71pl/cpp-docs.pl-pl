---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 8d109ec452df33b774848229837ed3e2eae80dc4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181021"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Typy **char**, **wchar_t**, **char16_t** i **char32_t** są typami wbudowanymi, które reprezentują znaki alfanumeryczne, a także symbole inne niż alfanumeryczne i znaki niedrukowalne.

## <a name="syntax"></a>Składnia

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Uwagi

Typ **char** to oryginalny typ znaku w C i C++. Typ **bez znaku** jest często używany do reprezentowania *bajtu*, który nie jest typem wbudowanym w C++. Typ **char** może służyć do przechowywania znaków z zestawu znaków ASCII lub dowolnych zestawów znaków ISO-8859, a także poszczególnych bajtów znaków wielobajtowych, takich jak Shift-JIS lub kodowanie UTF-8 zestawu znaków Unicode. Ciągi typu **char** są określane jako *wąskie* ciągi, nawet jeśli są używane do kodowania znaków wielobajtowych. W kompilatorze firmy Microsoft **znak** jest typu 8-bitowego.

Typ **wchar_t** jest typem szerokim zdefiniowanym dla implementacji. W kompilatorze firmy Microsoft reprezentuje 16-bitowy znak dwubajtowy używany do przechowywania kodowania Unicode zakodowanego jako UTF-16LE, natywny typ znaków w systemach operacyjnych Windows. Wersje szerokiego znaku funkcji biblioteki uniwersalnego środowiska uruchomieniowego języka C (UCRT) używają **wchar_t** , a jej wskaźników i typów tablic jako parametrów i zwracanych wartości, tak jak w przypadku wersji znaków dwubajtowych NATYWNEGO interfejsu API systemu Windows.

Typy **char16_t** i **char32_t** reprezentują odpowiednio 16-bitowe i 32-bitowe znaki. Kodowanie Unicode zakodowane jako UTF-16 może być przechowywane w typie **char16_t** , a kodowanie Unicode zakodowane jako utf-32 może być przechowywane w typie **char32_t** . Ciągi tych typów i **wchar_t** są określane jako ciągi *szerokie* , chociaż termin często odwołuje się głównie do ciągów typu **wchar_t** .

W bibliotece C++ standardowej typ `basic_string` jest wyspecjalizowany dla ciągów wąskich i szerokich. Użyj `std::string`, gdy znaki są typu **char**, `std::u16string`, gdy znaki są typu **char16_t**, `std::u32string`, gdy znaki są typu **char32_t**, i `std::wstring`, gdy znaki są typu **wchar_t**. Inne typy, które reprezentują tekst, w tym `std::stringstream` i `std::cout`, mają specjalizacje dla ciągów wąskich i szerokich.
